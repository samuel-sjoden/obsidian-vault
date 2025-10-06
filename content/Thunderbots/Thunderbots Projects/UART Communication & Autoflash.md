## Background
To flash firmware to the powerboard's ESP, the code is written from the raspi to the ESP. Previously, this was done with a direct USB connection from the raspi to the powerboard. The USB signal is the converted to a UART signal with a FTDI board which then writes to the ESP. 

The new solution to flash the ESP is a direct line of UART communication from the raspi which is routed to the UI board, then to the powerboard. This eliminates the FTDI cable. Currently, flashing through the header pins is unreliable

To actually flash the ESP, the boot and reset buttons are required, but are in physically unacessable locations. Ideally, we can flash the ESP without having to press the boot or reset buttons.

An additional capability desired is to be able to flash the ESP without requiring the raspi. That would be a direct connection from a laptop to the ESP, which would require the FTDI board.

### Questions To James
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

So a typical sequence to load code onto the ESP32 would look like this:
- Hold the EN pin low to power off the ESP32
- Hold the GPIO0 pin low to put the ESP into download mode
- After the chip has 
### FOC Analysis
#### Functions
- Must be able to flash the ESP directly through UART communication from the raspi
- Must be able to flash the ESP through a USB connection for testing
- Must be able to flash the ESP with and without pressing physical boot and reset buttons
#### Objectives
- 
#### Constraints

## Experiments

### Testing Sending and Receiving Serial Signals
**Goal:** Test serial communication between the ESP on the powerboard and a device writing serial data.

An external dev ESP will be configured to write serial communication through the UI header pins to the powerboard ESP. The ESP will be flashed with code that will indicate when it receives a message. 

We can either configure it to print to a serial monitor or send it back to the original ESP and print to its serial monitor.

#####  What we are looking for
To ensure the integrity of the signal it should accurately respond to the transmitting ESP. If it is missing signals or not receiving the data, there is an issue with the communication. We will measure how often it misses if  it does.

We will also scope the UART lines to see of there is any distortion on the signals we will scope the UART lines.




