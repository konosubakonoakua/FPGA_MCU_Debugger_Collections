# ST-LINK V2/V2-1 to J-Link OB Conversion

[中文](./readme.md) | **English**

Flash J-Link OB firmware onto ST-LINK V2 hardware.

## Specifications

| Item | Details |
|------|---------|
| **Hardware** | ST-LINK V2 (STM32F103-based) |
| **Goal** | Reflash with J-Link OB firmware; device enumerates as J-Link OB |
| **Reference design** | [MB1180.pdf](./MB1180.pdf) (ST's official Nucleo on-board ST-LINK reference design) |

## File manifest

| File | Description |
|------|-------------|
| [MB1180.pdf](./MB1180.pdf) | ST official reference schematic |
| `STLinkV2.J28.M18.bin` | ST-LINK firmware backup |
| `STLinkReflash_170807.7z` | SEGGER reflash tool (extract, then run `STLinkReflash.exe`) |

## Steps

1. Get an ST-LINK V2 board
2. Extract `STLinkReflash_170807.7z` and run `STLinkReflash.exe` to flash the firmware
3. Done — the device now enumerates as a J-Link OB

> Detailed tutorial: [ST MCU forum thread](http://www.stmcu.org/module/forum/forum.php?mod=viewthread&tid=616941&page=1&extra=#pid2365746) (Chinese)

## Process screenshots

| Screenshot | Description |
|------------|-------------|
| [插上电脑(无固件).png](<./插上电脑(无固件).png>) | Plugged in without firmware |
| [刚刷入固件.png](./刚刷入固件.png) | Firmware just flashed |
| [升级过程.png](./升级过程.png) | Upgrade in progress |
| [固件升级失败，flash不够.png](<./固件升级失败，flash不够.png>) | Upgrade failed: not enough flash (64KB chip) |
| [固件升级居然成功了.png](./固件升级居然成功了.png) | Upgrade succeeded |
| [升级成功的c8t6有虚拟串口了.png](./升级成功的c8t6有虚拟串口了.png) | Virtual COM port appears after upgrade |
| [103成功变身jlinkob.png](./103成功变身jlinkob.png) | F103 successfully became a J-Link OB |
| [jlinkstlink下载成功.png](./jlinkstlink下载成功.png) | Download success |
| [keil_jlinkob_警告.png](./keil_jlinkob_警告.png) | J-Link OB warning in Keil |
| [识别成不同的东西.png](./识别成不同的东西.png) | Enumerates as different devices with different firmware |
