# Troubleshooting Guide
---
Use this guide to troubleshoot any issues with your BrainPad. Please follow the steps on this page before going to [BrainPad Discussion Forum](https://forums.ghielectronics.com/c/brainpad) for help.

## Identify which BrainPad you have
A small number of early adopters received older versions of the BrainPad. The current production BrainPad has "BP2 Rev B" printed in the lower left corner. If your BrainPad doesn't look exactly like the image below, check the [Older BrainPad](older-brainpad.md) page for more details.

> [!Tip]
> Check the reset button. If it is smaller than the directional buttons you have an [**Older BrainPad**](older-brainpad.md).

![Production BrainPad](../images/production-brainpad.jpg)

## Bootloader
Push and hold the reset button for about 3 seconds. Does the LightBulb turn Green? If so you have a working bootloader and can skip the rest of this section.

If you did not get a green light in the step above, try updating the bootloader. To update the bootloader, download the latest bootloader DFU file from the [Resources](intro.md#bootloaders) page and then go to the [DFU Files](dfu-files.md) page for instructions on loading DFU files.

When the LightBulb turns Green, the BrainPad will present itself as a virtual storage device. Your computer should see it like any other storage device. The first time this happens, the operating system will need a few seconds to load the needed drivers.
![BrainPad virtual drive](images/brainpad-virtual-drive.png)

This virtual drive opens a window containing a text file that contains information such as the boot loader version. You can update the loader to the newest version to get the latest and greatest BrainPad features.

## Sample Demo
When the BrainPad virtual drive window is open (see Bootloader section), download [this demo]() file and drag it into the virtual drive window. 

## TinyCLR OS
We recommend starting with MakeCode to verify the hardware is functional first. Then, load TinyCLR OS as detailed in the [System Setup](../go-beyond/system-setup.md). Once loaded, your PC will detect a TinyCLR OS device as shown below.

![Device Manager](images/device-manager.png)

Visual Studio will also see the device:

![Visual Studio Deployment Transport](images/deployment-transport.png)

It is important that the TinyCLR OS version on the PC matches what is on the BrainPad. The same goes for the NuGet packages.

Our experts are ready to help on our [TinyCLR OS Forum](https://forums.ghielectronics.com/c/tinyclr-os).

---
You are on the documentation website for the BrainPad. The main website is found at [www.brainpad.com](http://www.brainpad.com/)
