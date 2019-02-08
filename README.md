spiflash
====

This repository is a GitHub fork of the repository found at [this BitBucket repo](https://bitbucket.org/hudson/spiflash).  I claim no responsibility/rights for this repo.  The only change is this line of the `README.md` file; all other files are exactly as they are on the original source.

More info: https://trmm.net/SPI_flash

Commands

* `i`: Read chip ID; if all 0xFF or 0x00, then something is wrong.
* `r7f0000`↵: read 16 bytes from 0x7f0000 and hex dump them.
* `e7f0000`↵: erase a sector at address 7f0000.
* `u190000 1a0000`↵: Upload (and erase) 0x1a0000 bytes to 0x190000.
* to read the entire rom, shell out and run:

    rx < /dev/ttyACM0 > /dev/ttyACM0 rom.bin

Otherwise, please read the source.
