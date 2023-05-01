# Voron0-2040-display
RP2040 port of the Voron0 display


I created this port in order to give another option when it comes to the Voron0 display. Additionally it makes use of the easily available RP2040 IC for ease of modificaion and implementation. The files in this github are everything you should need, if you wanted to make your own or if you have any questions about the details of the device. 

The display includes both a USB-C connector and 4-pin header. This makes installation a little cleaner, allowing you to use standard dupont connectors versus longer USB connectors. 

***Only data connector can be used, do not attempt to plug anything into the USB connector while the pin header is in use.

To contifigure this display, you can use use the following parameters:

[mcu rp2040]
#serial: /dev/serial/by-id/<modify this value to match your system> Details to be found in http://github.com/th0mpy/v0-2040display
restart_method: command

[display]
lcd_type: sh1106
i2c_mcu: rp2040
i2c_bus: i2c0a
vcomh: 31
x_offset: 2
encoder_pins: ^rp2040:gpio7, ^rp2040:gpio6
click_pin: ^!rp2040:gpio8
kill_pin: ^!rp2040:gpio5

[neopixel rp2040]
pin: rp2040:gpio16
chain_count: 1
color_order: GRB
initial_RED: .6
initial_GREEN: 0
initial_BLUE: .75



One method to find the serial port used by the display is to simply call 'ls /dev/serial/by-id' and look for a device which will be called something like usb-Klipper_rp2040_E6625495537C5221-if00 (the device will show up after it is plugged in).

