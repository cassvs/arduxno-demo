# ArdUxno-demo

A quick-and-dirty proof-of-concept port of [Devine Lu Linvega](https://xxiivv.com/)'s amazing [Uxn](https://wiki.xxiivv.com/site/uxn.html) virtual stack machine to an STM32 microcontroller. `uxn.c` and `uxn.h` are bundled with the loader program, `arduxno-demo.ino`, which is essentially `uxncli.c` with all the IO calls modified for the Arduino environment.

## Features

Feature | Implemented | Tested
---|---|---
Uxn VM | ✔️ | ✔️
ROM loading from SD card | ✔️ | ✔️
System device | ✔️ | ?
Console device (serial output) | ✔️ | ✔️
Console device (serial input) | ✔️ | ❌
File device (for SD card access) | ✔️ | ❌
Time device | ❌ | ❌
Screen device | ❌ | ❌
Audio device | ❌ | ❌
Controller device | ❌ | ❌
Mouse device | ❌ | ❌

## Supported Hardware

Currently only tested on a WeAct BlackPill v3, which uses an STM32F411CE MCU. A microSD card adapter is connected to the default SPI1 pins (A4 -> CS, A5 -> SCK, A6 -> CIPO, A7 -> COPI).

Any MCU or dev board supported by the Arduino ecosystem should work, provided that the MCU has _more than_ 64KiB of RAM. Standard STM32F103-based BluePill boards might not work, as many only have 64KiB. (There are variants with 128KiB.) Most AVR-based boards (Arduino Uno, Mega, Nano, etc.) also do not have enough RAM.

I have not tested this with PlatformIO, Arduino IDE 2.0, or any other tools. I've only used Arduino 1.8.

## Getting Started

1. Connect an SD card adapter to your board's default SPI interface
2. Connect to your board using your preferred programming method (USB bootloader, SWD, etc.)
3. Connect your board's default UART interface (RX/TX pins, native USB serial, etc.) to some console, so that you can see debugging messages when the board boots
4. Place a Uxn ROM named "`uxn-test.rom`" in the root directory of an SD card, and insert the card into the adapter
5. Upload ArdUxno-demo to your board

## Moving Forward

Ideally, this port would not use the Arduino platform at all. I used it because it was quick and easy, and my bare-metal STM32 skills are not up to SD card IO and USB serial ports yet.

## Questions

If you have any questions, suggestions, or improvements, feel free to open an issue, or send me a toot `@cassvs@mastodon.social`

Thanks to [Devine Lu Linvega](https://xxiivv.com/)
