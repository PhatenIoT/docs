# 8711 Series Programming Tool Guide

### Preparation:

**Programming Tool**: [Download Link](../../assets/download/A316/ImageTool.zip)

To enter programming mode: First, press and hold the "download" button, then press and hold the "chip" button. The serial port will print `\0`. Release both buttons simultaneously.

To enter print mode: Press the "chip" button once.
![Image 1](../../assets/images/speaker/shaolu-1.png)

---

### 1. Starting the Tool
After downloading the tool, locate the file shown in the image and double-click to open.
![Image 2](../../assets/images/speaker/shaolu-2.png)

---

### 2. Opening the Software
Once the software is open, click "File," then click "Open" to select the firmware file.
![Image 3](../../assets/images/speaker/shaolu-3.png)

---

### 3. Selecting the Firmware
Choose the file **“AmebaDplus FreeRTOS NOR.rdev”** (third file), which is used for burning the 8711 firmware.
The sixth file is for burning the 8730 firmware, choose according to your needs.
![Image 4](../../assets/images/speaker/shaolu-4.png)

---

### 4. Configuration
Select the configuration file, then choose the firmware to be burned. Ensure that the names match.
![Image 5](../../assets/images/speaker/shaolu-5.png)

---

### 5. Configuring Port and Baud Rate
Select the serial port, baud rate, and other settings as shown in the image (the settings should be auto-selected by default). After verification, click the "Download" button at the bottom to start the burning process.
![Image 6](../../assets/images/speaker/shaolu-6.png)

---

### 6. Burning Completion
Once the burning process completes without any errors, check the serial port logs. If the logs print normally, the burning process was successful.
![Image 7](../../assets/images/speaker/shaolu-7.png)
