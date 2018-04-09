# Troubleshooting Guide
---
This guide will try to take you through every step to troubleshoot any issues. This will also help our support team in helping you, so please go through this first.

# Identify which BrainPad you have
There are older BrainPad versions that early adopters recieved. If your BrainPad doesn't look exactly like the image below then check the [Older BrainPad](older-brainpad.md) page for more details.

> [!Tip]
> Note the reset button. If it is small then you have an [Older BrainPad](older-brainpad.md)

(image)

# Bootloader
Push and hold the reset button for about 3 seconds. Does the LightBulb turn Green? If so, you can skip this step.

To update the bootloader, download the latest bootloader DFU file from the [Resources](intro.md#bootloaders) page and then see the [DFU Files](dfu-files.md) page for instructions on loading DFU files.

When the LightBulb turns Green, the BrainPAd will present itself as a virtual storage device. Your computer should see it like any other storage device. The first time this happens, the operating system will need a few seconds to load the needed drivers.
(image of the drive and maybe device manager)

This virtual drive comes up with a text file that has some info, like the boot loader version. You can update the loader to the latest verion to get teh latest and greatest features.

# Sample Demo
When the virtual drive is up (see Bootloader section), download [this demo]() file and drag it into the virtual drive. 

# TinyCLR OS
We recommend starting with MakeCode to verify the hardware is functional first. Then, load the TinyCLR OS as detailed in the [System Setup](../go-beyond/system-setup.md). Once loaded, your PC will detect a TinYCLR Os device.

(image device manager)

Visual Studio will also see the device

(show transport)

It is important that the TinyCLR OS version on the PC matches what is on the BrainPad. Same goes for the NuGet packages.

Our experts are ready to help on our [TinyCLR OS forum](https://forums.ghielectronics.com/c/tinyclr-os)

---
You are on the documentation website for the BrainPad. The main website is found at [www.brainpad.com](http://www.brainpad.com/)
