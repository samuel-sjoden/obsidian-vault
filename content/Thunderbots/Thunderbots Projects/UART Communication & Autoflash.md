## Background
To flash firmware to the powerboard's ESP, the code is written from the raspi to the ESP. Previously, this was done with a direct USB connection from the raspi to the powerboard. The USB signal is the converted to a UART signal with a FTDI board which then writes to the ESP. 

The new solution to flash the ESP is a direct line of UART communication from the raspi which is routed to the UI board, then to the powerboard. This eliminates the FTDI cable. Currently, flashing through the header pins is unreliable

To actually flash the ESP, the boot and reset buttons are required, but are in physically unacessable locations. Ideally, we can flash the ESP without having to press the boot or reset buttons.

An additional capability desired is to be able to flash the ESP without requiring the raspi. That would be a direct connection from a laptop to the ESP, which would require the FTDI board.

#### Some Questions
>Why is it first routed to the UI board?
 To maintain consistency of the design and keep the electrical package consistent

> Why is it preferable to not have a FTDI connection?
 See the above.

> What are the current issues with the UART routing?
Unknown, this is untested. 

> Why do you need the boot and reset buttons to start flashing to the ESP?
 To prepare the ESP to be in a mode such that code can be flashed to the ESP. There is currently existing hardware that can be used to write to the boot and reset pins instead of physical button presses. Physical buttons are still desired for the powerboard for testing purposes.
 
> Why is flashing through the header pins 'unreliable'?
 Just untested. Suspect noise from connectors and long connection line.

### Research
Looking into the datasheet for the specific ESP32-Pico-D4 used on the powerboard I looked into the boot configurations of the chip.

The ESP has two strapping boot pins: GPIO0 and GPIO2

The pins have latches, so will store the value after a reset, so they can be used as normal after the boot process. They are stored untill the chip is powered/shut down.

If GPIO0 and GPIO2 are both held low, the chip is put into download mode, and it will wait for download from UART or SDIO
> I do not know what SDIO download would work with. Could this possibly be another possibility if UART is not reliable?

If the GPIO0 pin is held high, the chip goes into a typcial boot sequence copying the programs from flash to RAM. 

GPIO0 is internally held high with a pull up resistor and GPIO2 held low with a pulldown resistor. So long as GPIO2 is not held high during startup, it's status is not important.

Currently, GPIO0 is connected to the boot button. For an autoflash, the raspi would have to be able to bring the pin low so that it can be put into the download sequence.

>[!Verify This]
>So a typical sequence to load code onto the ESP32 would look like this:
>- Hold the EN pin low to power off the ESP32
>- Hold the GPIO0 pin low to put the ESP into download mode
>- After the chip has been written to over serial, the chip can be rebooted.
>- Hold the EN pin low again to boot of the ESP
>- GPIO0 pin is internally held high, and the ESP begins its boot sequence.

> Does the raspi and the ESP32 share a common ground?

#### Autoflash
Looking into how dev boards are able to autoflash when a user plugs into the board.
Programs like ESP tool are used to autoflash on the dev board. They connect the **DTR and RTS** lines to a circuit that gives acess to hold the GPI0 and EN pin low so they have have a proper boot sequence.
[espressif docs](https://docs.espressif.com/projects/esptool/en/latest/esp32/advanced-topics/boot-mode-selection.html?utm_source=chatgpt.com)

[Dev kit autoflash circuit](https://dl.espressif.com/dl/schematics/esp32_devkitc_v4-sch-20180607a.pdf)
![[Pasted image 20251009133515.png]]
On the dev kits they connect the DTR and RTS lines like this to the boot and EN pins. The DTR and RTS come from the USB signal so we dont have this luxury. This could be a quality of life improvement though to elimintate the need to press the buttons when uploading code directly to the powerboard.

Did my own analysis to see if I could verify the truth table above, found the same values:
![[Pasted image 20251009184753.png]]

#### Questions Round 2
> Why is the GPIO0 pin held high externally? In the dev kit they have a small cap across this too which I assume is for debouncing.

> The external pullup reduces the overall resistance, since the internal pullup is quite large ($47\text{k}\Omega$). This improves response speed. This is very useful for I2C lines.
> ![[Pasted image 20251009134101.png]]

> What are these sheild disconnects for?
> ![[Pasted image 20251009134309.png]]

> Can I get component number of the board we use to convert USB to UART.

> Is it alright to leave a connection to the reset pin floating if another circuit is holding it in a defined state? Thinking about connecting pins from UART  plug to the boot circuit which would allow autoflash and boot when testing. The issue would be is when not in place they would be left exposed.

> What is GPIO12 at boot? If it is held high, it brings refrence high for GPIO0 to 1.8V. The altium does not show anything connected.

> I can see that some pins to the connector are directly shorted to the pins on the ESP. What was the plan with those pins?

I found an open source library that is supposed to flash esps over serial [link](https://github.com/espressif/esp-serial-flasher)

An issue I may have encountered with the current hardware setup is that the PI's RX and TX connections are not connected to the flash TX and flash RX. This means that the PI cannot write to the flash because the ESP's ROM bootloader only looks at the GPIO1 and GPIO3 at boot. The serial connection bus UART1 can only be instantiated at runtime, which requires a an existing program to setup the pins. [Source](https://docs.espressif.com/projects/esptool/en/latest/esp32/advanced-topics/serial-protocol.html)

The code would have to be uploaded to the ESP at runtime. I am not sure if you can then execute this code which would require it to be written to persistent memory, then loaded into ram.
> Can this even be done at runtime?

![[Pasted image 20251010104436.png]]
## Experiments

### Testing Sending and Receiving Serial Signals
**Goal:** Test serial communication between the ESP on the powerboard and a device writing serial data.

An external dev ESP will be configured to write serial communication through the UI header pins to the powerboard ESP. The ESP will be flashed with code that will indicate when it receives a message. 

We can either configure it to print to a serial monitor or send it back to the original ESP and print to its serial monitor.

#####  What we are looking for
To ensure the integrity of the signal it should accurately respond to the transmitting ESP. If it is missing signals or not receiving the data, there is an issue with the communication. We will measure how often it misses if  it does.

We will also scope the UART lines to see of there is any distortion on the signals we will scope the UART lines.

#### Test
Wrote a short script for each the sending and receiving ESP32s. To emulate the behavior during flashing, the ESP on the powerboard was designated the receiver and the external dev board the sender. 

The RX and TX were connected to the header pin that the py would typically connect to the ESP through jumper cables. The testing code for both intialized the UART1 bus for the communication. The dev board sent a string which contained a number which incremented each time. It would then print to the UART0 bus, which we monitored, "Sent: {message number}". The receiving ESP, on the powerboard, would listen on that line and then write to UART0 "Received: {message number}".

The baud rate was set to 115200 bits per second. An uncertainty I have with this test is that the current code may just capture how fast the receiver code is looping not data loss.

We additionally scoped the transmission line for noise with the other ESP connected.

### Improving The Test Strategy
Doing some research I found a much more robust way of stress testing the communication lines. It will follow the same sender-receiver pattern but with some additinonal verification steps so that the testing is independent of loop speed and instead is able to capture data corruption, packet loss, and response rate.

The sent messages will be take the format:
```
SEQ<message number>:<checksum>\n
```

This allows the messages to be tracked and the checksum will be a method to see if there has been any data corruption.

The checksum that I am looking into is cyclic redundancy check because of the simplicity and small size of the bit streams I intend on sending. It will be able to detect bit errors during the transmission.

Found a [repo](https://github.com/d-bahr/CRCpp) that has an implementation of the CRC checksum so all that is left to do is verify. This [website](https://www.sunshine2k.de/articles/coding/crc/understanding_crc.html) provided a good explanation of how it works.
##### State Machines
###### Sender
1. Prepare a message in the form $\text{SEQ}\left< \text{Message Number} \right>:\left< \text{Message Checksum} \right>$. Send this message over UART and log when the message was sent.
2. Wait for up to a timeout period for a response from the receiver
3. If message recieved before timeout
	 - Parse acknowlegement into $\text{ACK}\left< \text{Message Number} \right>:\left< \text{Message Checksum} \right>$
	 - Verify the messages checksum
	 - Record in serial monitor if the acknoledgment was good or bad and record the time it took for the message to be returned. The absolute time is not what is important, it is changes in time that gives information on retries
	If the message was not returned before the timeout, record a no acknowledgement error
4. Increment message number and repeat
###### Receiver
1. Listen for a message of the form $\text{SEQ}\left< \text{Message Number} \right>:\left< \text{Message Checksum} \right>$.
2. If message received, parse into individual bits and validate the checksum
3. If the checksum matches, then record a successful transmission. 
	If it doesn't log the message number, time and the corrupted data. 
	If the message could not be properly parsed, report an unknown message
4. Respond to the sender with an acknowledgment.

###### Post-Testing Data Processing
The metrics we will be interested in running the test will be:
- Corruption rate - $\frac{\text{Corrupted Messages Received}}{\text{Number of Messages Sent}}$
- Histogram of response time
-  Loss Rate- $\frac{\text{Number of Messages Acknowledged}}{\text{Total Messages Sent}}$
- Error Rate - $\frac{\text{Number of Corrupted Responses}}{\text{Number of Acknowledgments}}$


