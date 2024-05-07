---
title: ESP32C2产品系列
---



# 产品概述
ESP32C2系列 每一款具有超低功耗的 Wi-Fi +Bluetooth® 5 (LE) 系统级芯片。

ESP8684 系列是极低功耗、高集成度的 MCU 系统级芯片 (SoC)，集成 2.4 GHz Wi-Fi 和低功耗蓝牙 (Bluetooth®
LE) 无线通信，专为物联网 (IoT)、智能家居、工业自动化、医疗保健及消费电子产品等各种应用而设计，具有行
业领先的低功耗性能和射频性能。
ESP8684 系列搭载 RISC-V 32 位单核处理器，工作频率高达 120 MHz。芯片支持二次开发，无需使用其他微控
制器或处理器。
ESP8684 系列芯片是业内集成度领先的 Wi-Fi + Bluetooth 5 (LE) 解决方案，集成了完整的发射/接收射频功能，
包括天线开关、射频 balun、功率放大器、低噪声放大器、滤波器、电源管理模块和先进的自校准电路，极大减
少了印刷电路板 (PCB) 的面积。
ESP8684 系列芯片还集成了先进的自校准电路，实现了动态自动调整，可以消除外部电路的缺陷，更好地适应
外部环境的变化。因此，ESP8684 的批量生产不需要昂贵的专用 Wi-Fi 测试设备。

# 特性
## CPU 和片上存储器
- 内置 ESP8684H2 或 ESP8684H4 芯片，RISC-V32 位单核微处理器，主频最高 120 MHz
- 576 KB ROM
- 272 KB SRAM（其中 16 KB 专用于 cache）
- 封装内 flash（详见表 1 ESP8684-WROOM-01C系列型号对比）
- 引入 cache 机制的 flash 控制器
- 支持 flash 在电路编程 (ICP)

## Wi-Fi
- 802.11 b/g/n
- 工作信道中心频率范围：2412 ~ 2484 MHz
- 在 2.4 GHz 频带支持 20 MHz 频宽
- 支持 1T1R 模式，数据速率高达 72.2 Mbps
- 无线多媒体 (WMM)
- 帧聚合 (TX/RX A-MPDU, TX/RX A-MSDU)
- 立即块确认 (Immediate Block ACK)
- 分片和重组 (Fragmentation and defragmentation)
- 传输机会 (Transmit opportunity, TXOP)
- Beacon 自动监测（硬件 TSF）
- 3 × 虚拟 Wi-Fi 接口
- 同时支持基础结构型网络 (Infrastructure BSS)Station 模式、SoftAP 模式、Station + SoftAP 模式和混杂模式请注意 ESP8684 系列在 Station 模式下扫描时，SoftAP 信道会同时改变


## 蓝牙
- 低功耗蓝牙 (Bluetooth LE)：Bluetooth 5
- 高功率模式（20 dBm）
- 速率支持 125 kbps、500 kbps、1 Mbps、2 Mbps
- 广播扩展 (Advertising Extensions)
- 多广播 (Multiple Advertisement Sets)
- 信道选择 (Channel Selection Algorithm #2)
- Wi-Fi 与蓝牙共存，共用同一个天线

## 外设
- GPIO、SPI、UART、I2C、LED PWM 控制器、通用 DMA 控制器、温度传感器、SAR 模/数转换器、定时器和看门狗模组集成元件
- 26 MHz 集成晶振
## 天线选型
- 板载 PCB 天线 (ESP8684-WROOM-02C)
- 通过连接器连接外部天线 (ESP8684-WROOM02UC)
## 工作条件
- 工作电压/供电电压：3.0 ~ 3.6 V
- 工作环境温度：–40 ~ 85 °C


# 具体模组

|     系列模组       |     规格书     |
| ---------- | ---------------------: |
| ESP8684-MINI-1 | [点击查看](https://www.espressif.com/sites/default/files/documentation/esp8684-mini-1_mini-1u_datasheet_cn.pdf) |
| ESP8684-WROOM-01C | [点击查看](https://www.espressif.com/sites/default/files/documentation/esp8684-wroom-01c_datasheet_cn.pdf) |
| ESP8684-WROOM-02C | [点击查看](https://www.espressif.com/sites/default/files/documentation/esp8684-wroom-02c_datasheet_cn.pdf) |
| ESP8684-WROOM-03 | [点击查看](https://www.espressif.com/sites/default/files/documentation/esp8684-wroom-03_datasheet_cn.pdf) |
| ESP8684-WROOM-04C | [点击查看](https://www.espressif.com/sites/default/files/documentation/esp8684-wroom-05_datasheet_cn.pdf) |
| ESP8684-WROOM-05 | [点击查看](https://www.espressif.com/sites/default/files/documentation/esp8684-wroom-05_datasheet_cn.pdf) |
| ESP8684-WROOM-06C | [点击查看](https://www.espressif.com/sites/default/files/documentation/esp8684-wroom-06c_datasheet_cn.pdf) |
| ESP8684-WROOM-07 | [点击查看](https://www.espressif.com/sites/default/files/documentation/esp8684-wroom-07_datasheet_cn.pdf) |
