# Extended SPIFlash documentation

This site assumes a Teensy 3.2, although it is designed to be backwards compatible with the 3.1.

The pinout of the Teensy is as follows:

>>> to do: insert image

On the Teensy 3.2, the wiring is as follows:

| Pin number (Teensy) | Function (from SOIC clip page) | Color (from SOIC clip page) |
| ------------------- | ------------------------------ | --------------------------- |
| 10                  | `!CE` (chip select)            | white                       |
| 12                  | `SO` (`SPI_MISO`)              | brown                       |
| NC                  | `!WP` (write protect)          |                             |
| `GND`               | `GND`                          | black                       |
| `3.3V`              | `Vcc +3v3`                     | red                         |
| NC                  | `!RST` (reset)                 |                             |
| 13                  | `SCK` (`SPI_SCLK`)             | green                       |
| 11                  | `SI` (`SPI_MOSI`)              | blue                        |

For the SOIC clip (buyable [here in 8pin][8pinsoic] and [here in 16pin][16pinsoic]), the pinout depends on the chip.
For 8-pin chips, see the [8-pin pinout details][8pin].  For 16-pin chips (less common), see the [16-pin pinout details][16pin].

[8pinsoic]: https://www.amazon.com/CPT-063-Test-Clip-SOIC8-Pomona/dp/B00HHH65T4/ref=pd_lpo_vtph_147_tr_t_1?_encoding=UTF8&psc=1&refRID=M35BTM5CX2KBHXGK7R9D "8-pin Pomona SOIC clip"
[16pinsoic]: https://www.amazon.com/SOIC-Test-Chips-either-Leads/dp/B072XTNB5P/ref=sr_1_2?s=industrial&ie=UTF8&qid=1550514427&sr=1-2&keywords=pomona+16+pin+soic "16-pin Pomona SOIC clip"
[8pin]: 8pin.html "8-SOIC-clip pinout"
[16pin]: 16pin.html "16-SOIC-clip pinout"

Once everything is wired, connect the Teensy with a micro-USB cable to the computer.  It should show up as a serial device, typically `/dev/ttyACM0` or something.

## Serial commands

Assuming your device label is `/dev/ttyACM0`:

* Most useful:
  * Read the entire image: `rx < /dev/ttyACM0 > /dev/ttyACM0 rom.bin`
  * Write a section: `pv new-rom.section.rom > /dev/ttyACM0`
* Less useful, lower-level:
  * Read 16 bytes from 0x7f0000: `r7f0000`
  * Erase a sector at address 0x7f0000: `e7f0000`  (typically not needed, since upload erases sectors as needed)
  * Upload (and erase) 0x1a0000 bytes to 0x190000: `pv new-section.rom > /dev/ttyACM0`
  * Read chip ID: `i`  (If it comes back with entirely 0xFF or 0x00, then something is wrong)

