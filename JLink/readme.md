# J-Link 系列

**中文** | [English](./readme_en.md)

自制 J-Link 调试器合集，涵盖 V9、V9 Mini、隔离版、OB 版本及 ST-LINK 硬件转刷方案。

## 子项目

| 子项目 | 主控 | 说明 | 状态 |
|--------|------|------|------|
| [JlinkV9](<./JlinkV9/readme.md>) | NXP LPC4322 | J-Link V9（SWD+JTAG+VCP），多 USB 接口版本 | ✅ 完整 |
| [JlinkV9 mini](<./JlinkV9 mini/readme.md>) | STM32F205RET6 | 20.7×12.95mm 超小型 V9，已打板验证 | ✅ 完整 |
| [JlinkV9 isoloated](<./JlinkV9 isoloated/readme.md>) | — | 隔离版 V9 底板（oshwhub 开源） | 🔗 链接+固件 |
| [Jlink OB 072](<./Jlink OB 072/readme.md>) | STM32F072 | J-Link OB（SWD+VCP） | ✅ 完整 |
| [J-Link OB-STM32F103 V1](<./J-Link OB-STM32F103 V1/readme.md>) | STM32F103C8T6 | J-Link OB（SWD），2012 v7 版稳定 | ✅ 完整 |
| [JLink converted to STLINK V2 V2-1](<./JLink converted to STLINK V2 V2-1/readme.md>) | STM32F103 | ST-LINK V2 硬件刷 J-Link OB 固件 | ✅ 完整 |

## 通用激活方法（V9 系列）

刷完固件后在 J-Link Commander 中执行：

```
Exec SetSN=XXXXXXXX
Exec AddFeature GDB
Exec AddFeature RDI
Exec AddFeature FlashBP
Exec AddFeature FlashDL
Exec AddFeature JFlash
Exec AddFeature RDDI
```

> 将 `XXXXXXXX` 替换为你的序列号。
