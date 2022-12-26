# TRH9000
The Yamaha V9990 based open-source video card for the MSX

## Kicad Project Files

* MSX_Breadboard_Large_V9990/ - Project for the prototype cartridge to validate the main TRH9000 circuit. The board project is based on the work done by Alexey Wierzbowsky and was adapted to have pads for memory chips, V9990, and two different video chips. We are testing the Sony RGB encoder (CXA2075M) and the TI Auto-Detecting SD/HD/PC Video Sync Separator (LMH1980) to generate the video signal.
* TRH9000.cxa2075/ - Main TRH9000 circuit and PCB project using the Sony CXA2075 RGB encoder.
* TRH9000.lmh1980/ - Main TRH9000 circuit and PCB project using the Texas LMH1980 sync separator. **This board is functional but doesn't follow the best practices when connecting to the RGB**
* TRH9000S/ - Main TRH9000S circuit and PCB board project. This version offers two connectors. One DIN8 270 to get input from the MSX computer and another DB15 as the RGB/VGA output. **This board is also using the LMH1980 and doesn't follow the best practices when connecting to the RGB. Please do not use this board on your vintage hardware. It is still under development and can cause harm to your hardware**


## License 

This work is licensed under the CERN OHL-S v2. You may redistribute and modify this project and its documentation under the terms of the CERN-OHL-S v2.

![Open Hardware](https://raw.githubusercontent.com/cristianoag/trh9000/main/Images/1024px-Open-source-hardware-logo.svg.png)