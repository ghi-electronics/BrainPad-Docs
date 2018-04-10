# DFU Files
---
The microcontroller (processor) on the BrainPad can be updated over USB cable using a DFU file. This is an advanced feature and should not be needed by most BrainPad users.

ST Microelectronics, the microcontroller manufacture, provides the tools needed for the following steps. Download and install the "DfuSe USB device firmware upgrade STMicroelectronics extension" [software package](http://www.st.com/en/development-tools/stsw-stm32080.html)

# Loading DFU Files
1. Press and hold the BOOT0 button. While continuing to hold the BOOT0 button, press and release the reset button quickly. Wait for a second then release BOO0 button.
2. Optionally, check the device manager to verify it shows "STM Device in DFU Mode".
3. Find and open "Open DfuSe Demo" (from the ST download higher in this page)
4. Under "Upgrade and Verify Action", click the "Chose..." button and select the DFU file you want to load.
5. Click the "Upgrade" button.
6. Click the "Leave DFU mode" button.

# Creating DFU file
If you have a DFU file to load then these steps are not necessary. For example, the BrainPad bootloader is already a DFU file.

Depending on using a HEX or BIN files, the instructions are slightly different.

## From HEX files
1. Find and open "Dfu file manager" and select "I want to generate a DFU file".
2. Click on "S19 or Hex..." button to select the hex file.
3. Click "Generate..."
4. You now have the DFU file!

## From BIN files
1. Find and open "Dfu file manager" and select "I want to generate a DFU file".
2. Click on "Multi BIN..." button to select the bin file.
3. Change the address to 08000000
4. Click on the "Add to list >>" button then click the "OK" button.
5. Click "Generate..."
6. You now have the DFU file!
