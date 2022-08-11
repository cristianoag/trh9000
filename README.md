# TRH9000
The Yamaha V9990 based open-source video card for the MSX

## Introduction

If you ever spent just a few minutes on YouTube searching for MSX content, I bet you certainly found some footage covering the V9990. Well, not specifically the V9990 chip, but video cards based on it.

The first video card based on the unreleased, kind of obscure Yamaha V9990 VDP chip was the Graphics9000 (or GFX9000). The GFX9000 is (was) an MSX standard graphics expansion device for home computers developed by Sunrise in 1994.

It was designed as an expansion cartridge for the MSX standard that can be installed in a slot on a computer that also connects to the computer’s video output and monitor. The device works as an additional independent video controller.

The device is based on the Yamaha V9990 video controller (VDP). The chip was based on the never-produced V9978 chip, designed specifically for use in computers of the alleged but not implemented (by the time of this writing) MSX3 standard. Compared to the V9978, the V9990 is not backward compatible with the V99x8 chips, and thus cannot be used as the main video controller of standard MSX-compatible computers.

## The TRH9000

TRH9000 is the name of a brand new open-source implementation of the GFX9000. It is a community effort to create everything required to build MSX cartridges capable to run V9990 software.

The goal is to make the card more accessible and improve the amount of software available for it. 

There are a few folks activelly helping with the project and I would like to call them out here:

* Alexandre Souza
* Darlei Duarte
* lintweaker
* Luciano Sturaro
* Thiago Valença


## Development Log 

* 8/10/2022 - Routing day 1. Decided to move from TSOP-II-40 to SOJ-40 as the pins in the first encapsulation are more difficult to connect/route to the V9990. Using 0.21 tracks to optimize routing. Will provide the RGB connector (standard) and a pin header with the SVGA signal. Updating the forums and rest of stakeholders. First image status uploaded. 
* 8/8/2022 - Initial component placement on the PCB. Still lot of work to do in order to improve routing. 
* 8/4/2022 - Reviewed the footprints in preparation to start creating the first PCB draft. Had to create a custom TSOP-2-40 footprint as I could't find any on the net. Using 0805 for the resistors and ceramic capacitors. THT electrolytics. Reviewing the list of pending questions to get everything ready for the PCB creation. (REV0)
* 8/2/2022 - I just finished the first (rev0) draft of the schematics and I'll run it through more experienced MSX hardware developers. Please, if you feel you have something to add, clone the repo and contribute. You can also reach out if you want to suggest something. You can see a PDF with the first draft [here](Docs/TRH9000_Schema_Revision_0.pdf). Kicad files are stored on the [hardware/kicad](hardware/Kicad/) folder. (REV0)

