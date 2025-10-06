## Background
To flash firmware to the powerboard's ESP, the code is written from the raspi to the ESP. Previously, this was done with a direct USB connection from the raspi to the powerboard. The USB signal is the converted to a UART signal with a FTDI board which then writes to the ESP. 

The new solution to flash the ESP is a direct line of UART communication from the raspi which is routed to the UI board, then to the powerboard. This eliminates the FTDI cable. Currently, flashing through the header pins is unreliable

To actually flash the ESP, the boot and reset buttons are required, but are in physically unacessable locations. Ideally, we can flash the ESP without having to press the boot or reset buttons.

An additional capability desired is to be able to flash the ESP without requiring the raspi. That would be a direct connection from a laptop to the ESP, which would require the FTDI board.

> Why is it first routed to the UI board?
 To maintain consistency of the design and keep the electrical package consistent

> Why is it preferable to not have a FTDI connection?
 See the above.

> What are the current issues with the UART routing?
Unknown, this is untested. 

> Why do you need the boot and reset buttons to start flashing to the ESP?
 To prepare the ESP to be in a mode such that code can be flashed to the ESP. There is currently existing hardware that can be used to write to the boot and reset pins instead of physical button presses. Physical buttons are still desired for the powerboard for testing purposes.

> How frequently does the ESP have to be re-flashed?
 Dont really care.
 
> Why is flashing through the header pins 'unreliable'?
 Just untested. Suspect noise from connectors and long connection line.
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




