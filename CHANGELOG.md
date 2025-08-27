# Changelog

### [3.6](https://github.com/leslieyang-amec/N323/releases/tag/v3.6) - 2025-08-20

#### Fixed

修正：

AIS message transmission power is lower than the configured setting.
AIS 訊息發射功率低於設定值。

After exiting power saving mode, the RATDMA access scheme does not resume operation.
系統離開省電模式後，RATDMA 無法恢復運行。

Writing data into flash memory may fail.
寫入 Flash 記憶體的操作可能失敗。

The AIS slot number is incorrect.
AIS slot 數值錯誤。

- Some output sentences are missing the appended TAG Block.
輸出 GNSS 模組資料時，未附加 TAG Block 資訊。

- NMEA 0183 encapsulation data contains an extra byte.
產生 NMEA 0183 encapsulation 資料時，多增加一個 byte。

- AIS Message 12 is transmitted unexpectedly at system startup.
系統開機時，會誤發送一筆 AIS Message 12。

- AIS Message 6/8/12/14 is transmitted with incorrect text length.
AIS Message 6/8/12/14 訊息內容長度與輸入不一致。

- AIS message payload includes an extra byte.
輸出 NMEA VDO/VDM encapsulation 資料時，長度不正確。

- AIS Message 25 destination flag does not match the NMEA 0183 MEB content.
AIS Message 25 Destination flag 與 NMEA 0183 MEB 內容不一致。

- AIS Message 6/8 DAC and FI field values are incorrect.
AIS Message 6/8/25/26 DAC 與 FI 欄位值與 NMEA 0183 ABM/BBM/MEB 內容不一致。

- LED behavior is incorrect.
LED 出現混色顯示，而非單色。

- Incorrect default value of UTC time.
UTC Time 預設值應為 00:00:00，而非隨機值。

- Virtual and synthetic stations’ “position accuracy” should always be set to “High”.
Virtual 與 Synthetic stations 的 position accuracy 預設應為 High。

- NMEA 0183 GNSS data stops outputting after system restart.
系統重新啟動後，GNSS 模組資料未輸出。

- RATDMA does not reset after Tx timeout or abort, preventing further transmissions.
當發射時間發生 timeout 或 abort 時，RATDMA 狀態未重置，導致後續無法正常發射。

- Fine-tuned the default VSWR threshold value.
修正 VSWR 門檻值的預設設定。

#### Changed
修改：

- Disabled output of certain NMEA 0183 GNSS sentences (GBS, VGT, and ZDA).
停止輸出部分 GNSS NMEA 0183 資料 (GBS, VGT, ZDA)。

- Default GNSS module dynamic platform model set to “sea”.
GNSS 模組 dynamic platform model 預設為 sea。

- NMEA 0183 ALR acknowledge state field default value changed to “V” (unacknowledged).
NMEA 0183 ALR 中 acknowledge state 欄位預設值由 “A” (acknowledged) 修改為 “V” (unacknowledged)。

#### Added
新增：

- For Type 1 AtoN, support transmitting NMEA 0183 ABM/BBM data using Message ID 0 with Message ID Index 0 scheduling.
AtoN Type 1 支援透過訊息 (0, 0) 排程發送 NMEA 0183 ABM/BBM 資料。

- Implemented redundant feature.
實作備援 (redundant) 機制。

- G-sensor feature: When the detected G value exceeds the threshold, the system triggers the transmission of AIS Message 12/14.
當 G-sensor 偵測值超過門檻時，系統觸發發送 AIS Message 12/14。

- Added support for NMEA 0183 MDA and WMV formatters.
支援 NMEA 0183 MDA、WMV 格式。

- Added support for transmitting AIS Message 8 (Meteorological and Hydrographic message).
支援發送 AIS Message 8 (水文氣象訊息)。

### [3.5.1] - 2024-08-16

### Added

- Support NMEA 0183 MDA,WMV, formatter.
- Transmit AIS message 8, Meteorological and Hydrographic message.

## Reference

All notable changes to this project will be documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
