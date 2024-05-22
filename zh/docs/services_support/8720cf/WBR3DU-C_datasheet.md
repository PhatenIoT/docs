---
title:  WBR3DU-C 简介 
---
# WBR3DU-C 简介 

## 1 产品描述
WBR3DU-C是一款低功耗嵌入式 Wi-Fi+蓝牙模组。它由一个高集成度的无线射频芯片
RTL8720CF(W701H-VT2-CG)构成，内置了 Wi-Fi 网络协议栈和丰富的库函数。此产品还包含低功耗的 KM4
MCU，WLAN MAC，1T1R WLAN，最高主频 100MHz，内置 256K SRAM ，芯片内置 2Mbyte flash 和丰富的外
设资源。
WBR3DU-C是一个 RTOS平台，集成了所有 Wi-Fi MAC 以及 TCP/IP 协议的函数库。用户可以基于这些
开发满足自己需求的嵌入式 Wi-Fi 产品。

### 1.1 产品特性

- 内置低功耗 KM4 MCU，可以兼作应用处理器
- 主频支持 100MHz
- 工作电压：3.0V~3.6V
- Wi-Fi 蓝牙连通性
    - 802.11 b/g/n
    - 信道 1-14@2.4GHz (CH1-11 for US/CA, CH1-13 for EU/CN)
    - 支持 WEP,WPA/WPA2,WPA2 PSK (AES) 安全模式
    - 支持 Bluetooth 4.2 Low Energy
    - 支持 SmartConfig 和 AP 两种配网方式（包括 Android 和 IOS 设备）
    - 外接天线
    - 工作温度：-40℃ to 105℃


### 1.2 规格描述

| 项目 | 描述 |
|--------------|---------------------------|
| 产品名称      | WBR3DU-C                    |
| 产品描述      | Wi-Fi and BT 4.2 双模模组     |
| 产品尺寸      | L x W: 12±0.3 *15±0.3 mm  |
| 接口类型      | SMT 类型                   |
| 环保说明      | 所有硬件部件完全符合欧盟 RoHS 指令 |


### 1.3 绝对电气参数


| 参数             | 描述           | 最小值 | 最大值 | 单位 |
|-----------------|--------------|------|------|----|
| Ts              | 存储温度       | -40  | 125  | ℃  |
| VBAT            | 供电电压       | -0.3 | 3.6  | V  |
| 静电释放电压（人体模型） | TAMB -25℃ | -    | 2    | KV |
| 静电释放电压（机器模型） | TAMB -25℃ | -    | 0.5  | KV |


### 1.4 正常工作条件

| 参数   | 描述         | 最小 | 标准 | 最大 | 单位 |
|-------|------------|----|----|----|----|
| Ta    | 工作温度     | -40 | -  | 105 | ℃  |
| VBAT  | 供电电压     | 3.0 | 3.3 | 3.6 | V  |
| VIL   | IO 低电平输入 | -   | -   | 0.8 | V  |
| VIH   | IO 高电平输入 | 2.0 | -   | -   | V  |
| VOL   | IO 低电平输出 | -   | -   | 0.4 | V  |
| VOH   | IO 高电平输出 | 2.4 | -   | -   | V  |
| I IO  | 驱动电流     | -   | -   | 16  | mA |


## 2 Pin 描述
### 2.1 Pin 定义图&Pin 定义

![](/assets/images/8720CF/8720cf管脚.png)

| 序号  | Pin定义  | IO类型 | 功能              |
|------|---------|-------|-----------------|                                                
| 1  | GND    | P   | 电源参考地            |                                         
| 2  | VCC    | P   | 模组电源引脚（3.3V）   |                                              
| 3  | A19    | I/O | GPIOA_19，硬件 PWM，IC Pin40   |                                      
| 4  | A18    | I/O | GPIOA_18，硬件 PWM，IC Pin39    |                                   
| 5  | A17    | I/O | GPIOA_17，硬件 PWM，IC Pin38     |                                     
| 6  | A16    | I/O | GPIOA_16，UART_Log_TXD(用于打印模组内部信息)，可配置成普通 GPIO      |      
| 7  | A15    | I/O | GPIOA_15，UART_Log_RXD(用于打印模组内部信息)，可配置成普通 GPIO    |               
| 8  | A14/TX | I/O | GPIOA_14，UART0_TXD（用户串口）     |                                      
| 9  | A13/RX | I/O | GPIOA_13，UART0_RXD（用户串口）    |                              
| 10 | A12    | I/O | GPIOA_12，硬件 PWM，IC Pin26       |                                    
| 11 | A11    | I/O | GPIOA_11，硬件 PWM，IC Pin25       |                                   
| 12 | A7     | I/O | GPIOA_7，硬件 PWM，IC Pin21         |                                 
| 13 | A4     | I/O | GPIOA_4，硬件 PWM，IC Pin20         |                                  
| 14 | A3     | I/O | GPIOA_3，硬件 PWM，IC Pin19          |                                  
| 15 | A2     | I/O | GPIOA_2，硬件 PWM，IC Pin18          |                                 
| 16 | A0     | I/O | GPIOA_0                                |                                 
| 17 | EN     |     | 模组使能引脚，高电平有效，模组已上拉高电平，用户可外部控制该引脚    |                   


## 3 封装信息及生产指导
### 3.1 机械尺寸
PCB 尺寸大小：12±0.3mm (L)×15±0.3mm (W) ×0.8±0.1mm (H)。
下图为 WBR3DU-C 封装对应图

![](/assets/images/8720CF/8720cf尺寸.png)


## 更多资料

[详细规格书请前往WBR3DU-C模组规格书下载页面](../../download/8720df/8720df_datasheet.md#rtl8720cf)