# ST-LINK V2/V2-1 转 J-Link OB

**中文** | [English](./readme_en.md)

将 ST-LINK V2 硬件刷写为 J-Link OB 固件。

## 规格

| 项目 | 详情 |
|------|------|
| **硬件** | ST-LINK V2（STM32F103 方案） |
| **目标** | 刷写为 J-Link OB 固件，识别为 J-Link OB |
| **参考设计** | [MB1180.pdf](./MB1180.pdf)（ST 官方 Nucleo 板载 ST-LINK 参考设计） |

## 资料清单

| 文件 | 说明 |
|------|------|
| [MB1180.pdf](./MB1180.pdf) | ST 官方参考设计原理图 |
| `STLinkV2.J28.M18.bin` | ST-LINK 固件备份 |
| `STLinkReflash_170807.7z` | SEGGER 刷写工具（解压后运行 `STLinkReflash.exe`） |

## 使用步骤

1. 准备一块 ST-LINK V2 硬件
2. 解压 `STLinkReflash_170807.7z`，运行 `STLinkReflash.exe` 刷写固件
3. 完成后设备识别为 J-Link OB

> 详细教程见 [ST MCU 论坛帖子](http://www.stmcu.org/module/forum/forum.php?mod=viewthread&tid=616941&page=1&extra=#pid2365746)

## 过程截图

| 截图 | 说明 |
|------|------|
| [插上电脑(无固件).png](<./插上电脑(无固件).png>) | 无固件时插上电脑 |
| [刚刷入固件.png](./刚刷入固件.png) | 刚刷入固件 |
| [升级过程.png](./升级过程.png) | 升级过程 |
| [固件升级失败，flash不够.png](<./固件升级失败，flash不够.png>) | 升级失败：Flash 不够（64KB 版芯片） |
| [固件升级居然成功了.png](./固件升级居然成功了.png) | 升级成功 |
| [升级成功的c8t6有虚拟串口了.png](./升级成功的c8t6有虚拟串口了.png) | 升级成功后出现虚拟串口 |
| [103成功变身jlinkob.png](./103成功变身jlinkob.png) | F103 成功变身 J-Link OB |
| [jlinkstlink下载成功.png](./jlinkstlink下载成功.png) | 下载成功 |
| [keil_jlinkob_警告.png](./keil_jlinkob_警告.png) | Keil 中的 J-Link OB 警告 |
| [识别成不同的东西.png](./识别成不同的东西.png) | 不同固件识别成不同设备 |
