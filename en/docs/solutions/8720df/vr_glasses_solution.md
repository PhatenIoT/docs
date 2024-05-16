---
title: W5B03A-1720DFV1 5.8G Data Transmission Application Solution
---
# W5B03A-1720DFV1 5.8G Data Transmission Application Solution

## 1 Industry Requirements

1. Automotive head-mounted VR glasses accurately synchronize VR content with the physical movement of the car by acquiring data from the car's sensors to prevent vertigo.
2. Acquiring data from automotive sensors: position data, motion data, vehicle status, environmental data, etc.
3. The data from the car sensors need to be transmitted to the VR glasses by wired or wireless means.

## 2 Market Existing Solutions

1. Wired: Wired transmission of vehicle sensor data restricts the flexibility and convenience of moving the head-mounted VR glasses.
2. Wireless: Wireless Wifi 2.4G transmission method, high latency, packet loss, unstable connection and other shortcomings.

## 3 W5B03A-1720DFV1 5.8G Transparent Transmission Solution
Based on W5B03A-1720DFV1 5.8G wireless transmitting application program has the following characteristics:

1. low latency: TCP/UDP data transmission <15ms
2. stable connection: TCP/IP-based error detection and retransmission mechanism
3. Low packet loss rate: based on 5.8G high speed transmission to ensure data stability.

## 4 Advantages
This program is based on W5B03A-1720DFV1 module; RTL872xD is a dual-band Wi-Fi (2.4G+5G) and BLE5.0 Soc chip. With ultra-low power consumption, complete encryption strategy and rich peripheral resources, it has low latency and high transmission speed compared with traditional 2.4G communication, which can fully meet the requirements of real-time data processing and low-latency transmission of VR glasses.
![W5B03A-1720DFV1 5.8G Data Transmission Application Solution](/assets/images/8720DF/RTL-8720DF-5.8G透传方案.JPEG.png)

1. MCU module collects vehicle data through sensors. 2.
2. Collected vehicle data, through the serial port AT command control W5B03A-1720DFV1 to establish TCP/UDP connection, through the 5.8G transmission, the data will be transmitted to the VR glasses.
3. VR glasses receive the transmitted vehicle data and precisely adjust the position to fit the vehicle movement.   

## 5 Product Description
[Click to view W5B03A-1720DFV1 module introduction](../../products/8720df/index.md)

