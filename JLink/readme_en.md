# J-Link Series

[中文](./readme.md) | **English**

Collection of DIY J-Link debuggers: V9, V9 Mini, isolated version, OB variants, and ST-LINK hardware conversion.

## Subprojects

| Subproject | MCU | Description | Status |
|------------|-----|-------------|--------|
| [JlinkV9](<./JlinkV9/readme_en.md>) | NXP LPC4322 | J-Link V9 (SWD+JTAG+VCP), multiple USB connector variants | ✅ Complete |
| [JlinkV9 mini](<./JlinkV9 mini/readme_en.md>) | STM32F205RET6 | Ultra-compact 20.7×12.95mm V9, board-verified | ✅ Complete |
| [JlinkV9 isoloated](<./JlinkV9 isoloated/readme_en.md>) | — | Isolated V9 base board (oshwhub open source) | 🔗 Links+firmware |
| [Jlink OB 072](<./Jlink OB 072/readme_en.md>) | STM32F072 | J-Link OB (SWD+VCP) | ✅ Complete |
| [J-Link OB-STM32F103 V1](<./J-Link OB-STM32F103 V1/readme_en.md>) | STM32F103C8T6 | J-Link OB (SWD), 2012 v7 version stable | ✅ Complete |
| [JLink converted to STLINK V2 V2-1](<./JLink converted to STLINK V2 V2-1/readme_en.md>) | STM32F103 | Flash J-Link OB firmware onto ST-LINK V2 hardware | ✅ Complete |

## Common activation (V9 series)

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

> Replace `XXXXXXXX` with your serial number.
