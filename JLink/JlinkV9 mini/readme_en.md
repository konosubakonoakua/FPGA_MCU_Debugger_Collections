# J-Link V9 Mini (JLinkMini)

[中文](./readme.md) | **English**

> Open-source project: [shuanghanbitian/JLinkMini](https://github.com/shuanghanbitian/JLinkMini) (the `HuhxOpensource.zip` in this folder is its resource pack)

J-Link V9 programmer designed in AD24, measuring a compact 20.7mm × 12.95mm. This version focuses on a minimal peripheral architecture for evaluation; the output is a combined SWD + virtual COM port design with an integrated GH1.25-7P connector. Intended for STM32 flashing and debugging; also usable with some Cortex-M or Cortex-A embedded chips (voltage levels must be compatible).

![](https://github.com/shuanghanbitian/JLinkMini/raw/main/Images/3.png)

## Hardware specifications

- **Dimensions**: 20.7mm × 12.95mm
- **Core interfaces**: SWD debug + UART virtual COM port (GH1.25-7P right-angle connector)
- **USB connector**: Type-C
- **Main chip**: STM32F205RET6 (STM32F205RCT6 compatible)
- **PCB stack-up**: 4-layer

## Electrical characteristics

- **Input voltage**: 5.0V
- **Max operating current**: 500mA
- **I/O level**: 3.3V TTL

## Pinout

| Pin | Signal | Description |
| :-- | :----- | :---------- |
| 1 | SWDIO | SWD data |
| 2 | SWCLK | SWD clock |
| 3 | GND | Ground |
| 4 | 3V3 | 3.3V supply |
| 5 | TX | UART transmit |
| 6 | RX | UART receive |
| 7 | RST | Hardware reset |

## Design notes

- This version targets minimal peripherals and fast validation — no reverse-polarity protection, ESD protection, buffers, or op-amp circuits
- Signal integrity not deeply optimized, but layer 2 is a solid ground plane; verified stable 12M full-speed download via CubeIDE
- USB traces not impedance-matched or length-tuned; short traces and low frequency make this fine for normal use in practice
- Passives use 0402M extended-lead packages, reasonably hand-solderable

## Fabrication & soldering guide

- 1.0mm board thickness recommended
- Solder-paste stencil recommended
- After soldering, check:
  - 3.3V-to-GND and 5V-to-GND shorts
  - Cold/insufficient solder joints

## Flashing & configuration guide

- Flash the bootloader via a 4-pin 2.54mm test clip; test point pitch is 2.54mm
- The 4-pin flashing port sits under the GH1.25-7P connector — follow this order strictly:
  1. Flash the bootloader
  2. Upgrade the firmware via J-Link Commander
  3. Run the SN-setting commands, etc.
  4. Only then solder the GH1.25 socket
- If you flash via flying wires on the test points, clean solder residue with desoldering braid afterwards to avoid mechanical interference with the socket

## Photos

> Images live in the upstream repository and inside the `HuhxOpensource.zip` pack.

- Prototype size
  ![image](https://github.com/shuanghanbitian/JLinkMini/raw/main/Images/1.JPG)
- PCB top side soldered
  ![image](https://github.com/shuanghanbitian/JLinkMini/raw/main/Images/2.JPG)
- PCB both sides
  ![image](https://github.com/shuanghanbitian/JLinkMini/raw/main/Images/3.png)

## Attachments (`HuhxOpensource.zip`)

- [Docs] Detailed flashing walkthrough
- [Firmware] Bootloader firmware
- [Hardware] Altium Designer sources, gerbers, pick-and-place files, BOM
- [Tools] .exe utilities
- [Images] Prototype photos
