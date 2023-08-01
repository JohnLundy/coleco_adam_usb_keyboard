# **USB Coleco Adam Keyboard Adapter**

This adapter enables an unmodified Coleco Adam keyboard to work as a USB keyboard on any modern computer. This is great option for using the keyboard with PC ADAM emulators. The Coleco Adam keyboard was considered one of the best keyboards of its time with its modern layout and build quality.

This is a fork of the original project developed by Nick A. Bild found here [USB Coleco Adam Keyboard](https://github.com/nickbild/coleco_adam_usb_keyboard)


![](https://github.com/JohnLundy/coleco_adam_usb_keyboard/raw/main/media/20230731_202517%20-%20small.jpg)

## How It Works

Unlike a typical keyboard of its time that arranged the keys into a matrix of switches that triggered pins on an interface chip when they were closed, Coleco designed a communications protocol called ADAMnet. The keyboard connects to the computer via an RJ-12 connector with a single data line that communicates over a 62.5 kbit/s half-duplex serial bus. It contains its own Motorola 6801 microcontroller to cache key presses and send them to the main computer when it asks for them by sending a series of commands via the ADAMnet protocol.

This project uses a Teensy 4.x microcontroller development board that communicates with the keyboard via ADAMnet to acquire keystrokes, then they are translated into the appropriate key codes and sent to the host computer as if the Teensy was a USB keyboard (be sure to set serial mode to "Keyboard" in Arduino IDE).  Modifier keys like "SHIFT", "CONTROL", and "ALT (Mapped to ESCAPE/WP)" are supported. Note that the ADAM keyboard doesn't have the ability to just select the "CONTROL" key by itself without having a combination of an alphnumeric key pressed at the same time. _This behavior makes it impossible to do a combination of "CONTROL-ALT-DELETE" like a standard PC keyboard_.

The ADAM keyboard is powered directly by the PC by way of the TEENSY 5V (VIN) line.

**Mapping of the keyboard's special keys are as follows:**
| ADAM MAPPED KEY | PC KEY |
| ------ | ------ |
| ESC | ESC |
| WILD CARD | ALT |
| DEL | DEL |
| HOME | HOME |
| I | F1 |
| II | F2 |
| III | F3 |
| IV | F4 |
| V | F5 |
| VI | F6 |
| <SHIFT> + I | F7 | 
| <SHIFT> + II | F8 |
| <SHIFT> + III | F9 | 
| <SHIFT> + IV | F10 | 
| <SHIFT> + V | F11 | 
| <SHIFT> + VI | F12 | 
| UNDO | PAUSE |
| MOVE/COPY | PAGE UP |
| STORE/GET | PAGE DOWN |
| INSERT | INSERT |
| PRINT | PRINT SCREEN |
| CLEAR | END |

**Wiring:**
| TEENSY PIN | RJ12 PIN | ADAMnet SIGNAL |
| ------ | ------ | ------ |
| PIN-1 | RJ12-1 | DATA |
| PIN-2 | RJ12-2 | RESET|
| GND   |  RJ12-3,4,5 | GND |
| +5 (VIN) | RJ12-6 | POWER |

## Schematic

Coming soon

## Media

![](https://github.com/JohnLundy/coleco_adam_usb_keyboard/raw/main/media/20230731_202645%20-%20small.jpg)

## Bill of Materials

- 1 x  &nbsp; Teensy 4.0 or 4.1 Microcontroller Development Board
- 1 x  &nbsp; RJ-12 Breakout Connector Board
- 1 x  &nbsp; 2.2K Resistor (used as a voltage divider to safely drop the +5v ADAM data to 3v for the Teensy)
- 1 x  &nbsp; 3.3K Resistor (used as a voltage divider to safely drop the +5v ADAM data to 3v for the Teensy)
- 1 x  &nbsp; ESD Suppressor / TVS Diode **(OPTIONAL)** &nbsp;P/N# PESD1FLEX,215 or equivelent
- 1 X  &nbsp; 10uF Capacitor **(OPTIONAL)**

## License

GNU General Public License v3.0
