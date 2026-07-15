# J-Link OB (STM32F072)

[中文](./readme.md) | **English**

DIY J-Link OB debugger based on the STM32F072.

## Specifications

| Item | Details |
|------|---------|
| **MCU** | STM32F072 |
| **Interfaces** | SWD + VCP (virtual COM port) |

## File manifest

| File | Description |
|------|-------------|
| [JlinkOB_PCB_Project/](<./JlinkOB_PCB_Project/readme_en.md>) | Altium Designer project |
| `JlinkOB_PCB_Project/Sheet.SchDoc` | Schematic |
| `JlinkOB_PCB_Project/PCB.7z` | PCB archive (design your own PCB) |
| `JlinkOB_PCB_Project/jlink-ob-com/bin_8000000.bin` | Firmware (base address 0x08000000) |
| `JlinkOB_PCB_Project/jlink-ob-com/Jlink_OB_072/` | OB 072 firmware and extracted firmware fragments |
| `JlinkOB_PCB_Project/jlink-ob-com/` | Windows firmware utility (unpacked contents, incl. JLinkARM.dll) |

## PCB renders

See [JlinkOB_PCB_Project/](<./JlinkOB_PCB_Project/readme_en.md>):

![](<./JlinkOB_PCB_Project/top.png>)

![](<./JlinkOB_PCB_Project/bottom.png>)
