# ICE40HXDevBoard: an expandable iCE40HX4K development board

![ICE40HXDevBoard PCB](/images/ICE40HXDevBoard.png)

## Features

The specification for this development board is as follows:

* [iCE40HX4K](https://www.latticesemi.com/view_document?document_id=49312) in
144 pin QFP
  * [N25Q032A](https://docs.rs-online.com/0866/0900766b80f7f8ab.pdf) 32 Mbit SPI flash
* Space for two 5mm x 3mm oscillators
* [W9825G6KH](https://www.mouser.co.uk/datasheet/2/949/w9825g6kh_a04-1489735.pdf) 4M x 4 Banks x 16 bits SDRAM (32 MByte)
* PS/2 port with two channels for a mouse and keyboard
* I2C:
  * [DS3231M](https://www.analog.com/media/en/technical-documentation/data-sheets/ds3231m.pdf) RTC
  * [AT24C64](https://ww1.microchip.com/downloads/en/devicedoc/doc0336.pdf) EEPROM
  * Header for I2C connections
* RGB LED
* 4 buttons
* Buzzer
* [FT231XS](https://ftdichip.com/wp-content/uploads/2024/05/DS_FT231X.pdf) USB to UART converter with USB-C socket doubling up as the source of 5V power
* [MicroSDCard](https://en.wikipedia.org/wiki/SD_card) slot
* [PMOD](https://en.wikipedia.org/wiki/Pmod_Interface) header
* 40 pin expansion:
  * 3.3V and 5V power, 27 general purpose IO, 2 clock pins, shared I2C bus

A [schematic](ICE40HXDevBoard.pdf) is included here, along with the
[KiCAD](https://www.kicad.org) data files, whcih are in KiCAD 6 format.

## HDMI expansion card features

An expansion card featuring HDMI and I2S output on a 3.5mm jack has been built:

* [TFP410PAP](https://www.ti.com/lit/ds/symlink/tfp410.pdf) HDMI transmitter
  * Full size HDMI connector
* [PCM5100A](https://www.ti.com/lit/ds/symlink/pcm5100a.pdf) I2S DAC
  * 3.5mm stereo jack

## VGA expansion card features

A further, unbuilt, expansion card has been designed for VGA output:

* [ADV7123](https://www.analog.com/media/en/technical-documentation/data-sheets/ADV7123.pdf) RGB DAC
* [PCM5100A](https://www.ti.com/lit/ds/symlink/pcm5100a.pdf) I2S DAC
  * 3.5mm stereo jack

## PCB design

The PCBs are 4 layer boards.  My boards were manufactured by
[JLCPCB](https://www.jlcpcb.com).

## Using

The jumper mechanism to route the SPI signals which carry the configuration data
from the programmer was borrowed directly from the [Lattice’s iCE40 UltraPlus
Breakout Board](https://www.latticesemi.com/view_document?document_id=51987).

Any iCE40 compatible programmer should be useable. I built my own, out of a Pi
Pico, the software for which is documented in [another
repo](https://github.com/aslak3/spi-flasher). The programmer has been used to
program both the attached flash and the FPGA directly.

The header is a IDC10 in 100mil pitch. For the pinout refer to the schematic.

## Possible gotchas

The design of the FPGA board is a tweaked version of the build I have on my bench, since it has some issues:

* The PMOD pinning was backwards.
* The PS/2 port lacked clamping diodes due to the FPGA's intolerance of 5V signals from the PS/2 device. Remarkably I see no problems with my board, but it is not correct not having diodes to clamp the PS/2 data and clock lines to 3.3V.

The following features have not been tested yet:

* The MicroSDCard slot
* The SDRAM
* The I2C RTC
* The I2S DAC

## Blog

The best place to learn about this board is undoubtably [my
blog](https://www.aslak.net/).
