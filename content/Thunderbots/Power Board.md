## Overview
Reverse polarity protection
Current sense and voltage measurement to powerboard
 - goes though shunt resistor - tiny little affect on voltage
 Two buck converter to 12V and 5V3 ( for raspi) 
 
 ESP Stuff
 ESP has boot and reset pins
 Connector for UI board with power, UART and boot and reset signals
Power switch on UI board to turn power board on and off
I2C from ESP for power management (current sense as previously mentioned). Discrete chip handles it. 

Break beam 1/0 signal

kick and chip pwm are isolated into a 15 volt signals

> Look into galvanic isolation -> TI document

How we get signal isolation

Two separate ground planes: High voltage (15V and 240V) and then signal which is everything else (5V3, 24V)

Need to review mutual inductance




