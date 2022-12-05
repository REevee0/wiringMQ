## About

  This project basing on WiringOP and WiringPi. It has been rearranged to work on the MQ_Quad board belonging to Mango Pi company.
So use this only on MQ_QUAD.

Run on Linux compiled by showsoft 
https://github.com/showsoft/Mangopi-MQQuad-srv

## What working?

  Gpio Output and Input.


## How to download wiringMP

```
# apt-get update
# apt-get install -y git
# git clone https://github.com/REevee0/wiringMQ.git
```


## How to build wiringMP

```
# cd wiringMP
# ./build clean
# sudo ./build 
```


---
## The output of the gpio readall command

```
 +------+-----+----------+------+---+ MQ_Quad  +---+------+----------+-----+------+
 | GPIO | wPi |   Name   | Mode | V | Physical | V | Mode | Name     | wPi | GPIO |
 +------+-----+----------+------+---+----++----+---+------+----------+-----+------+
 |      |     |     3.3V |      |   |  1 || 2  |   |      | 5V       |     |      |
 |  264 |   0 |  PI8/SDA |  OUT | 0 |  3 || 4  |   |      | 5V       |     |      |
 |  263 |   1 |  PI7/SCL |  OUT | 0 |  5 || 6  |   |      | GND      |     |      |
 |  256 |   2 |      PI0 |  OUT | 1 |  7 || 8  | 1 | OUT  | TXD.0    | 3   | 224  |
 |      |     |      GND |      |   |  9 || 10 | 1 | OUT  | RXD.0    | 4   | 225  |
 |  226 |   5 |     TX.5 |  OUT | 1 | 11 || 12 | 1 | OUT  | PI1      | 6   | 257  |
 |  227 |   7 |     RX.5 |  OUT | 1 | 13 || 14 |   |      | GND      |     |      |
 |  269 |   8 |     PI13 | ALT2 | 0 | 15 || 16 | 0 | ALT2 | PI14     | 9   | 270  |
 |      |     |     3.3V |      |   | 17 || 18 | 0 | OFF  | PH4      | 10  | 228  |
 |  231 |  11 |   MOSI.1 |  OFF | 0 | 19 || 20 |   |      | GND      |     |      |
 |  232 |  12 |   MISO.1 |  OFF | 0 | 21 || 22 | 0 | OFF  | PI6      | 13  | 262  |
 |  230 |  14 |   SCLK.1 |  OFF | 0 | 23 || 24 | 0 | (null) | CS.0     | 15  | 229  |
 |      |     |      GND |      |   | 25 || 26 | 0 | (null) | CS.1     | 16  | 233  |
 |  266 |  17 |     PI10 | ALT2 | 0 | 27 || 28 | 0 | ALT2 | PI9      | 18  | 265  |
 |  267 |  19 |     PI11 | ALT2 | 0 | 29 || 30 |   |      | GND      |     |      |
 |  268 |  20 |     PI12 | ALT2 | 0 | 31 || 32 | 0 | ALT2 | PI5      | 21  | 261  |
 |  271 |  22 |     PI15 | ALT2 | 0 | 33 || 34 |   |      | GND      |     |      |
 |  258 |  23 |      PI2 | ALT2 | 0 | 35 || 36 | 0 | ALT3 | PH10     | 24  | 234  |
 |  272 |  25 |     PI16 | (null) | 0 | 37 || 38 | 0 | ALT2 | PI4      | 26  | 260  |
 |      |     |      GND |      |   | 39 || 40 | 0 | ALT2 | PI3      | 27  | 259  |
 +------+-----+----------+------+---+----++----+---+------+----------+-----+------+
 | GPIO | wPi |   Name   | Mode | V | Physical | V | Mode | Name     | wPi | GPIO |
 +------+-----+----------+------+---+  MQ_Quad +---+------+----------+-----+------+
```
## Enable SPI1
Add the configuration in the part below to /boot/orangepiEnv.txt, and then
restart the Linux system to open SPI1.

overlays=spi-spidev
param_spidev_spi_bus=1
param_spidev_spi_cs=1

##Enable I2C3 
Since there is a h616 processor on the board and the operating system is made by changing the files of the Orange Pi Zero 2 model, i2c seems to have i2c3 for now. I haven't tested the others yet.

SCL Pin = H4
SDA Pin = H5

Add the configuration in the  part below to /boot/orangepiEnv.txt, and then
restart the Linux system to open I2C3.

overlays=i2c3
## TO-DO

 More tests with communcation protocols.
