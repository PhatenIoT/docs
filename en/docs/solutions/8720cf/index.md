---
title: WBR3DU-C Transparent Transmission Solution Based on WBR3DU-C
---


# WBR3DU-C Transparent Transmission Solution Based on WBR3DU-C

<p>WIFI Transparent Transmission Solution based on WBR3DU-C AT Instruction Set; is a technology that utilizes the AT instruction set to achieve transparent transmission of data through WIFI networks. This solution is widely used in Internet of Things (IoT) devices, such as smart home appliances, sensor networks, etc. It allows devices to communicate with other devices or servers over WIFI networks without user intervention. </p>

### I. Solution Overview

1. Hardware composition: usually includes a WIFI module and a microcontroller (MCU).
2. Software Component: Includes an AT instruction set parser and a WIFI driver. 3.
3. Workflow: The MCU sends AT commands to the WIFI module through the serial port, and the WIFI module parses these commands and performs the corresponding network operations.

### II. Core Advantages
1. Simple and easy to use: AT instruction set is standardized, easy to learn and use.
2. High flexibility: supports customized AT instructions, and can flexibly expand functions according to needs.
3. Cost-effective: suitable for low-cost embedded systems.
4. Good compatibility: Most WIFI modules support AT instruction set.
![AT instruction set](/assets/images/8720CF/1280X1280.PNG)

### III. Implementation Steps
1. Initialize WIFI module: Send specific AT instruction to initialize WIFI module.
2. Connect to network: Connect to the specified WIFI network by AT command.
3. data passthrough: use AT instruction to passthrough data from MCU to network or from network to MCU.
![realization plan](/assets/images/8720CF/逻辑图.PNG)