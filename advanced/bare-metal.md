# Bare Metal
---
You can also write programs from scratch using one of the more traditional C/C++ development tools. The easiest option would be to start with the Mbed online compiler and then export your project. You can also use the free open source GNU GCC tools to build your programs, which is what we used to build the TinyCLR OS firmware. Another option is to use a commercial compiler like the Keil compiler and development environment. Keil tools are free for programs up to 32KB (MDK-Lite).

> [!Tip]
> If you are not adding a SWD-JTAG tool, like ST-Link, follow the STM32 bootloader instructions on generating and loading DFU files. 

* [Keil Website](http://www.keil.com/)
* [Keil ARM MDK tools](http://www2.keil.com/mdk5)
* [GNU ARM Tools (GCC)](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads)

## STM32 Bootloader
The STM32 Bootloader lives on all STM32 chips. It is necessary to load files (loaders and/or firmware) onto the chip. Several TinyCLR OS supported boards will use this loader to load the software.

These instructions apply to all STM32 chips with built in USB and DFU features.

### Creating DFU file
The STM32 bootloader only accepts DFU file types, which can be generated from a HEX or BIN files. To generate a DFU file, download the "DfuSe USB device firmware upgrade STMicroelectronics extension" [software package](http://www.st.com/en/development-tools/stsw-stm32080.html)

Depending on using a HEX or BIN files, the instructions are slightly different.

#### From HEX files
1. Find and open "Dfu file manager" and select "I want to generate a DFU file".
2. Click on "S19 or Hex..." button to select the hex file.
3. Click "Generate..."
4. You now have the DFU file!

#### From BIN files
1. Find and open "Dfu file manager" and select "I want to generate a DFU file".
2. Click on "Multi BIN..." button to select the bin file.
3. Change the address to 08000000
4. Click on the "Add to list >>" button then click the "OK" button.
5. Click "Generate..."
6. You now have the DFU file!

### Uploading DFU Files
To set the STM32 chip in DFU mode, BOOT1 pin (if available) needs to be low and and BOOT0 needs to be high when the system powers up. If your system has a BOOT1 button, just hold the button down while powering the system up. The device manager will see the device "STM Device in DFU Mode".
1. Find and open "Open DfuSe Demo" (from the ST download higher in this page)
2. Under "Upgrade and Verify Action", click the "Chose..." button and select the firmware DFU file you want to load.
3. Click the "Upgrade" button.
4. Click the "Leave DFU mode" button.
5. Congratulations, your board is now running the loaded firmware!
