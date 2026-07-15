# J-Link V9 Build Guide

[中文](./readme.md) | **English**

DIY J-Link V9 debugger based on the NXP LPC4322, with schematic, PCB projects, bootloader, firmware tools, and activation instructions.

## Specifications

| Item | Details |
|------|---------|
| **MCU** | NXP LPC4322 (Cortex-M4) |
| **Interfaces** | SWD + JTAG + VCP (virtual COM port) |
| **Highlights** | Upgradeable bootloader, multiple USB connector variants |

## File manifest

| File | Description |
|------|-------------|
| [制作资料/JlinkV93.pdf](<./制作资料/JlinkV93.pdf>) | Schematic |
| [制作资料/Jlinkv9mini_latest.pdf](<./制作资料/Jlinkv9mini_latest.pdf>) | V9 Mini schematic |
| `制作资料/jlinkv9mini_latest.7z` | V9 Mini PCB project (latest, board-verified) |
| `制作资料/jlinkv9_only_usbc.7z` | USB-C-only PCB project |
| `制作资料/jlinkv9_taobao_version.7z` | Taobao-version PCB project |
| `制作资料/bootloader.bin` | Bootloader firmware |
| `制作资料/bom.xls` | BOM |
| [制作资料/top asm.pdf](<./制作资料/top asm.pdf>), [btm asm.pdf](<./制作资料/btm asm.pdf>) | Assembly drawings (top/bottom) |
| `ひみつ/JLink_V9固件生成工具.rar` | Firmware generation tool |
| `ひみつ/jlink_v9固件升级资料.zip` | Firmware upgrade materials |
| [制作资料/jlink-v9激活.txt](<./制作资料/jlink-v9激活.txt>) | Activation commands (note: file is GBK-encoded) |

## Variants

- **Original**: multiple USB connectors + pin headers (micro-USB / mini-USB / USB-C)
- **USB-C-only**: single USB-C connector, more reliable under repeated plugging (`jlinkv9_only_usbc.7z`)
- **V9 Mini (latest)**: board-verified (`jlinkv9mini_latest.7z`); see also the standalone [JlinkV9 mini](<../JlinkV9 mini/readme_en.md>) project

## Renders & photos

![](./assets/3d.png)![](./assets/3d2.png)

The above are Altium renders; actual boards below:

![](./assets/shashinn2.jpg)

![](./assets/shashinn.jpg)

![](./assets/test1.png)

![](./assets/a.png)

![](./assets/mini.png)

![](./assets/micro.png)

![](./assets/typec.png)

Project files are inside the archives.

## Build steps

1. **Solder**: about half an hour by hand; a knife-tip iron is recommended (0402 with a fine tip will test your hand stability 🐶)
2. **Flash the bootloader**: flash `制作资料/bootloader.bin` via SWD
3. **Upgrade firmware**: automatic upgrade via J-Link Commander
4. **Activate**: add the S/N in J-Link Commander, then add licenses:

```
Exec SetSN=XXXXXXXX
Exec AddFeature GDB
Exec AddFeature RDI
Exec AddFeature FlashBP
Exec AddFeature FlashDL
Exec AddFeature JFlash
Exec AddFeature RDDI
```

> Replace `XXXXXXXX` with your serial number; see [制作资料/jlink-v9激活.txt](<./制作资料/jlink-v9激活.txt>)

5. 🎉 **Done**:

![](./assets/success1.png)

![](./assets/success2.png)

![](./assets/com.png)

## Revision notes

The earlier design combined multiple USB connectors + pin headers, which could develop contact issues after many plug cycles:

![1559136810152](./readme.assets/1559136810152.png)

So a USB-C-only revision was made — PCB file `jlinkv9_only_usbc.PcbDoc` (JLCPCB matte black, free of charge 🐂🍺):

![1559137003244](./readme.assets/1559137003244.png)
