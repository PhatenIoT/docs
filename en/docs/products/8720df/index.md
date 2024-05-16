---
title: Phaten W5B03A-1720DFV1 Module 
---
# Module W5B03A-1720DFV1 

## 1 Product Overview
## 2 General Description
<p style="text-indent:2em;">
The W5B03A-1720DFV1 is a highly integrated, single-chip, low-power dual-band (2.4 GHz and 5 GHz) wireless local area network (WLAN) and Bluetooth low energy (BLE 5.0) communications controller. It consists of a high-performance MCU called Real-M300 (Armv8-M, or KM4, compatible with the Rortex-M33 instruction set) followed by a low-power microcontroller (Rortex-M23 instruction set compatible) called RealM200 (or KM0 followed by the KM0), a WLAN (802.11 a/b/g/n) MAC, a WLAN (802.11 a/b/g/n) MAC with a 1T1R-capable WLAN baseband, RF, Bluetooth, and peripherals.
</p>
A high-speed connectivity port, SDIO port, and USB port are also provided. There are also audio codecs, key scanning and touch keys integrated into this IC. In addition, the flexible design allows the GPIOs to be configured for different functions depending on the application.
<p style="text-indent:2em;">
The W5B03A-1720DFV1 also integrates memory (ROM/SRAM/PSRAM) for IoT (Internet of Things) Wi-Fi protocol functions and applications. Customers are supported with user-friendly development kits (SDK and HDK) to develop IoT applications.
</p>
The KM4 MCU is a 32-bit core that provides system enhancements such as low power consumption, enhanced debugging features, floating-point computing, DSP instructions, and a high level of support for block integration.The KM4 MCU contains a 3-level pipeline.
<p style="text-indent:2em;">
The KM0 coprocessor is an energy-efficient, easy-to-use 32-bit core that is compatible with the code and tools of the KM4 core.The KM0 coprocessor provides up to 20MHz performance with a simple instruction set and reduced code size.
</p>

## 3 System Architecture

![](/assets/images/8720DF/kappframework-LiXlSP.png)
<p style="text-indent:2em;">
In the W5B03A-1720DFV1, the master system consists of a 32-bit multilayer AXI bus matrix that interconnects all master and slave lines. The bus matrix provides master-to-slave access, enabling parallel access and efficient operation even when multiple high-speed peripherals are operating simultaneously.
</p>
The multi-layer AXI bus matrix connects the CPU bus and other bus masters to peripherals in a flexible way that optimizes performance by allowing different bus masters to simultaneously access peripherals on different slave ports of the matrix.
<p style="text-indent:2em;">
APB peripherals are connected to the AXI bus matrix via APB buses from the AXI bus ports of the multilayer AXI bus matrix. This reduces conflicts between the CPU and the DMA controller, and also allows peripherals on asynchronous bridges to have fixed clocks that do not track the system clock.
</p>

##  4 Product Documentation
[Click to enter W5B03A-1720DFV1 module datasheet](../../download/8720df/8720df_datasheet.md)


<!-- 换行使用<br> -->
##  5 Buy Links
[Click to buy W5B03A-1720DFV1 Module](../../buy_sample/8720df.md)