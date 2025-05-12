# Modbus

AIS AtoN Modbus

## Introduction

This doscument describe how to use Modbus RTU protocol to read the AMEC AtoN device status.
這份文件說明如何透過 Modbus RTU 協定來讀取 AMEC AtoN 的系統部分狀態。

## Modbus RTU slave

AtoN support read system status via Modbus proctol.
AtoN 支援透過 Modbus RTU 通訊協定來讀取設備部份資料。

### Communicate setting 通訊設定

Baudate(鮑率): 115200/38400/9600/4800 bps
Data bits(資料長度): 8 bits
Parity(同位校驗): None (無校驗)
Stop bit: 1 bit

### Modbus setting 設定

Unit Address: 1 ~ 247, default is 1
設備地址: 1 ~ 247，預設為 1

### Holding Registers 保持寄存器

AtoN device status are store int the Modbus holding registers.
Following data will be update every 5 seconds.
AtoN 的狀態資訊儲存在 Modbus 的保持寄存器內。
下列資訊，每五秒會更新一次。

| Address 位址 | Comment | 說明 |
| :--: | -- | -- |
| `0x00` | Reserved | 保留 |
| `0x01` | System voltage (milliVolt) | 系統電壓 (毫伏特)|
| `0x02` | Tx status ( 0: OK, 1: not good) | 發射機狀態(0:正常 1:異常) |
| `0x03` | Rx channel A status ( 0: OK, 1: not good) | 頻道A接收機狀態(0:正常 1:異常) |
| `0x04` | Rx channel B status ( 0: OK, 1: not good) | 頻道B接收機狀態(0:正常 1:異常) |

### Example 範例

Here is an example that AtoN device receive Modbus RUT request and response.
下面是 AtoN device 收到 Modbus RTU 請求以及回應的範例。

#### Modbus RTU requset 請求


```text
0x01 0x03 0x00 0x01 0x00 0x04 0xHH 0xHH
```

| Field nameq1 | Value (hex) | Comment |
| -- | -- | -- |
| Unit address 地址 | `0x01` | default unit address|
| Function code 功能碼 | `0x03` | read holding registers 讀取保持寄存器|
| Start address (Hi) 寄存器起始位址 | `0x00` | |
| Start address (Lo) 寄存器起始位址 | `0x01` | start from address 1 保持寄存器起始位址|
| Number of registers (Hi) 寄存器數量 | `0x00` |  |
| Number of registers (Lo) 寄存器數量 | `0x04` | read 4 data 讀取 4 組|
| Checksum Hi | `0xHH` | 檢查碼 
| checksum Lo | `0xHH` | 檢查碼 

#### Modbus RTU Response 回應

```text
0x01 0x03 0x08 0x2C 0xE4 0x00 0x00 0x00 0x00 0x00 0x00 0xHH 0xHH
```

| Field name | Value (hex) | Comment |
| -- | :--: | -- |
| Unit address 地址 | `0x01` | |
| Function code 功能碼 | `0x03`  |
| Byte count 位元組數量 | `0x08` | |
| Register value Hi (0x01) | `0x2C` |  |
| Register value Lo (0x01) | `0xE4` |  |
| Register value Hi (0x02) | `0x00` |  |
| Register value Lo (0x02) | `0x00` |  |
| Register value Hi (0x03) | `0x00` |  |
| Register value Lo (0x03) | `0x00` |  |
| Register value Hi (0x04) | `0x00` |  |
| Register value Lo (0x04) | `0x00` |  |
| Checksum Hi | `0xHH` | 檢查碼 
| checksum Lo | `0xHH` | 檢查碼 

| Field name | Value (hex) | Comment |
| -- | :--: | -- |
| Unit address 地址 | `0x01` | |
| Function code 功能碼 | `0x03` |  |
| Byte count 位元組數量 | `0x08` | |
| Register value (0x01) | `0x2C 0xE4` | 0x2CE4 = 11492, 11.492-mV |
| Register value (0x02) | `0x00 0x00` | 發射機狀態 正常 |
| Register value (0x03) | `0x00 0x00` | 頻道A接收機狀態 正常 |
| Register value (0x04) | `0x00 0x00` | 頻道B接收機狀態 正常 |
| Checksum | `0xHH 0xHH` | 檢查碼 |
