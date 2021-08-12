# microbit-max7219

> microbit设备的 max7219（8*8 LED矩阵） 驱动。

### 连接

DIN --- MOSI(pin15)

CS  --- pin2

CLk --- SCK(pin13)

### 例子

```
import max7219
from microbit import spi,pin13,pin14,pin15,pin2
from time import sleep
import gc
gc.collect()

spi.init(baudrate=1000000, bits=8, mode=0, sclk=pin13, mosi=pin15, miso=pin14)
display = max7219.Matrix8x8(spi,pin2)

display.brightness(0)

screen=[
    [0,0,0,0,0,0,0,0],
    [0,1,1,0,0,1,0,0],
    [1,0,0,1,0,1,0,1],
    [1,0,0,1,0,1,1,0],
    [1,0,0,1,0,1,0,0],
    [1,0,0,1,0,1,1,0],
    [0,1,1,0,0,1,0,1],
    [0,0,0,0,0,0,0,0]
]

display.fill(0)
for y,line in enumerate(screen):
    for x,pixel in enumerate(line):
        display.pixel(y,x,pixel)
display.show()
```
