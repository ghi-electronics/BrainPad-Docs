# DFU Files
---
The microcontroller (processor) on the BrainPad can be updated with a DFU file over a USB cable. This is an advanced feature and should not be needed by most BrainPad users.

ST Microelectronics, the microcontroller manufacturer, provides the tools needed for the following steps. Download and install the "DfuSe USB device firmware upgrade STMicroelectronics extension" [software package](http://www.st.com/en/development-tools/stsw-stm32080.html)

## Loading DFU Files on the BrainPad
1. Press and hold the BOOT0 button. While continuing to hold the BOOT0 button, press and release the reset button. Wait for a second then release BOOT0 button.
2. Optionally, check the device manager to verify it shows "STM Device in DFU Mode".
3. Find and open "Open DfuSe Demo" (from the ST download higher in this page)
4. Under "Upgrade and Verify Action", click the "Choose..." button and select the DFU file you want to load.
5. Click the "Upgrade" button.
6. Click the "Leave DFU mode" button.
