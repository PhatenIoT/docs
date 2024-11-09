
### 1 射频功耗
|工作状态|模式|速率|功率|平均值|峰值|单位|
|---|---|---|---|---|---|---|
|TX|2.4GHz11b|11Mbps|+18dBm|254|500|mA|
|TX|2.4GHz11g|54Mbps|+16dBm|224|500|mA|
|TX|2.4GHz11n|HT40 MCS7|+15dBm|206|500|mA|
|TX|5GHz11a|54Mbps|+16dBm|297|500|mA|
|TX|5GHz11n|HT40 MCS7|+15dBm|286|500|mA|

|工作状态|模式|速率|平均值|峰值|单位|
|---|---|---|---|---|---|
|RX|2.4GHz11b|11Mbps|49|65|mA|
|RX|2.4GHz11g|54Mbps|59|77|mA|
|RX|2.4GHz11n|HT40 MCS7|63|77|mA|
|RX|5GHz11a|54Mbps|61|77|mA|
|RX|5GHz11n|HT40 MCS7|65|77|mA|

## 2. 射频技术指标
### 2.1基本射频特性 - 2.4GHz
- **无线标准**：IEEE 802.11b/g/n。
- **通讯频率范围**：2.412 - 2.484GHz（2.4GHz ISM Band）。
- **调制方法**：DSSS、DBPSK、DQPSK、CCK和OFDM（BPSK/QPSK/16 - QAM/64 - QAM）。
- **传输速率**：802.11b支持1、2、5.5、11Mbps；802.11g支持6、9、12、18、24、36、48、54Mbps；802.11n - 2.4 HT20和HT40均支持MCS0 - 7。
- **天线类型**：PCB天线。

### 2.2发射性能
|参数项|最小值|典型值|最大值|EVM|
|---|---|---|---|---|
|802.11b@11Mbps|16dBm|18dBm|20dBm|≤ - 13dB|
|802.11g@54Mbps|15dBm|17dBm|19dBm|≤ - 25dB|
|802.11n@N20 MCS7|14dBm|16dBm|18dBm|≤ - 27dB|
|802.11n@N40_MCS7|14dBm|16dBm|18dBm|≤ - 27dB|
|频偏误差|-12ppm||12ppm|

### 2.3接收性能
|RX|典型值|单位|
|---|---|---|
|PER<8% 802.11b@11Mbps|≤ - 85|dBm|
|PER<10% 802.11g@54Mbps|≤ - 73|dBm|
|PER<10% 802.11n@N20 MCS7|-68|dBm|
|PER<10% 802.11n@N40 MCS7|-65|dBm|

### 2.4基本射频特性 - 5GHz
- **无线标准**：IEEE 802.11a/n。
- **通讯频率范围**：5.180 - 5.825GHz。
- **调制方法**：OFDM（BPSK/QPSK/16 - QAM/64 - QAM）。
- **传输速率**：802.11a支持6、9、12、18、24、36、48、54Mbps；802.11n HT20和HT40均支持MCS0 - 7。
- **天线类型**：PCB天线。

### 2.5发射性能
|参数项|最小值|典型值|最大值|EVM|
|---|---|---|---|---|
|802.11a@54Mbps|11dBm|13dBm|15dBm|≤ - 25dB|
|802.11n@N20_MCS7|10dBm|12dBm|14dBm|≤ - 27dB|
|802.11n@N40_MCS7|10dBm|12dBm|14dBm|≤ - 27dB|
|频偏误差|-12ppm||12ppm|

### 2.6接收性能
|RX|单位|
|---|---|
|PER<10% 802.11a@54Mbps|dBm|
|PER<10% 802.11n@N20 MCS7|dBm|
|PER<10% 802.11n@N40 MCS7|dBm|

### 2.7蓝牙技术指标
- **蓝牙规格**：蓝牙5.0。
- **工作频率**：2.402 - 2.480GHz。

### 2.8射频技术参数
|模式|速率|功率(dBm)|频率(Khz)|灵敏度|
|---|---|---|---|---|
|BLE|GPSK/1Mbps|0 - 10|±75|≤ - 95dB（灵敏度LE1M@PER<30.8%）|
|BLE|GPSK/2Mbps|0 - 10|±75|≤ - 93dB（灵敏度LE2M@PER<30.8%）|

## 3. 硬件设计指南
### 3.1天线设计注意事项
为确保Wi - Fi性能最优，模组天线部分与其他金属件距离至少15mm以上。

### 2 Pin描述
#### 2.1 Pin定义图
![8711 模组图片.png](../../assets/images/speaker/11-08/model/8711%20模组图片.png)


#### 2.2 Pin定义
|序号|Pin定义|I0类型|功能|
|---|---|---|---|
|1|GND|G|地|
|2|BAT MEAS|I/0|battery voltage measurement|
|3|PB4|I/0|LOG RXD|
|4|PB5|I/0|LOG TXD|
|5|PB6|I/0|GPIO PB6|
|6|PB7|I/0|GPIO PB7|
|7|PB8|I/0|GPIO PB8|
|8|PB9|I/0|GPIO PB9|
|9|PB10|I/0|GPI0 PB10/音频发射模式 - I2S - IN - MCLK PIN|
|10|GND|G|地|
|11|PB13|I/0|GPIO PB13|
|12|PB14|I/0|GPIO PB14|
|13|PB15|I/0|GPIO PB15/IIC - SDA|
|14|PB16|I/0|GPI0 PB16/IIC - SCL|
|15|PB17|I/0|GPI0 PB17/音频接收模式 - I2S - OUT - DATA1 PIN|
|16|PB18|I/0|GPIO PB18|
|17|PB19|I/0|GPIO PB19|
|18|PB20|I/0|GPIO PB20|
|19|PB21|I/0|GPIO PB21|
|20|PB22|I/0|GPI0 PB22/音频发射模式 - 12S - IN - DATA2 PIN|
|21|PB30|I/0|GPIO PB30|
|22|PB31|1/0|GPIO PB31|
|23|CHIP EN|RST|Chip enable or shut - down selected pin 1: Enable the chip 0: Shut down the chip 模组内部有3.3V上拉|
|24|GND|G|地|
|25|VDD33|P|VCC|
|26|GND|G|地|
|27|PA8|I/0|GPIO PA8|
|28|PA12|I/0|GPIO PA12|
|29|GND|G|地|
|30|PA13|I/0|GPIO PA13|
|31|PA14|I/0|GPI0 PA14|
|32|PA15|I/0|GPI0 PA15|
|33|PA16|I/0|GPIO PA16|
|34|PA17|I/0|GPIO PA17|
|35|PA18|I/0|GPIO PA18|
|36|PA19|I/0|GPI0 PA19/音频接收模式 - I2S - OUT - MCLK PIN|
|37|PA20|I/0|GPI0 PA20/音频发射模式 - I2S - IN - LRCLK PIN/音频接收模式 - 12S - OUT - LRCLK PIN|
|38|PA21|I/0|GPI0 PA21/音频发射模式 - I2S - IN - DATA0 PIN|
|39|PA22|I/0|GPI0 PA22/音频发射模式 - 12S - IN - DATA1 PIN/音频接收模式 - 12S - OUT - DATA0 PIN|
|40|PA23|I/0|GPI0 PA23/音频发射模式 - 12S - IN - BCLK PIN/音频接收模式 - 12S - OUT - BCLK PIN|
|41|GND|G|地|
|42|PA26|I/0|GPI0 PA26 / UART TX|
|43|PA27|1/0|GPIO PA27 / UART RX|
|44|PA28|I/0|GPIO PA28|
|45|PA29|I/0|GPIO PA29|
|46|PA30|I/0|GPIO PA30|
|47|PA31|I/0|GPI0 PA31|
|48|PBO|I/0|GPIO PBO|
|49|PB1|I/0|GPIO PB1|
|50|PB2|I/0|GPIO PB2|
|51|PB3|I/0|GPIO PB3|
|52|GND|G|地|
|53|NC||No connect|
|54|GND|G|地|


## 4.机械尺寸
PCB尺寸为16.1±0.3mm（L）×29.1±0.3mm（W）×0.8±0.1mm（H）。

![8711 模组尺寸.png](../../assets/images/speaker/11-08/model/8711%20模组尺寸.png)
