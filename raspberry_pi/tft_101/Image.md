Displaying Images on the TFT 1.8" 128x160 Display
================================================
Today I was playing with the TFT 1.8" 128x160 Display and I wanted to display an image on it.
The pins and images are defined in the [Pins](Pins.md) and here I'm detailing how I got it to 
work.

# Pin layout
|Screen Pin|Board Pin|Notes|
|----------|---------|-----|
|GND|GND|Ground, black, no brainer|
|BL|3.3v|Backlight, red, no brainer|
|VCC|5v|Voltage, red, no brainer|
|CLK|SCLK, PIN 23|Clock, orange, a little brainer because different name|
|DIN|MOSI? PIN 19|Data In, green, I am honestly not even sure at this point|
|D/C|GPIO 25|Data/Command, Orange again, hameno?|
|CS|CE0, PIN 24|Chip Select, white, no brainer|
|RST|GPIO 24|Reset, Yellow, no brainer|

# Sample Python Code
This comes from the Python st7735 library. The repo can be seen [here](https://github.com/degzero/Python_ST7735)

```python
import sys
from PIL import Image

import ST7735 as TFT
import Adafruit_GPIO as GPIO
import Adafruit_GPIO.SPI as SPI

if len(sys.argv) < 2:
    print("Usage: {} <image_file>".format(sys.argv[0]))
    sys.exit(1)

image_file = sys.argv[1]

WIDTH = 128
HEIGHT = 160
SPEED_HZ = 4000000


# Raspberry Pi configuration.
DC = 25
RST = 24
SPI_PORT = 0
SPI_DEVICE = 0

# Create TFT LCD display class.
disp = TFT.ST7735(
    DC,
    rst=RST,
    spi=SPI.SpiDev(
        SPI_PORT,
        SPI_DEVICE,
        max_speed_hz=SPEED_HZ))

# Initialize display.
disp.begin()

# Load an image.
image = Image.open(image_file)

r, g, b = image.split()
print(r, g, b)
image = Image.merge('RGB', (b, g, r))


# Resize the image and rotate it so matches the display.
image = image.resize((WIDTH, HEIGHT))

# Draw the image on the display hardware.
print('Drawing image')
disp.display(image)
```

## A few notes,
- This code works with the pin layout we made above. so if you change the pins you have to update the code
- For some reason the library or my screen were switching the red and blue color chanels, and the result looked wonky.
  That's why I had to switch them with image.split and Image.merge
