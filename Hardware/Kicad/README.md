# TRH9000
The Yamaha V9990 based open-source video card for the MSX

## Kicad Project Files

* MSX_Breadboard_Large_V9990/ - This project involves a prototype cartridge designed to validate the main TRH9000 circuit. The board project is based on the work done by Alexey Wierzbowsky and has been adapted to include pads for memory chips, V9990, and two different video chips. We are currently testing the Sony RGB encoder (CXA2075M) and the TI Auto-Detecting SD/HD/PC Video Sync Separator (LMH1980) to generate the video signal.

* TRH9000.cxa2075/ - This is the main TRH9000 circuit and PCB project that utilizes the Sony CXA2075 RGB encoder. This board has been tested and is fully functional, delivering very good image quality.

* TRH9000.lmh1980/ - This is another version of the main TRH9000 circuit and PCB project that uses the Texas LMH1980 sync separator. While this board is functional, it doesn't follow the best practices when connecting to the RGB.

* TRH9000S/ - The TRH9000S is the latest version of the main TRH9000 circuit and PCB board project. This version features two connectors, including one DIN8 270 to receive input from the MSX computer and another DB15 as the RGB/VGA output. However, please note that this board also uses the LMH1980 and does not follow the best practices when connecting to the RGB. As a result, I recommend that you not use this board on your vintage hardware, as it is still under development and may cause harm to your computers.
* 
## License 

This work is licensed under the CERN OHL-S v2. You may redistribute and modify this project and its documentation under the terms of the CERN-OHL-S v2.

![Open Hardware](https://raw.githubusercontent.com/cristianoag/trh9000/main/Images/1024px-Open-source-hardware-logo.svg.png)