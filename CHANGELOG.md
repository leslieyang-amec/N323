# Changelog

## [3.6-T10](https://github.com/leslieyang-amec/N323/releases/tag/v3.6-T10) - 2025-08-07

### Fixed
- ***The AIS message transmission power may be lower than the setting.***

### Changed

- The method of calculating the next transmission time of the RATDMA message scheduling.
- Fine-tune the default VSWR threshold value.

## [3.6-T9](https://github.com/leslieyang-amec/N323/releases/tag/v3.6-T9) - 2025-08-04

### Changed

- Disable output of some NMEA 0183 GNSS data (GBS, VGT, and ZDA).
- Default GNSS module operation mode at sea level.
- For Type 1 AtoN, use Message ID 0 with Message ID Index 0 message schedule to transmit NMEA 0183 ABB/BBM data.

## [3.6-T8](https://github.com/leslieyang-amec/N323/releases/tag/v3.6-T8) - 2025-07-15

### Fixed

- The slot number is incorrect.
- Some output sentences without the appended TagBlock.

## [3.6-T7](https://github.com/leslieyang-amec/N323/releases/tag/v3.6-T7) - 2025-06-25

### Changed

- Increase the timeout value of the AIS acknowledgement message from 4 to 6 seconds.
- Enhance GNSS module initial flow.

## [3.6-T6](https://github.com/leslieyang-amec/N323/releases/tag/v3.6-T6) - 2025-06-04

### Fixed

- NMEA 0183 encapsulation data with extra data.

### Changed

- Change GNSS module baud rate to increase stability.

## [v3.6-T5](https://github.com/leslieyang-amec/N323/releases/tag/v3.6-T5) - 2025-05-08

### Fixed

- Transmit the AIS message 12 after system startup.
- Transmit the AIS message 12/14 with incorrect text length.
- AIS message payload with an extra byte.

### Added

- Output of all AIS messages feature.

## [3.6-T4](https://github.com/leslieyang-amec/N323/releases/tag/v3.6-T4) - 2025-04-24

### Fixed

- AIS message 25 Destination flag does not match NMEA 0183 MEB content.
- AIS message 6/8 DAC and FI field with incorrect value.

### Changed

- NMEA 0183 ALR, alarm's acknowledge state field default value to 'V'.
- Enhance NMEA 0183 parser.

## [3.6-T3](https://github.com/leslieyang-amec/N323/releases/tag/v3.6-T3) - 2025-04-10

### Added

- Support NMEA 0183 XDR foramtter.
- Configure mapping between NMEA 0183 XDR transducer ID and AIS message 8 Met/Hydro.
- Add a check external SPI flash status. Output PAMC sentence if there is an error.
- The restart operation after deleting the real AtoN station
- Redundant setting
- Add support query GNSS antenna state via $PAMC,Q,USER,61108,,,*61 command,
device will output $PAMC,R,USER,61108,2569,2,GNSS antenna state; 2=Ok; 3=Short; 4=Open*08
- G sensor features

### Fixed

- Write the firmware version into internal flash with wrong data.
  Write the firmware version, the operation should be executed after generating the firmware version.
- LED incorrect behavior.
- UTC time initial value.
- Sequence ID of NMEA 0183 VDO, the value will increase when the total sentence number is one.
- Virtual and synthetic stations' "position accuracy" value should always be set as high,
- Check the AtoN synchronization status method.
- NMEA 0183 GNSS data stop output.
- When Tx time-out, RATDMA will not abort.

### Changed

- FATDMA/RATDMA schedule count increase to 80.
- RATDMA random set start slot method, if there are more than 10 messages that need to be transmitted in the current minute,
  the transmission will be one by one instead of random in a minute. 

### [3.5.1] - 2024-08-16

### Added

- Support NMEA 0183 MDA,WMV, formatter.
- Transmit AIS message 8, Meteorological and Hydrographic message.

## Reference

All notable changes to this project will be documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
