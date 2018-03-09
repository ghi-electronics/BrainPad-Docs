# Mbed
---
## Using Mbed with the BrainPad

Mbed is an online compiler platform. There is nothing to install, just log in and start coding!
One of the supported boards is Nucleo-F401RE, which uses the exact same microcontroller found on BrainPad. Start with it to build and compile then follow the STM32 bootloader instructions at the bottom of this page. 

This video shows the steps needed to use Mbed.

<iframe width="560" height="315" src="https://www.youtube.com/embed/8qcKctDvV_4" frameborder="0" allowfullscreen></iframe>

* [mbed Website](https://developer.mbed.org/)
* [Nucleo-F401RE](https://developer.mbed.org/platforms/ST-Nucleo-F401RE/)

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
