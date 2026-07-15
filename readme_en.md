# FPGA / MCU Debugger Collections

[中文](./readme.md) | **English**

Collection of hardware design files (schematics, PCB), firmware, and build tutorials for DIY FPGA / MCU debuggers, logic analyzers, and wireless serial tools.

[![GitHub issues](https://img.shields.io/github/issues/konosubakonoakua/FPGA_MCU_Debugger_Collections)](https://github.com/konosubakonoakua/FPGA_MCU_Debugger_Collections/issues)

**Note: this project is for educational and research purposes only.**

---

## Table of Contents

- [Category Overview](#category-overview)
- [Repository Structure](#repository-structure)
- [Work in Progress](#work-in-progress)
- [General Build Guide](#general-build-guide)
- [Required Tools](#required-tools)
- [Notes](#notes)
- [Contributing](#contributing)
- [Related Links](#related-links)

---

## Category Overview

| Category | Description | Subprojects | Status |
|----------|-------------|-------------|--------|
| [JLink](<./JLink/readme_en.md>) | DIY J-Link series | V9 / V9 Mini / isolated / OB 072 / OB F103 / ST-LINK conversion | ✅ Complete |
| [STLink](<./STLink/readme_en.md>) | ST-LINK mods & DIY | V2-1 mod / V3 / V3 Mini | ✅ V2-1 complete, V3 🚧 |
| [DAPLink](<./DAPLink/readme_en.md>) | CMSIS-DAP series | Wired (STM32F103/CH552/ESP32) + Wireless (ch32v208 recommended/ch32v307/esp32s3) | ✅ Complete |
| [BlackMagic](<./BlackMagic/readme_en.md>) | Black Magic Probe | Official + MioLink (RP2040) | 🔗 Links only |
| [JTAG-FTDI](<./JTAG-FTDI/readme_en.md>) | Xilinx FTDI JTAG | hw-ftdi-jtag-xilinx (submodule, FT2232HQ) | ✅ Complete |
| [Xilinx Virtual Cable (XVC)](<./Xilinx Virtual Cable (XVC)/readme_en.md>) | JTAG over network (XVC) | xvc-pico / jtag-remote-server | 🔗 Links only |
| [USBBlaster](<./USBBlaster/readme_en.md>) | Altera/Intel FPGA programmer | CH552Nano | 🔗 Links only |
| [MiniWiggler](<./MiniWiggler/readme_en.md>) | Infineon 3-in-1 programmer | DAP + JTAG + UART | ✅ Complete |
| [Logic Analyzer](<./Logic Analyzer/readme_en.md>) | Logic analyzers | CH32H417 / CY7C68013A / Rpi Pico | 🔗 Links only |
| [Serial Port Wireless](<./Serial Port Wireless/readme_en.md>) | Wireless serial port | CH570 | ✅ Complete |

---

## Repository Structure

```
FPGA_MCU_Debugger_Collections/
├── JLink/                              # DIY J-Link series
│   ├── JlinkV9/                        #   J-Link V9 (LPC4322)
│   ├── JlinkV9 mini/                   #   Ultra-compact V9 (STM32F205)
│   ├── JlinkV9 isoloated/              #   Isolated V9
│   ├── Jlink OB 072/                   #   J-Link OB (STM32F072)
│   ├── J-Link OB-STM32F103 V1/         #   J-Link OB (STM32F103C8T6)
│   └── JLink converted to STLINK V2 V2-1/  # J-Link OB on ST-LINK V2 hardware
├── STLink/                             # ST-LINK series
│   ├── STLINKV2-1/                     #   V2 modded to V2-1 (with st-decrypt tool)
│   └── STLINKV3/                       #   V3 (MB1367 reference design) + v3 mini
├── DAPLink/                            # CMSIS-DAP series
│   ├── wired/                          #   Wired: STM23F103x / CH552 / cmsis_dap_tcp_esp32
│   └── Wireless/                       #   Wireless: ch32v208 (recommended) / ch32v307 / esp32s3
├── BlackMagic/                         # Black Magic Probe (links)
├── JTAG-FTDI/
│   └── hw-ftdi-jtag-xilinx/            # Xilinx FTDI JTAG (Git submodule)
├── Xilinx Virtual Cable (XVC)/         # JTAG over network (links)
├── USBBlaster/                         # USB Blaster (CH552, links)
├── MiniWiggler/                        # Infineon 3-in-1 programmer
├── Logic Analyzer/                     # Logic analyzers: CH32H417 / CY7C68013A / Rpi Pico
├── Serial Port Wireless/               # Wireless serial: CH570
├── readme.md                           # Chinese version
└── readme_en.md                        # This file (English)
```

See each subfolder's readme for chip choices, file manifests, and build steps.

---

## Work in Progress

The following projects are incomplete — contributions welcome:

| Project | Status | Progress |
|---------|--------|----------|
| [ARM-Mbed DAPLink](<./DAPLink/wired/STM23F103x/readme_en.md>) | Incomplete | Schematic + PCB (Altium) uploaded, firmware pending |
| [BlackMagic Probe](<./BlackMagic/readme_en.md>) | Incomplete | Official project links only |
| [ST-LINK V3](<./STLink/STLINKV3/readme_en.md>) | Incomplete | MB1367 reference schematic uploaded, firmware pending |

---

## General Build Guide

### Preparation

1. Order PCBs for your chosen project (JLCPCB recommended)
2. Solder all components
3. Have a working SWD programmer ready (ST-LINK / J-Link / DAP-Link)

### Flash the Bootloader

1. Connect the programmer to the target board via SWD
2. Erase the chip with the appropriate tool:
   - STM32CubeProgrammer / ST-LINK Utility
   - J-Flash
   - OpenOCD
3. Flash the bootloader to the chip's base address

### Flash the Firmware

Methods differ per debugger (see each subfolder readme):

- **J-Link V9**: automatic upgrade via J-Link Commander → [JLink/JlinkV9](<./JLink/JlinkV9/readme_en.md>)
- **ST-LINK V2-1**: automatic upgrade via ST-LINK Utility → Firmware Update → [STLink/STLINKV2-1](<./STLink/STLINKV2-1/readme_en.md>)
- **CMSIS-DAP**: directly flash the firmware built from the Keil project → [DAPLink/wired/STM23F103x](<./DAPLink/wired/STM23F103x/readme_en.md>)

### Activation (J-Link V9 only)

After flashing the firmware, run in J-Link Commander:

```
Exec SetSN=XXXXXXXX
Exec AddFeature GDB
Exec AddFeature RDI
Exec AddFeature FlashBP
Exec AddFeature FlashDL
Exec AddFeature JFlash
Exec AddFeature RDDI
```

> Replace `XXXXXXXX` with your serial number

---

## Required Tools

### Hardware

- SWD programmer (any working debugger)
- Soldering iron + solder (hand soldering; a knife-tip iron is recommended)
- Multimeter (for troubleshooting solder joints)

### Software

| Tool | Purpose |
|------|---------|
| [J-Link Commander](https://www.segger.com/downloads/jlink/) | J-Link V9 activation, firmware upgrade |
| [ST-LINK Utility / STM32CubeProgrammer](https://www.st.com) | ST-LINK firmware flashing |
| [Altium Designer / KiCad](https://www.kicad.org) | View/edit PCB projects |
| [Keil MDK](https://www.keil.com) | Build CMSIS-DAP source |
| [MounRiver Studio](http://www.mounriver.com/) | Build CH32-series source (wireless DAPLink, CH570, etc.) |
| [FT_Prog](https://ftdichip.com/utilities/) | FTDI chip configuration (MiniWiggler, FTDI JTAG) |
| [Sigrok PulseView](https://sigrok.org/wiki/PulseView) | Logic analyzer host software |
| [OpenOCD](https://openocd.org) | General debugger toolchain |

---

## Notes

### Safety & Legal Disclaimer

> **Warning: this project is for educational and research purposes only.**
>
> This repository only provides hardware reference designs and build methods. Firmware files are extracted from or generated by each debugger's official tools (J-Link, ST-LINK, etc.).
>
> - Segger J-Link is a registered trademark of [SEGGER Microcontroller GmbH](https://www.segger.com)
> - ST-LINK is a registered trademark of [STMicroelectronics](https://www.st.com)
> - ARM and CMSIS are registered trademarks of [Arm Limited](https://www.arm.com)
>
> Debuggers built from this project may violate the original vendors' license agreements. Use within legal bounds.

### Other Notes

- The STM32F103C8T6 comes in 64KB and 128KB flash variants; some firmware may require the 128KB variant
- Soldering 0402 components takes some experience; a knife-tip iron is recommended
- If the device is not recognized, check soldering and power first, then the SWD connection

---

## Contributing

Issues and pull requests welcome.

- Found a bug or problem → file an [Issue](https://github.com/konosubakonoakua/FPGA_MCU_Debugger_Collections/issues)
- Want to complete an unfinished project → contact the author or submit a PR

---

## Related Links

- [J-Link official](https://www.segger.com)
- [ST-LINK official](https://www.st.com)
- [CMSIS-DAP specification](https://arm-software.github.io/CMSIS_5/DAP/html/index.html)
- [DAPLink official](https://github.com/ARMmbed/DAPLink)
- [BlackMagic Probe official](https://black-magic.org)
- [OpenOCD](https://openocd.org)
- [WCH](https://www.wch.cn)
- [Sigrok](https://sigrok.org)
