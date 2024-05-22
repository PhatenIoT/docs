---
title: Phaten WBR3DU-C Product Specification 
---
# WBR3DU-C Product Specification 




## 1 Product Description
WBR3DU-C is a low power consumption embedded Wi-Fi+Bluetooth module. It consists of a highly integrated wireless RF chip
RTL8720CF(W701H-VT2-CG) with built-in Wi-Fi network stack and rich library functions. This product also includes a low-power KM4
MCU, WLAN MAC, 1T1R WLAN, up to 100MHz, 256K SRAM, 2Mbyte flash and rich peripheral resources.
device resources.
The WBR3DU-C is an RTOS platform with integrated libraries for all Wi-Fi MAC and TCP/IP protocols. Users can develop their own embedded Wi-Fi applications based on these
WBR3DU-C is an RTOS platform that integrates all Wi-Fi MAC and TCP/IP protocol libraries.
1.1 Product Features
- Built-in low-power KM4 MCU, which can be used as an application processor.
- Support 100MHz main frequency
- Operating voltage: 3.0V~3.6V
- Wi-Fi Bluetooth connectivity
    - 802.11 b/g/n
    - Channel 1-14@2.4GHz (CH1-11 for US/CA, CH1-13 for EU/CN)
    - Supports WEP,WPA/WPA2,WPA2 PSK (AES) security mode
    - Supports Bluetooth 4.2 Low Energy
    - Supports SmartConfig and AP (both Android and IOS devices)
    - External Antenna
    - Operating temperature: -40°C to 105°C


### 1.2 Specification

| Item | Description |
|--------------|---------------------------|
| Product Name | WBR3DU-C |
| Product Description | Wi-Fi and BT 4.2 Dual Mode Module |
| Product Dimension | L x W: 12±0.3 *15±0.3 mm |
| Interface Type | SMT Type | 
| Eco-Friendly |  All hardware components are fully compliant with EU RoHS Directive. |


### 1.3 Absolute electrical parameters


| Parameter | Description | Minimum | Maximum | Unit |
|-----------------|--------------|------|------|----|
| Ts | Storage Temperature | -40 | 125 | °C |
| VBAT | Supply voltage | -0.3 | 3.6 | V |
| Static Discharge Voltage (Human Body Models) | TAMB -25 °C | - | 2 | KV |
| TAMB -25°C | - | 0.5 | KV | Static Discharge Voltage (Machine Model) | TAMB -25°C | - | 0.5 | KV | Static discharge voltage (machine model)


### 1.4 Normal Operating Conditions

| Parameter | Description | Minimum | Standard | Maximum | Unit |
|-------|------------|----|----|----|----|
| Ta | Operating Temperature | -40 | - | 105 | °C |
| VBAT | Supply Voltage | 3.0 | 3.3 | 3.6 | V | VIL |
| VIL | IO low input | - | - | 0.8 | V |
| VIH | IO High Input | 2.0 | - | - | V |
| VOL | IO Low Output | - | - | 0.4 | V |
| VOH | IO High Level Output | 2.4 | - | - | V |
| I IO | Drive Current | - | - | 16 | mA |


## 2 Pin Description
### 2.1 Pin Definition Diagram & Pin Definition

![](/assets/images/8720CF/8720cf管脚.png)

| Serial Number | Pin Definition | IO Type | Function
|------|---------|-------|-----------------|                                                
| 1  | GND    | P   | Power Reference Ground            |                                         
| 2  | VCC    | P   | Module Power Pin (3.3V)   |                                              
| 3  | A19    | I/O | GPIOA_19，Hardware PWM，IC Pin40   |                                      
| 4  | A18    | I/O | GPIOA_18，Hardware PWM，IC Pin39    |                                   
| 5  | A17    | I/O | GPIOA_17，Hardware PWM，IC Pin38     |                                     
| 6  | A16    | I/O | GPIOA_16，UART_Log_TXD (for printing internal module information), can be configured as a normal GPIO      |      
| 7  | A15    | I/O | GPIOA_15，UART_Log_RXD (for printing internal information of the module), can be configured as a normal GPIO    |               
| 8  | A14/TX | I/O | GPIOA_14，UART0_TXD（user serial port）     |                                      
| 9  | A13/RX | I/O | GPIOA_13，UART0_RXD（user serial port）    |                              
| 10 | A12    | I/O | GPIOA_12，Hardware PWM，IC Pin26       |                                    
| 11 | A11    | I/O | GPIOA_11，Hardware PWM，IC Pin25       |                                   
| 12 | A7     | I/O | GPIOA_7，Hardware PWM，IC Pin21         |                                 
| 13 | A4     | I/O | GPIOA_4，Hardware PWM，IC Pin20         |                                  
| 14 | A3     | I/O | GPIOA_3，Hardware PWM，IC Pin19          |                                  
| 15 | A2     | I/O | GPIOA_2，Hardware PWM，IC Pin18          |                                 
| 16 | A0     | I/O | GPIOA_0                                |                                 
| 17 | EN     |     | Module enable pin, active high, module has been pulled up high, the user can externally control this pin    |                   


## 3 Package Information and Production Guidelines
### 3.1 Mechanical Dimensions
PCB size: 12±0.3mm (L) × 15±0.3mm (W) × 0.8±0.1mm (H).
The following diagram shows the WBR3DU-C package counterpart.

![](/assets/images/8720CF/8720cf尺寸.png)


## More information

[For detailed specs, please go to WBR3DU-C Module Specification Download Page](../../download/8720df/8720df_datasheet.md#rtl8720cf)