# AVR from Scratch

Bare metal AVR tinkering using both C and Assembly. This project is a collection of some libraries and code for actual projects. The code is all either C99, or AVR assembly. One of the main goals of this project is to teach myself the needed concepts to write AVR code without the Arduino libraries. If it seems like I'm reinventing the wheel here, that's exactly the point. The other main goal is to make some cool projects, [led_matrix.c](https://github.com/nixpulvis/avr/blob/master/led_matrix.c) for example plays [Conway's Game of Life](http://en.wikipedia.org/wiki/Conway's_Game_of_Life) on an 8x8 LED matrix.

## Getting Started

I'm developing this project on OS X. If you are using another system, this project should still work for you. You will need to install the needed system dependencies yourself.

### Installing Dependencies

Make sure you have these packages installed with Homebrew:

- avr-binutils
- avr-gcc
- avr-libc
- avrdude

### Make

It's important to me to make building things easy. I've made a Makefile which aims to make compiling and flashing AVRs as easy as possible. It tries to help you out too, for example it will find a `/dev/tty.usb*` device automatically.

```sh
# Compile and upload "blink.c".
# By default it sets the BAUD to be compatible with Arduino Uno's
# at 115200.
TARGET=blink make

# Compile and upload "led_matrix.c"
# This will upload to a Arduino mini pro.
TARGET=led_matrix BAUD=57600 make

# Assemble and upload "hand_coded_blink.asm"
TARGET=hand_coded_blink LANGUAGE=asm make
```

TODO: Add info on all Makefile configuration ENV variables.

## Projects

TODO: LED Matrix, Conway's Game of Life.

## Libraries

I'm building some libraries as a part of this repository, as I need them. Anything possibly needed in more than one project is it's own library. Some of the libraries are for functionality of the AVR itself, and some are for external devices.

All Libraries have their own set of header and source files, with a common name in the `/lib` directory. All projects get built with all libraries, but this is something that I aim to improve as I continue refining the Makefile.

Libraries in this repository:

- [avr](#avr)
- [max7219](#max7219)
- [nrf24l01p](#nrf24l01p)

### avr

A collection of basic functions for the AVR. These functions work in harmony with the functions included in the AVR toolkit.

To view the API for this library read the [header file](https://github.com/nixpulvis/avr/blob/master/lib/avr.h).

### max7219

> Not fully functional yet.

A set of functions for using the [MAX7219CNG LED Display Driver](https://www.sparkfun.com/products/9622). This chip can control up to 8 digit 7-segment numeric LED displays, LED bar graphs, or 64 individual LEDs.

To view the API for this library read the [header file](https://github.com/nixpulvis/avr/blob/master/lib/max7219.h).

### nrf24l01p

> Not fully functional yet.

A set of functions for using the [Nordic Transceiver nRF24L01+ Module with RP-SMA](https://www.sparkfun.com/products/705).

To view the API for this library read the [header file](https://github.com/nixpulvis/avr/blob/master/lib/nrf24l01p.h).

## Reference

- [avr-libc manual](http://www.nongnu.org/avr-libc/user-manual/pages.html)