# J-Link V9 Mini（JLinkMini）

**中文** | [English](./readme_en.md)

> 开源项目：[shuanghanbitian/JLinkMini](https://github.com/shuanghanbitian/JLinkMini)（本目录 `HuhxOpensource.zip` 为其资料包）

基于 AD24 设计的 J-Link V9 编程器，硬件尺寸 20.7mm × 12.95mm，结构紧凑。该版本聚焦于评估外围器件的最简化架构，输出接口为 SWD + 虚拟串口复合设计，并集成 GH1.25-7P 接插件，适用于 STM32 程序烧录与调试场景，部分 Cortex-M 核或 A 核的嵌入式芯片（需兼容输出电平）也适用。

![](https://github.com/shuanghanbitian/JLinkMini/raw/main/Images/3.png)

## 硬件规格

- **物理尺寸**：20.7mm × 12.95mm
- **核心接口**：SWD 调试接口 + UART 虚拟串口（GH1.25-7P 卧式连接器）
- **USB 接口类型**：Type-C
- **主要芯片**：STM32F205RET6（STM32F205RCT6 兼容）
- **PCB 层数**：四层板

## 电气特性

- **输入电压**：5.0V
- **最大工作电流**：500mA
- **接口电平**：3.3V TTL

## 接口定义

| 引脚号 | 信号定义 | 说明 |
| :----- | :------- | :----------- |
| 1 | SWDIO | SWD 数据线 |
| 2 | SWCLK | CLK 时钟线 |
| 3 | GND | 电源地 |
| 4 | 3V3 | 3.3V 电源 |
| 5 | TX | 串口发送 |
| 6 | RX | 串口接收 |
| 7 | RST | 硬件复位信号 |

## 设计说明

- 本版本设计目的为外围器件最少化及快速验证，因此未加入防反接、ESD 保护、缓冲器及运放电路
- 信号完整性未做深入优化，但第二层设有完整地平面，实测可通过 CubeIDE 实现 12M 全速稳定下载
- USB 走线未做阻抗匹配与等长，因走线较短、频率较低，经验上可满足常规使用
- 贴片阻容为 0402M 加长引脚封装，一定程度上支持手工焊接

## 打样及焊接指南

- 推荐使用 1.0mm 板厚
- 推荐制作锡膏钢网进行焊接
- 焊接完成后请进行以下检查：
  - 3.3V 对地、5V 对地短路检查
  - 器件是否虚焊

## 烧录与配置指南

- Bootloader 烧录建议通过 4Pin 的 2.54mm 测试夹完成，测试点间距即为 2.54mm
- 4Pin 烧录口位于 GH1.25-7P 接口下方，请务必按顺序完成以下操作：
  1. 烧录 bootloader
  2. 通过 J-Link Commander 升级固件
  3. 运行设置 SN 码等命令
  4. 最后再焊接 GH1.25 插座
- 如通过测试点飞线烧录，完成后须用吸锡带清除焊锡残留，防止与插座发生机械干涉

## 部分图片展示

> 图片位于上游仓库及 `HuhxOpensource.zip` 资料包内。

- 样机大致尺寸
  ![image](https://github.com/shuanghanbitian/JLinkMini/raw/main/Images/1.JPG)
- PCB 正面焊接
  ![image](https://github.com/shuanghanbitian/JLinkMini/raw/main/Images/2.JPG)
- PCB 正反面展示
  ![image](https://github.com/shuanghanbitian/JLinkMini/raw/main/Images/3.png)

## 附件描述（`HuhxOpensource.zip`）

- 【Docs】详细烧录步骤文档
- 【Firmware】bootloader 固件
- 【Hardware】Altium Designer 源文件、gerber 打样文件、坐标文件、BOM 表
- 【Tools】.exe 软件
- 【Images】样机图片
