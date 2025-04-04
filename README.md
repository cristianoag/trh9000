# TRH9000
The Yamaha V9990 based open-source video card for the MSX

![TRH9000](Labels/TRH9000_Label_72x52_Patolas.png)

## Introduction

If you ever spent just a few minutes on YouTube searching for MSX content, I bet you certainly found some footage covering the V9990. Well, not specifically the V9990 chip, but video cards based on it.

The first video card based on the unreleased, kind of obscure Yamaha V9990 VDP chip was the Graphics9000 (or GFX9000). The GFX9000 is (was) a graphics expansion device for MSX computers developed by Sunrise in 1994.

It was designed as an expansion cartridge for the MSX standard that can be installed in a slot on a computer that also connects to the computer’s video output and monitor. The device works as an additional independent video controller.

The device is based on the Yamaha V9990 video controller (VDP). The chip was designed specifically for use in computers of the alleged but not implemented (by the time of this writing) MSX3 standard. The V9990 is not backward compatible with the V99x8 chips, and thus cannot be used as the main video controller of standard MSX-compatible computers.

## The TRH9000

TRH9000 is an open-source implementation of the GFX9000, representing a community-driven effort to document everything necessary to build MSX cartridges that can run V9990 software.

| PCB Front | PCB Back |
| --- | --- |
| ![TRH9000](Images/2025-01-01_08-23.png) | ![TRH9000](Images/2025-01-01_08-23_1.png) |

The goal is to make those cards more accessible and improve the amount of software available for it. 

## Technical Information

The TRH9000 is a graphics expansion cartridge designed for MSX computers that was developed by a community of MSX enthusiasts as an open-source implementation of the GFX9000. 

### Selection Logic
For the TRH9000, the control logic is implemented by two ICs. According to the not exhaustive list of IO ports documented [here](https://www.msx.org/wiki/I/O_Ports_List). The IO ports used the by an GFX9000 compatible cartridge must be 60h~6Fh*. The 74LS138 IC on the board performs the selection of those IO ports and with the aid of the 74LS32 performs the activation of the appropriate signals on the V9990 chip.

> **Note:** Very important to use the 74LS138 and 74LS32 ICs. The 74HC138 and 74HC32 are not 100% compatible with the logic levels used by old MSX computers and if used, the cartridge may not work properly. 74HCT138 and 74HCT32 are also compatible with the old logic levels and can be used as a replacement.

### RAM chips

The KM428C256 RAM chip is the primary memory module used in the TRH9000. It is a CMOS 256K x 8 bit dual-port dynamic random-access memory (DRAM) chip that serves as the primary memory module in the cartridge. We use two memory chips, wired to the Yamaha V9990 VDP.

### Connectors

On its latest version, the TRH9000 features three types of video output connectors: a DB15 RGB/VGA connector, a RCA composite connector and a mini-DIN 4 SVideo connector. The DB15 connector is a standard video connector that supports VGA, and RGB, making it a versatile choice for connecting to various types of displays. The SVIDEO signal, on the other hand, is a video signal that carries the chrominance and luminance components of the video separately, resulting in a higher quality image than composite video that is output on the RCA connector. 

### Video Output

#### RGB 
The TRH9000 cartridge produces RGB signal with a horizontal frequency of 15.7KHz, which was the standard at the time of the V9990 chip's release. If you plan to connect the cartridge directly to your monitor using a VGA cable, it's important to ensure that your monitor supports synchronization at 15.7KHz.

You can see a list of modern monitors with support to 15.7KHz available at http://15khz.wikidot.com/

If you're not getting any image from the cartridge connector, it indicates that your monitor cannot sync at 15.7KHz. Typically, modern monitors can only sync at frequencies above 31KHz.

In such a scenario, you will require an adapter to upscale the frequency, making it compatible with your monitor. These adapters are commonly used for vintage video games and are readily available in various marketplaces. Here are a few options to consider:

||Description|Link|
|--|--|--|
|![Alt text](Images/image.png)|TZT HamGeek GBSC Converter GBS Control Retro Video Game Signal Converter Gaming Accessory  |[Ali Express](https://s.click.aliexpress.com/e/_DcZRM6T)
|![Alt text](Images/image-1.png)|OSSC HDMI-Compatible Converter Open Source Scan Adapter Kit with Game Cable for Retro Game Consoles  |[Ali Express](https://s.click.aliexpress.com/e/_DnNQGvv)
|![Alt text](Images/image-2.png)|Retrotink 2X Scart | https://www.retrotink.com/product-page/retrotink-2x-scart

If you decide to use the Retrotink you will need a VGA to SCART cable. That is easy to solder and you need to connect the signals in the following way:

|VGA||SCART|Signal|
|-|-|-|-|
|1|-->|15 |Red
|2|-->|11| Green
|3|--> |7 |Blue
|5|--> |21 |GND
|13|-->|20| Sync

By request of the community, a jumper was included on the latest PCB version to provide optionally 5V on the pin 9 of the VGA connector. This is useful for those who want to use build a SCART cable that depending on the monitor may require 5V in some pins. 

The jumper is located on the back of the PCB and is labeled as "JP1". The default position is open, so if you need to use it, you will need to close it with a solder blob.

Here is a diagram of the DH15 connector:

![RGB pinout](Images/RGB_PINOUT.png)

#### S-Video and Composite

The TRH9000 cartridge provides support for both S-Video and Composite video outputs. These video signals are transmitted through respective connectors that are located on the upper edge of the cartridge PCB. 

## Bill of Materials

[TRH9000 Interactive BOM](https://htmlpreview.github.io/?https://github.com/cristianoag/trh9000/blob/main/Hardware/Kicad/TRH9000_1.7/bom/ibom.html)

|References|Value|Footprint|Qtd|Link|
|-|-|-|-|-|
|C1, C6, C7, C8, C17, C19, C20, C22, C24	|0.1uF	|C_0805_2012Metric	|9|[Ali Express](https://s.click.aliexpress.com/e/_DkAAT2J)
|C9, C11, C12, C13, C14, C15, C26|	220uF	|CP_EIA-3528-15_AVX-H|	7|[Ali Express](https://s.click.aliexpress.com/e/_DCrPttV)
|C3, C4	|27pF|	C_0805_2012Metric|	2|[Ali Express](https://s.click.aliexpress.com/e/_DkAAT2J)
|C5, C10|	47pF	|C_0805_2012Metric|	2|[Ali Express](https://s.click.aliexpress.com/e/_DkAAT2J)
|C16, C18|	1uF	|C_0805_2012Metric	|2|[Ali Express](https://s.click.aliexpress.com/e/_DkAAT2J)
|C23, C25|	10nF|	C_0805_2012Metric|	2|[Ali Express](https://s.click.aliexpress.com/e/_DkAAT2J)
|C2|	10uF|	C_0805_2012Metric	|1|[Ali Express](https://s.click.aliexpress.com/e/_DkAAT2J)
|C21|	47uF|	CP_EIA-3528-15_AVX-H|	1|[Ali Express](https://s.click.aliexpress.com/e/_DCrPttV)
|R1, R3, R4, R5, R6, R10|	4K7	|R_0805_2012Metric|	6|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|R14, R15, R16, R17, R18, R19|	75R	|R_0805_2012Metric|	6|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|R20,R21,R22|470R|R_0805_2012Metric|3|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|R7, R12|	2K2	|R_0805_2012Metric|	2|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|			R2	|10M	|R_0805_2012Metric|	1|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|			R8	|1K	|R_0805_2012Metric|	1|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|			R9	|100R	|R_0805_2012Metric|	1|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|			R11	|220R	|R_0805_2012Metric	|1|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|			R13	|3K3|	R_0805_2012Metric	|1|[Ali Express](https://s.click.aliexpress.com/e/_DEyTmBN)
|			L1, L2|	4.7uH|	L_0805_2012Metric	|2|[Ali Express](https://s.click.aliexpress.com/e/_Dern3vN)
|			U4, U5	|KM428C256	|SOJ-40_400mil|	2|[UT Source](https://www.utsource.net/itm/p/781989.html)
|			U1	|74HC138	|SO-16_3.9x9.9mm_P1.27mm	|1|[Ali Express](https://s.click.aliexpress.com/e/_De0MrAf)
|			U2	|74HC32	|SO-14_3.9x8.65mm_P1.27mm|	1|[Ali Express](https://s.click.aliexpress.com/e/_DlCjJDN)
|			U3|	V9990|	LQFP-128_28x28mm_P0.8mm	|1|[The Retro Hacker Store](https://theretrohacker.com/product/v9990-non-vga-video-controller-ic-qfp-128/)
|			U6	|CXA2075M	|SOP-24_7.5x15.4mm_P1.27mm|	1|[Ali Express](https://s.click.aliexpress.com/e/_DBjZMTN)
|			Y1	|21.47727Mhz	|Crystal_HC49-U_Vertical|	1|[Ali Express](https://s.click.aliexpress.com/e/_DDj3q9t)
|			X1	|14.31818MHz|	Oscillator_DIP-4|	1|[Ali Express](https://s.click.aliexpress.com/e/_DEBzKw3)
|			RV1, RV2, RV3	|500R	|Potentiometer_Bourns_3314G_Vertical	|3|[Ali Express](https://s.click.aliexpress.com/e/_DnebEdD)
|			Q1	|BC817	|SOT-23	|1|[Ali Express](https://s.click.aliexpress.com/e/_DBlTES3)
|			J4	|S-Video	|Mini DIN 4 Pin Connector | 1 | [Ali Express](https://s.click.aliexpress.com/e/_De7X4Ud)
|			J2	|RGB	|DSUB-15-HD_Female_Horizontal	|1|[Ali Express](https://s.click.aliexpress.com/e/_DntckRl)
|            J3	|Composite	|RCA-2_Horizontal	|1|[Ali Express](https://s.click.aliexpress.com/e/_DBxnR6d)

## Community Contributions

There are a few folks activelly helping with the project and I would like to call them out here:

* Alexandre Souza
* Doomn00b
* Darlei Duarte
* lintweaker
* Luciano Sturaro
* MetalGear2
* sdsnatcher73
* sdsnatcher
* Thiago Valença
* Wagner Tavares


## License 

![Open Hardware](Images/ccans.png)

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/).

* If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
* You may not use the material for commercial purposes.
* You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

**ATTENTION**

This project was made for the retro community and not for commercial purposes. So only retro hardware forums and individual people can build this project.

THE SALE OF ANY PART OF THIS PROJECT WITHOUT EXPRESS AUTHORIZATION IS PROHIBITED!
