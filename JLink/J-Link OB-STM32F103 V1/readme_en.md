# J-Link OB (STM32F103 V1)

[中文](./readme.md) | **English**

DIY J-Link OB debugger based on the STM32F103C8T6.

## Specifications

| Item | Details |
|------|---------|
| **MCU** | STM32F103C8T6 (Cortex-M3) |
| **Interfaces** | SWD |

## File manifest

| File | Description |
|------|-------------|
| [2012版本(v7版)/Schematic_temp_ARM-OB_20180808014643.pdf](<./2012版本(v7版)/Schematic_temp_ARM-OB_20180808014643.pdf>) | Schematic |
| `2012版本(v7版)/jlinkv7_pcb/jlink.PcbDoc` | PCB (Altium Designer), also archived as `jlinkv7_pcb.7z` |
| `2012版本(v7版)/J-Link ARM-OB STM32 compiled Aug 22 2012.bin` | v7 firmware |
| `2012版本(v7版)/jlink_ob_c8t6.hex` | HEX firmware |

## ⚠️ Versions

| Version (folder) | Status |
|------------------|--------|
| `2012版本(v7版)` (2012, v7) | ✅ Stable, usable |
| `2017版本有问题,JFlash不能用` (2017, broken) | ❌ J-Flash does not work, **not recommended** |

## Photos

PCB top/bottom:

![](top.png)

![](bottom.png)

Recognized in Keil:

![](keil成功识别.png)

Upgrade screenshot: [2012版本(v7版)/升级截图53.png](<./2012版本(v7版)/升级截图53.png>); note this version [occasionally pops a warning](<./2012版本(v7版)/时不时会弹出警告.png>).
