
# RTL8711DCM Demonstration Board Wiring Instructions

### 1. Wireless Audio Demonstration Board Control Overview
(1) Wireless 2.1 Audio Demonstration Board Control Diagram
![Image](../../assets/images/speaker/11-08/dome/d-1.PNG)
(2) Wireless 5.1 Audio Demonstration Board Control Diagram
![Image](../../assets/images/speaker/11-08/dome/d-2.PNG)
(3) Wireless 7.1.2 Audio Demonstration Board Control Diagram
![Image](../../assets/images/speaker/11-08/dome/d-3.PNG)

### 2. Wireless Audio Demonstration Board Wiring Overview
#### (1) Wireless Audio TX Demonstration Board I2S, I2C Control Pin Diagram
![Image](../../assets/images/speaker/11-08/dome/4.png)

#### (2) DSP and Wireless Audio TX Demonstration Board I2S, I2C Wiring Diagram
![Image](../../assets/images/speaker/11-08/dome/d-5.png)

1) DSP and Wireless Audio TX Demonstration Board 2.1 Channel I2S Wiring Instructions

- **When DSP is Slave**, the required I2S signal lines are:
I2S_BCLK, I2S_LRCLK, I2S_DATA0, I2S_DATA1, GND

- **When DSP is Master**, the required I2S signal lines are:
I2S_MCLK, I2S_BCLK, I2S_LRCLK, I2S_DATA0, I2S_DATA1, GND

2) DSP and Wireless Audio TX Demonstration Board 5.1 Channel I2S Wiring Instructions

- **When DSP is Slave**, the required I2S signal lines are:
I2S_BCLK, I2S_LRCLK, I2S_DATA0, I2S_DATA1, I2S_DATA2, GND

- **When DSP is Master**, the required I2S signal lines are:
I2S_MCLK, I2S_BCLK, I2S_LRCLK, I2S_DATA0, I2S_DATA1, I2S_DATA2, GND

3) DSP and Wireless Audio TX Demonstration Board 7.1.2 Channel I2S Wiring Instructions

- **When DSP is Slave**, the required I2S signal lines are:
I2S_BCLK, I2S_LRCLK, I2S_DATA0, I2S_DATA1, I2S_DATA2, I2S_DATA3,
I2S_EX_LRCLK, I2S_EX_BCLK, I2S_EX_DATA0, GND

- **When DSP is Master**, the required I2S signal lines are:
I2S_MCLK, I2S_BCLK, I2S_LRCLK, I2S_DATA0, I2S_DATA1, I2S_DATA2, I2S_DATA3,
I2S_EX_LRCLK, I2S_EX_BCLK, I2S_EX_DATA0, GND

#### (3) Wireless Audio RX Demonstration Board Wiring Diagram
![Image](../../assets/images/speaker/11-08/dome/d-6.png)

![Image](../../assets/images/speaker/11-08/dome/d-7.png)


