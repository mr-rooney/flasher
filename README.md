Firmware Flasher
================

Firmware flasher to update the firmware of the nav.HAT microcontroller. 

Thanks to Tormod Volden for providing this source code. The original code can be found at https://sourceforge.net/p/stm32flash/code/ci/master/tree/.
The code has been slightly modified to fit for the STM32F091CB microcontroller used on the nav.HAT. See the git log for further information.


Compiling the sources
=====================

host> export CC=arm-linux-gnueabihf-gcc
host> make

Copy the created binary *stm32flash* and the appropriate binary for the HAT microcontroller (in this example *application.binary*)
to the file system of your Raspberry Pi.

Usage
=====

    raspi> sudo su
    raspi> insmod i2c-gpio-param.ko
    raspi> echo 5 2 3 2 100 > /sys/class/i2c-gpio/add_bus
    raspi> ./stm32flash -R -i 17,-18,18:-17,18,-18,18 -w application.binary -v -g 0x00 -a 0x41 /dev/i2c-5
    raspi> shutdown now

**Ensure that you unplug and replug the power supply of the Raspberry Pi after shutting down.**