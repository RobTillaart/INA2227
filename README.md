
[![Arduino CI](https://github.com/RobTillaart/INA2227/workflows/Arduino%20CI/badge.svg)](https://github.com/marketplace/actions/arduino_ci)
[![Arduino-lint](https://github.com/RobTillaart/INA2227/actions/workflows/arduino-lint.yml/badge.svg)](https://github.com/RobTillaart/INA2227/actions/workflows/arduino-lint.yml)
[![JSON check](https://github.com/RobTillaart/INA2227/actions/workflows/jsoncheck.yml/badge.svg)](https://github.com/RobTillaart/INA2227/actions/workflows/jsoncheck.yml)
[![GitHub issues](https://img.shields.io/github/issues/RobTillaart/INA2227.svg)](https://github.com/RobTillaart/INA2227/issues)

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/RobTillaart/INA2227/blob/master/LICENSE)
[![GitHub release](https://img.shields.io/github/release/RobTillaart/INA2227.svg?maxAge=3600)](https://github.com/RobTillaart/INA2227/releases)
[![PlatformIO Registry](https://badges.registry.platformio.org/packages/robtillaart/library/INA2227.svg)](https://registry.platformio.org/libraries/robtillaart/INA2227)


# INA2227

Arduino library for the INA2227, I2C, 16 bit, dual channel, voltage, current, power and energy sensor.


## Description

**Experimental - WORK IN PROGRESS**

_This documentation is based upon the INA236 and INA228 library, 
and may contain information not updated yet.
Please open an issue if needed._

Experimental library for the INA2227 current and power sensor.  

Read datasheet for details.

==> **USE WITH CARE**

The INA2227 is a voltage, current and power measurement device. 
A few important maxima, see datasheet, chapter 6.

|  description  |  max  |  unit  |  notes  |
|:--------------|------:|-------:|:--------|
| bus voltage   |  48   | Volt   |  unclear for how long.
| shunt voltage |  80   | mVolt  |  can be set to 20 mV.
| current       |  20   | Ampere |  ?? TODO check

Feedback as always is welcome.


### Special characters

- Ω == Ohm = ALT-234 (Windows)
- µ == micro = ALT-0181 (Windows)


### Related



## I2C

### Address


### Performance

To be elaborated, example sketch needed + HW


### I2C multiplexing

Sometimes you need to control more devices than possible with the default
address range the device provides.
This is possible with an I2C multiplexer e.g. TCA9548 which creates up
to eight channels (think of it as I2C subnets) which can use the complete
address range of the device.

Drawback of using a multiplexer is that it takes more administration in
your code e.g. which device is on which channel.
This will slow down the access, which must be taken into account when
deciding which devices are on which channel.
Also note that switching between channels will slow down other devices
too if they are behind the multiplexer.

- https://github.com/RobTillaart/TCA9548


## About Measurements


## Interface

```cpp
#include "INA2227.h"
```

### Constructor

- **INA2227(const uint8_t address, TwoWire \*wire = Wire)** Constructor to set 
the address and optional Wire interface.
- **bool begin()** initializes the class.
returns true if the INA2227 address is on the I2C bus.
Note: one needs to set **Wire.begin()** before calling **begin()**.
- **bool isConnected()** returns true if the INA2227 address is on the I2C bus.
- **uint8_t getAddress()** returns the address set in the constructor.

### Bus voltage


### Shunt voltage


### Shunt current


### Power


### Energy


### Conversion Ready


### ADC conversion time



|  enum description   | BVCT SVCT |   time    |  notes  |
|:-------------------:|:---------:|:---------:|--------:|
|  INA2227_140_us     |     0     |  140 us   |
|  INA2227_204_us     |     1     |  204 us   |
|  INA2227_332_us     |     2     |  332 us   |
|  INA2227_588_us     |     3     |  588 us   |
|  INA2227_1100_us    |     4     |  1.1 ms   |  default
|  INA2227_2100_us    |     5     |  2.1 ms   |
|  INA2227_4200_us    |     6     |  4.2 ms   |
|  INA2227_8300_us    |     7     |  8.3 ms   |



|  enum description     | value | # samples |  notes  |
|:---------------------:|:-----:|----------:|--------:|
|  INA2227_1_SAMPLE     |   0   |      1    |  default
|  INA2227_4_SAMPLES    |   1   |      4    |
|  INA2227_16_SAMPLES   |   2   |     16    |
|  INA2227_64_SAMPLES   |   3   |     64    |
|  INA2227_128_SAMPLES  |   4   |    128    |
|  INA2227_256_SAMPLES  |   5   |    256    |
|  INA2227_512_SAMPLES  |   6   |    512    |
|  INA2227_1024_SAMPLES |   7   |   1024    |




### ADCRange


### Calibration

See datasheet.

### About normalization


### Error codes setMaxCurrentShunt

|  descriptive name error        |  value   |  meaning  |
|:-------------------------------|:--------:|:----------|
|  INA2227_ERR_NONE               |  0x0000  |  OK
|  INA2227_ERR_SHUNTVOLTAGE_HIGH  |  0x8000  |  maxCurrent \* shunt > 80 mV 
|  INA2227_ERR_MAXCURRENT_LOW     |  0x8001  |  maxCurrent < 0.001
|  INA2227_ERR_SHUNT_LOW          |  0x8002  |  shunt      < 0.001
|  INA2227_ERR_NORMALIZE_FAILED   |  0x8003  |  not possible to normalize.

TODO Complete?

### Operating mode

See datasheet, not tested.


### Alert functions

See datasheet, not tested.


### Alert Limits

See datasheet, not tested.


### Meta information

- **uint16_t getManufacturerID()** should return 0x5449
- **uint16_t getDieID()** should return 0xA080.


### Error Handling

- **int getLastError()** returns last (I2C) error.



## Future


#### Must

- keep in sync with INA226 where possible.

#### Should

#### Could

#### Won't


## Support

If you appreciate my libraries, you can support the development and maintenance.
Improve the quality of the libraries by providing issues and Pull Requests, or
donate through PayPal or GitHub sponsors.

Thank you,

