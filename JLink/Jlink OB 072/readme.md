# J-Link OB（STM32F072）

**中文** | [English](./readme_en.md)

基于 STM32F072 的 J-Link OB 自制调试器。

## 规格

| 项目 | 详情 |
|------|------|
| **MCU** | STM32F072 |
| **接口** | SWD + VCP (虚拟串口) |

## 资料清单

| 文件 | 说明 |
|------|------|
| [JlinkOB_PCB_Project/](<./JlinkOB_PCB_Project/readme.md>) | Altium Designer 工程 |
| `JlinkOB_PCB_Project/Sheet.SchDoc` | 原理图 |
| `JlinkOB_PCB_Project/PCB.7z` | PCB 文件压缩包（PCB 请自己设计） |
| `JlinkOB_PCB_Project/jlink-ob-com/bin_8000000.bin` | 固件（基址 0x08000000） |
| `JlinkOB_PCB_Project/jlink-ob-com/Jlink_OB_072/` | OB 072 固件与提取的固件片段 |
| `JlinkOB_PCB_Project/jlink-ob-com/` | Windows 固件操作工具（解包内容，含 JLinkARM.dll） |

## PCB 效果图

见 [JlinkOB_PCB_Project/](<./JlinkOB_PCB_Project/readme.md>)：

![](<./JlinkOB_PCB_Project/top.png>)

![](<./JlinkOB_PCB_Project/bottom.png>)
