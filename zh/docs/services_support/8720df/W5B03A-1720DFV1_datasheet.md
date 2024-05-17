---
title: 飞腾云 W5B03A-1720DFV1 产品规格介绍
---
# W5B03A-1720DFV1 产品规格介绍


## 1 产品描述
W5B03A-1720DF-1624(以下简称：W5B03A)是一款基于Realtek高集成度的支持WLAN双频（2.4GHz和5GHz）和低功耗蓝牙5.0的芯片RTL8720DF的模组。芯片内置Real-M300（或KM4）高性能MCU（Armv8-M，与Cortex-M33指令集兼容），Real-M200（或KM0）低功耗MCU（Armv8-M，Cortex-M23指令集兼容）、WLAN（802.11a/b/g/n）MAC、支持1T1R的WLAN基带、射频、蓝牙。提供了一组可配置的 GPIO 口，用于不同外围设备的控制，同时集成了内部存储器，支持简单的应用程序开发，可实现完整的 Wi-Fi 和 BT 5.0 协议功能。

### 1.1 产品特性

- 内置低功耗 KM4 MCU，可以兼作应用处理器
- 主频支持 200MHz
- 工作电压：3.0V~3.6V
- 支持 802.11 a/b/g/n，2.4GHz 和 5GHz
- 支持 HT20/HT40 模式
- 支持 BLE5.0
- 支持低功率 Beacon 侦听模式
- WIFI/BT 共用天线
- 内置 AES/DES/FSHA 硬件引擎
- 支持 TrustZone-M 安全启动
- 支持 STA/AP/STA+AP 工作模式
- 工作温度：-20℃ to 85℃或-40℃ to 105℃（根据订购信息选择）


### 1.2 规格描述

| 项目 | 描述 |
| --- | --- |
| 产品名称 | W5B03A-1720DF |
| 产品描述 | Wi-Fi 2.4GHz/5GHz and BLE 5.0 双模双频模组 |
| 接口类型 | SMT 类型 |
| 环保说明 | 所有硬件部件完全符合欧盟 RoHS 指令 |

1.3 绝对电气参数

| 参数 | 描述 | 最小值 | 最大值 | 单位 |
| --- | --- | --- | --- | --- |
| Ts | 存储温度 | -40 | 125 | ℃ |
| VBAT | 供电电压 | 3.0 | 3.6 | V |
| 静电释放电压（人体模型） | TAMB -25℃ | -2 | 2 | KV |
| 静电释放电压（器件模型） | TAMB -25℃ | -500 | 500 | V |

1.4 正常工作条件

| 参数 | 描述  | 最小 |  标准 |  最大 |  单位 |
| --- | --- | --- | --- | --- | --- |
| Ta | 工作温度 | -20 | - | 85 | ℃ |
| Ta | 工作温度 | -40 | - | 105 | ℃ |
| VD33 | 供电电压 | 3.0 | 3.3 | 3.6 | V |
| V-OL | IO 输出低电压 | - | - | 0.4 | V |
| V-OH | IO 输出高电压 | 2.4 | - | - | V |
| V-IL | IO 输入低电压 | - | - | 0.8 | V |
| V-IH | IO 输入高电压 | 2.0 | - | - | V |
| I-IL | Input 漏电流 | -10 | ±1 | 10 | uA |

## 2 Pin 描述
### 2.1 Pin 定义图&Pin 定义

![](/assets/images/8720DF/8720df管脚.png)


| 序号  | Pin定义  | IO类型 | 功能              |
|------|---------|-------|-----------------|
| 1    | PB2     | I/O   | GPIOB_2/UART_RXD |
| 2    | PB1     | I/O   | GPIOB_1/UART_TXD |
| 3    | CHIP_EN | I     | High: Enable the chip. Low: Module power off. |
| 4    | PB3     | I/O   | GPIOB_3/SWD_CLK  |
| 5    | LOG_RXD | I/O   | GPIOA_8/UART_LOG_RXD |
| 6    | PA12    | I/O   | GPIOA_12/SPI_MOSI |
| 7    | PA13    | I/O   | GPIOA_13/SPI_MISO |
| 8    | VD33    | P     | Power Supply 3.3V |
| 9    | PA14    | I/O   | GPIOA_14/SPI_CLK/UART_RTS |
| 10   | PA15    | I/O   | GPIOA_15/SPI_CS/UART_CTS |
| 11   | PA26    | I/O   | GPIOA_26/HSDP    |
| 12   | PA25    | I/O   | GPIOA_25/HSDM    |
| 13   | PA27    | I/O   | GPIOA_27/SWD_DAT |
| 14   | PA28    | I/O   | GPIOA_28/RREF   |
| 15   | GND     | P     | GND             |
| 16   | PB20    | I/O   | GPIOB_20/SDIO_CMD |
| 17   | LOG_TXD | I/O   | GPIOA_7/UART_LOG_TXD |
| 18   | PB21    | I/O   | GPIOB_21/SDIO_CLK |
| 19   | PB22    | I/O   | GPIOB_22/SDIO_D0  |
| 20   | PB23    | I/O   | GPIOB_23/SDIO_D1  |
| 21   | PB18    | I/O   | GPIOB_18/SDIO_D2  |
| 22   | PB19    | I/O   | GPIOB_19/SDIO_D3  |



## 3 封装信息及生产指导
### 3.1 机械尺寸

PCB 尺寸大小：16±0.3mm (L)×24±0.3mm (W) ×0.8±0.1mm (H)。单位：mm

![](/assets/images/8720DF/8720df尺寸.png)


# 更多资料

[详细规格书请前往W5B03A-1720DFV1模组规格书下载页面](../../download/8720df/8720df_datasheet.md)