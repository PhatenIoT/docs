---
title: WBR3DU-C's Transmission Application Solution
---


# WBR3DU-C's Transmission Application Solution



The product of this solution is **WBR3DU-C module** 

It is a WIFI pass-through solution based on the RTL8720CF AT instruction set; a technology that utilizes the AT instruction set to achieve transparent data transmission over WIFI networks. This solution is widely used in Internet of Things (IoT) devices, such as smart home appliances, sensor networks, etc. It allows devices to communicate with other devices or servers over WIFI networks without user intervention.

## 1 Solution Overview
The WBR3DU-C Embedded Wi-Fi provides a solution to connect a user's physical device to a Wi-Fi wireless network and provides a UART serial port to transfer data. The module hardware integrates MAC, base frequency chip, and RF transceiver unit; AT pass-through firmware supports Wi-Fi protocol and configuration.WBR2 module is an integrated 801.11 b/g/n Wi-Fi low-power solution, and through the pass-through protocol, the traditional low-end serial port devices or MCU-controlled devices can be easily accessed to the Wi-Fi wireless network, thus realizing the IOT network control and management.

## 2 Program features

- No data loss
- Bi-directional data transmission
- There is no protocol encapsulation for WIFI over-the-air packets, so you can control the packet size yourself.
- Users do not need to understand the complex underlying protocol of WIFI, just a few simple steps to set up the WIFI transmission.

## 3 Program Advantages

- Simple and easy to use: AT command set is standardized, easy to learn and use.
- High flexibility: supports customized AT commands, which can flexibly expand the functions according to the requirements.
- Cost-effective: suitable for low-cost embedded systems.
- Good compatibility: Most WIFI modules support AT instruction set.
- Rich functionality: supports WIFI STA and AP, static IP function, TCP/UDP pass-through function.

## 4 Functional Block Diagram
![functional block diagram](/assets/images/8720CF/功能框图.png)

## 5 Implementation steps
1. Initialize WIFI module: send specific AT command to initialize WIFI module.
2. Connect to network: Connect to the specified WIFI network using AT instruction.
3. Data passthrough: Use AT instruction to passthrough data from MCU to network or from network to MCU.


## 6 Functions

1. AP association application 

![AP association application ](/assets/images/8720CF/1280X1280AP关联应用.PNG)

2.WIFI STA + AP functional application

![WIFI STA + AP functional application](/assets/images/8720CF/1280X1280WIFISTAAP功能应用.PNG)

3.TCP/UDP Transmission applications 

![TCP/UDP Transmission applications](/assets/images/8720CF/1280X1280TCP-UDP透传应用.PNG)

## 7 Product Description
[Click here to see the introduction of WBR3DU-C module](../../products/8720cf/index.md)
