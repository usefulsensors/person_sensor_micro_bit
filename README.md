# Person Sensor Micro Bit
Example of accessing the Person Sensor from MicroPython on a BBC Micro:bit.

The [Person Sensor](https://usfl.ink/ps) from [Useful Sensors](https://usefulsensors.com)
is a small, low-cost hardware module that detects nearby peoples’ faces, and
returns information about how many there are, where they are relative to the
device, and performs facial recognition. It is designed to be used as an input
to a larger system, and this example shows how to read it from a [BBC micro:bit board](https://microbit.org/)
using MicroPython. It can also be used as the starting point for other
MicroPython-based boards, but since the exact syntax used to access the I2C bus
varies across platforms, you'll probably need to modify the lines that mention
`i2c` in the main Python script. For a full developer's guide, see [usfl.ink/ps_dev](https://usfl.ink/ps_dev).

## BoM

To build this project you'll need:

 - [Micro:bit board](https://microbit.org/buy/).
 - [Person Sensor from Useful Sensors](https://usfl.ink/ps).
 - [Qwiic connector cable](https://www.sparkfun.com/products/14427).
 - [SparkFun Qwiic micro:bit breakout](https://www.sparkfun.com/products/16445).

 I suggest the SparkFun breakout because it converts the micro:bit's small I2C
 pins into a standard Qwiic socket, but if you're skilled at soldering you could
 attach the wires directly to the edge pins on the board instead.

## Assembling

Slot the micro:bit into the breakout slot, with the two I2C sockets on the
breakout facing in the same direction as the front of the board (the side with
the buttons and LED display on it). Plug one end of the Qwiic cable into either
of the breakout's I2C sockets, and the other into the socket at the top of the
person sensor. If you power the micro:bit board, you should see the green LED
on the person sensor light up when you point it at yourself.

## Running

Create a new project in the [Python micro:bit editor](https://python.microbit.org/v/3).
Click on the `Open` button, and choose the `main.py` file in this folder. Make
sure you have your micro:bit plugged in and click `Send to micro:bit` to upload
the program to the board. If you click on `Show serial` on the right hand pane
you should see information about any found faces shown as text logs. If no faces
are seen, there should be output like this:

```bash
0 []
```

The first number is how many face have been detected, and the second part shows
information about any faces that were found. Here's an abbreviated example of
the output with a face present:

```
1 [{'box_height': 158, 'box_width': 201, 'id': -1, 'box_confidence': 99, 'box_left': ]
```