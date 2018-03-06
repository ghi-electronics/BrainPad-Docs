# Plain C/C++
---
You can also write programs from scratch using one of the more traditional C/C++ development tools. The easiest option would be to start with the Mbed online compiler and then export your project. You can also use the free open source GNU GCC tools to build your programs, which is what we used to build the TinyCLR OS firmware. Another option is to use a commercial compiler like the Keil compiler and development environment. Keil tools are free for programs up to 32KB (MDK-Lite).

> [!Tip]
> If you are not adding a SWD-JTAG tool, like ST-Link, follow the [STM32 bootloader](../../../hardware/loaders/stm32_bootloader.md) instructions on generating and loading DFU files. 

* [Keil Website](http://www.keil.com/)
* [Keil ARM MDK tools](http://www2.keil.com/mdk5)
* [GNU ARM Tools (GCC)](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads)
* [STM 32 Bootloader Instructions](../../../hardware/loaders/stm32_bootloader.md)