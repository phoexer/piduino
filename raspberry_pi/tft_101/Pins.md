Pins are a pain.
================

So I honestly don't understand pins, so lets take notes, there are probably mistakes here. and there are
probably several things I've gotten wrong. So if you see something wrong, please let me know. or open a 
PR and fix it. 

| Pin  | Name | Description                                  | Alternate Name(s) |
|------| ---- |----------------------------------------------|------------------|
| GND  |Ground| the negative terminal. the minus for your 5v or 3v red |                  |
| VCC  |Voltage| the positive terminal. the plus for your 5v | (maybe VIN?)     |
| VIN  |Voltage In| the positive terminal. the plus for your 5v | VCC              |
| CLK  |Clock| the clock pin. used to clock in data | SCK, SCL         |
| SCK  |Serial Clock| the serial clock pin. used to clock in data | CLK, SCLK, SCL   |
| SCL  |Serial Clock| the serial clock pin. used to clock in data | CLK, SCLK, SCK   |
| SCLK |Serial Clock| the serial clock pin. used to clock in data | CLK, SCK, SCL    |
| BLK  |Backlight| the backlight pin. used to turn on the backlight | LED, LITE        |
| SDA  | Serial Data|birectional data pin. Connected to MOSI| MOSI             |
| MOSI | Microcontroller Out, Serial In| It is used to send data from the microcontroller to the SD card and/or display.||
| MISO | Microcontroller In, Serial Out| It is used to send data from the SD card and/or display to the microcontroller.||
| CS   |Chip Select| It is used to select the SD card and/or display.||
| D/C  |Data/Command| It is used to select the SD card and/or display.| RS, A0           |
| RS   |Register Select| It is used to select the SD card and/or display.| DC, A0           |
| A0   |Address 0| It is used to select the SD card and/or display.| DC, RS           |
| RST  |Reset| It is used to reset the SD card and/or display.| RESET            |
| DIN  |Data In| It is used to send data from the microcontroller to the SD card and/or display.| MOSI, SDA        |               


