---
title: Phaten 飞腾云 matter WB02B-8684H2V1 模组规格书
---
# WB02B-8684H2V1 模组规格书

## 1、产品介绍
### 1.1 产品描述
WB02B-8684H2V1是⼀款低功耗嵌⼊式Wi-Fi4 and BLE5 IOT双模模组。它由⼀个⾼集成度的⽆线射频
芯⽚ESP8684和少量外围器件构成，⽀持STA/AP/STA+AP⼯作模式，并同时⽀持低功耗蓝⽛连接。
WB02B-8684H2V1内置运⾏速度最⾼可到120MHz的32-bit MCU，1T1R WLAN，272 KB SRAM及内置
2MB Flash和丰富的外设资源。
WB02B-8684H2V1是⼀个RTOS 平台，集成了所有Wi-Fi MAC以及TCP/IP协议的函数库。⽤⼾可以基于
这些开发满⾜⾃⼰需求的嵌⼊式Wi-Fi 产品。

### 1.2 产品特性

- 内置低功耗32-bit MCU，可以兼作应⽤处理器
- 主频⽀持120MHz
- ⼯作电压：3V to 3.6V
- Wi-Fi 连通性
    - IEEE 802.11 b/g/n
    - Channel 1-14 @ 2.4GHz(CH1-11 for US/CA, CH1-13 for EU/CN, CH1-14 for JP) 
    - ⽀持WEP/WPA/WPA2/WPA2 PSK(AES)和WPA3安全模式
    - ⽀持STA/AP/STA+AP⼯作模式
    - ⽀持蓝⽛, SmartConfig以及AP两种配⽹⽅式(包括Android和IOS设备)
- PCB板载天线
- ⼯作温度：-40℃ to 105℃
- 蓝⽛连通性
    - 低功耗蓝⽛BLE5
    - 完整的蓝⽛共存接⼝

### 1.3 规格描述

| 项目 | 描述 |
| --- | --- |
| 产品名称 | WB02B-8684H2V1 |
| 产品描述 | Wi-Fi4 and BLE5 IOT双模模组 |
| 封装类型 |  SMT邮票孔 |
| 环保说明 | 所有硬件部件完全符合欧盟RoHS指令 |


### 1.4 绝对电气参数

| 参数 | 描述 | 最⼩值 | 最⼤值 | 单位 |
| --- | --- | --- | --- | --- |
| Ts | 存储温度 | -40 | 150 | ℃ |
| VBAT | 供电电压 | -0.3 | 3.6 | V |
| 静电释放电压（⼈体模型） | TAMB -25℃ | -2 | 2 | KV |
| 静电释放电压（机器模型） | TAMB -25℃ | -500 | 500 | V |


### 1.5 正常工作条件

| 参数 | 描述 | 最⼩值 | 标准值 | 最⼤值 | 单位 |
| --- | --- | --- | --- | --- | --- |
| Ta | ⼯作温度 | -40 | - | 105 | ℃ |
| VBAT | ⼯作电压 | 3 | 3.3 | 3.6 | V |
| VOL | IO低电平输出 | - | 0.1×VDD1 | - | V |
| VOH | IO⾼电平输出 | 0.8×VDD1 | - | - | V |
| I | IO驱动电流 | - | 40 | - | mA |

<!-- ## 2、射频参数
### 2.1 Wi-Fi射频性能

Wi-Fi基本射频性能

| 产品特性 | 产品描述 |
| --- | --- |
| ⽆线标准 | IEEE 802.11 b/g/n |
| ⼯作频率 | 2.400 GHz ~ 2.4835 GHz (2.4 GHz ISM Band) |
| 调制⽅法 | DSSS,DBPSK, DQPSK, CCK and OFDM (BPSK/QPSK/16-QAM/ 64-QAM) |
| Wi-Fi通道 | Channel 1-14@2.4GHz(CH1-11 for US/CA, CH1-13 for EU/CN, CH1-14 for JP) |
| 天线类型 | PCB板载天线 |

Wi-Fi发射性能

| TX | 最⼩值 | 典型值 | 最⼤值模式 | 单位 |
| --- | --- | --- | --- | --- |
| 802.11b@1Mbps EVM≤-21dB | - | 21 | - | dBm |
| 802.11b@11Mbps EVM≤-21dB | - | 21 | - | dBm |
| 802.11g@54Mbps EVM≤-25dB | - | 19 | - | dBm |
| 802.11g@6Mbps EVM≤-5dB | - | 21 | - | dBm |
| 802.11n@HT20 MCS0 EVM≤-5dB | - | 20 | - | dBm |
| 频偏误差 | -12 | - | 12 | ppm |

Wi-F接收性能

| | RX | 典型值 | 单位 |
| --- | --- | --- |
| 802.11b@11Mbps PER≤10% | -90 | dBm |
| 802.11n@HT20 MCS7 PER≤10% | -74 | dBm |
| 802.11g@54Mbps PER≤10% | -77 | dBm |

### 2.2 蓝⽛技术指标

蓝⽛基本规格

| 产品特性 | 产品描述 |
|---------|---------|
| 蓝⽛规格 | BLE5    |
| ⼯作频率 | 2.402~2.480GHz |

蓝⽛发射性能

| TX | 最⼩值 | 典型值 | 最⼤值 | 单位 |
|----|-------|-------|-------|-----|
| 发射功率 | -24 | - | 21 | dBm |
| 连接速率 | - | 1 | - | Mbps |
| 连接速率 | - | 1 | - | Mbps |

蓝⽛接收性能

| RX | 典型值 | 单位 |
|----|--------|-----|
| 灵敏度 @ PER≤1% | ≤-85 | dBm | -->

<!-- ## 3、天线信息
### 3.1 天线类型

PCB板载天线

### 3.2 天线设计注意事项
 当Wi-Fi模组上使⽤PCB 板载天线时，为确保Wi-Fi 性能的最优化，建议模组天线部分和其他⾦属件距
离⾄少在15mm 以上。⽤⼾PCB 板在天线区域勿⾛线甚⾄覆铜，以免影响天线性能。

![](/assets/images/matter/板载天线.png) -->

## 2、管脚定义
### 2.1 管脚布局

![](/assets/images/matter/8684-05管脚.png)

### 2.2 管脚描述

| 序号 | 名称 | 类型 | 功能 |
| ---- | ---- | ---- | ---- |
| 1 | IO3 | I/O/T | GPIO3, ADC1_CH3, LED PWM |
| 2 | IO7 | I/O/T | GPIO7, FSPID, MTDO, LED PWM |
| 3 | IO6 | I/O/T | GPIO6, FSPICLK, MTCK, LED PWM |
| 4 | IO4 | I/O/T | GPIO4, ADC1_CH4, FSPIHD, MTMS, LED PWM |
| 5 | IO5 | I/O/T | GPIO5, FSPIWP, MTDI, LED PWM |
| 6 | GND | P | 接地 |
| 7 | 3V3 | P | 供电 |
| 8 | GND | P | 接地 |
| 9 | 3V3 | P | 供电 |
| 10 | RX | I/O/T | GPIO19, U0RXD |
| 11 | TX | I/O/T | GPIO20, U0TXD |
| 12 | IO9 | I/O/T | GPIO9 |
| 13 | EN | I | ⾼电平：芯⽚使能； 低电平：芯⽚关闭； 内部默认已上拉 |

## 3、模组尺⼨和 PCB 封装图形
### 3.1 模组尺⼨
PCB尺⼨：15±0.15(L)X17.3±0.15(W)X0.8±0.15(H)
![](/assets/images/matter/8684-05尺寸.png)

## 4、产品包装信息

托盘+外箱包装

## 更多资料

[详细规格书请前往ESP8684规格书下载页面](../../download/8720df/8720df_datasheet.md#esp8684)