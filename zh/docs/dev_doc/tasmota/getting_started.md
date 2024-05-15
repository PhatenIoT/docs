---
title: tasmota 开发文档--getting startde
---



# 先决条件
## 所需硬件


### ESP 设备
每台基于[乐鑫](https://www.espressif.com/en/products/socs) ESP8266、ESP8285、ESP32、ESP32-S 或 ESP32-C3 芯片组的设备都可以使用 Tasmota 进行闪存。术语 ESP 是指其中任何一个。

### 串行编程器
[提供给设备的电源](https://www.letscontrolit.com/wiki/index.php?title=Power)是设备闪烁和稳定运行的**最重要因素之一**。您必须确保设备获得足够的功率（电流和适当的电压tage 电平）以正确刷新设备上的固件。

- 推荐 [CH340G](https://cdn.sparkfun.com/datasheets/Dev/Arduino/Other/CH340DS1.PDF) 是最可靠和最便宜的启动（CH340G、[Sparkfun](https://www.sparkfun.com/products/14050)、[焊接连接](https://soldered.com/product/connect-programmer/)、[带AMS1117的 CH340N](https://www.aliexpress.com/item/1005004742270942.html)）。

- 推荐 [VoltLink](https://github.com/voltlog/VoltLink) - 基于流行的 CP2102N 芯片的 USB 转串口适配器板，内置 ESP 自动复位电路和 500mA 稳压器 
![串口适配器图片](/docs/assets/images/tasmota/ch340g.png)

- [CP2102](https://www.silabs.com/documents/public/data-sheets/cp2102-9.pdf) 或 [PL2303](http://www.prolific.com.tw/UserFiles/files/ds_pl2303HXD_v1_4_4.pdf) - 适用于某些器件，但可能需要使用外部 3.3V 电源。不建议初学者使用！

- [节点MCU](https://en.wikipedia.org/wiki/NodeMCU)如果您通过将 GND 桥接到 RST 或 EN 引脚来禁用板载 ESP，并将 TX 和 RX 直接连接到另一个 ESP82xx 而不是交叉连接，您还可以使用 NodeMCU（或类似设备）作为可靠的串行编程器。



<div style="border-radius: 15px; background-color: pink; padding: 10px;">
  不要忘记为您的串行编程器安装驱动程序。
</div>

<p></p>

<div style="border-radius: 15px; background-color: pink; padding: 10px;">
<p>**注意：**</p>
<p>某些适配器可以在 3.3V 和 5V 之间切换数据引脚，但仍可在电源引脚上提供 5V，这将不可挽回地损坏您的设备。您必须确保数据（RX 和 TX）和 VCC 引脚设置为 3.3V。</p>
</div>

许多串行编程器没有像图中那样的板载稳压器。ESP 至少需要 150mA，许多 3.3V 串行编程器无法提供如此大的电流，因为许多串行编程任务不需要大量功率。

使用外部 3.3V 电源时，确保两者的接地 （GND） 连接在一起，这确保了公共接地。PC 电源可以作为 3.3V 直流电源的电源。

具有 USB 上传端口的设备通常内置串行编程器，例如 [NodeMCU](https://en.wikipedia.org/wiki/NodeMCU)、[D1 mini](https://www.wemos.cc/en/latest/d1/d1_mini.html) 或 [M5Stack 产品](https://m5stack.com/)。
<img src="/docs/assets/images/tasmota/golden-ch340g.png" alt="USB 上传端口" width="200"/>

### 焊接工具
要焊接，您当然需要烙铁、锡和一些助焊剂。如果您不熟悉焊接，请查看一些焊接教程视频。

如果您对焊接感到害怕，那么有 3D 打印夹具可用于不同的模块和设备。在最坏的情况下，您可以在闪光期间用跳线将针孔中的接头紧紧固定，但这不是一个万无一失的过程，闪光可能会失败。

### 跳线
您可以使用任何类型的电线，但跳线（也称为杜邦电线）比焊接和拆焊更实用。

### 排针
排针有公头或母头两种版本。根据您的跳线连接器进行选择。

### 装有 Linux、Windows 或 MacOS 的计算机
您需要一台带有 USB 端口的计算机才能将固件上传到您的设备并对其进行配置。

### 智能手机
从预编译的二进制文件安装的 Tasmota 需要配置为与您的 Wi-Fi 网络配合使用，然后才能访问 Tasmota Web UI。这通常是通过使用智能手机（或具有 Wi-Fi 的平板电脑或计算机）连接到 Tasmota Wi-Fi 接入点来完成的。

## 所需软件
### Tasmota 固件二进制文件
下载 Tasmota 固件二进制文件 （.bin）。如果您不确定哪个二进制文件适合您，只需从构建表开始或查阅构建表以查看您需要哪些功能。tasmota.bin

官方版本的二进制文件可以从[固件服务器下载](http://ota.tasmota.com/tasmota/release/)。

最新的开发分支二进制文件只能从我们的 OTA 服务器获得。最新的合并开发代码每小时编译一次。

### 闪烁工具
- **[Tasmota Web 安装程序](https://tasmota.github.io/install/)** - 使用基于 Chrome 的浏览器为 ESP82XX 和 ESP32 刷新 Tasmota
- **[Tasmotizer](https://github.com/tasmota/tasmotizer)** - 仅适用于ESP82XX的闪烁和固件下载工具。（Windows、Linux 或 Mac）
- **[ESP-Flasher](https://github.com/Jason2866/ESP_Flasher)** - 基于 ESP82XX 和 ESP32 esptool.py 的 Tasmota 的 GUI 刷新器.（Windows、Linux 或 Mac）
- **[Esptool.py](https://github.com/espressif/esptoolb)** - 乐鑫为 ESP82XX 和 ESP32 提供的官方刷机工具。

<div style="border-radius: 15px; background-color: #ADD8E6; padding: 10px;">
<p>编译工具（可选）</p>
<p>如果您想修改代码或默认设置并编译您自己的 Tasmota 固件。</p>
</div>

## MQTT知识
Tasmota 旨在通过 [MQTT](http://mqtt.org/) 进行控制和通信。要充分利用它的潜力，您需要一个 [MQTT 代理](https://www.hivemq.com/blog/mqtt-essentials-part-3-client-broker-connection-establishment/)。

阅读TASMOTA关于 [MQTT 的文章](https://tasmota.github.io/docs/MQTT/)，了解为什么它在 Tasmota 中至关重要。

## 硬件准备
我们需要连接到ESP芯片的串口编程接口。这是通过将我们的串行到 USB 转换器 TX 和 RX 引脚连接到 ESP RX 和 TX 引脚并使用 3.3V 和 GND 引脚为芯片供电来完成的。

在大多数情况下，这些引脚在PCB上以引脚孔或焊盘的形式提供，但引脚接头或跳线需要焊接或以其他方式应用。在某些情况下，您需要直接将导线焊接在芯片的引脚上，这需要一些经验和良好的焊接设备。

<div style="border-radius: 15px; background-color: pink; padding: 10px;">
❌请勿在盖子打开且电路板暴露的情况下将设备连接到交流电源!!
</div>

<p></p>
<div style="border-radius: 15px; background-color: pink; padding: 10px;">
<p>⚠️切勿在设备连接到主电源时尝试闪烁⚠️</p>

<p>⚠️如果你不知道自己在做什么，你可能会触电⚠️</p>
</div>
<img src="/docs/assets/images/tasmota/pow1.jpg" alt="pow" width="200"/>
如果你不小心，你自己的健康就会处于危险之中。使用电源交流电源短路串行接口会烧毁您的设备和串行适配器，还会损坏或损坏您的计算机。在通过串行连接时，甚至在打开设备外壳时
**始终将所有电源线与设备断开连接，这一点很重要**。

### 串行连接
每个器件的引脚都以不同的方式标记。如果标签在 PCB 上不可见，请参阅设备闪烁指南或在互联网上搜索正确的引脚位置。特定于设备的说明和限制记录在 Tasmota 支持的设备存储库中。常用 Wi-Fi 模块的引脚排列可在此处找到

识别设备上的引脚后，根据表连接电线：

|    串行适配器   |    ESP设备   |
| ----- | ----- |
| 3V3 | 3V3 or VCC |
| RX | TX |
| TX | RX |
| GND | GND |

**请注意，来自适配器的 TX 转到 ESP 设备上的 RX，来自适配器的 RX 转到设备上的 TX！**
![接线图](/docs/assets/images/tasmota/接线.png)

### 编程模式
Typical GPIO0 Location

ESP需要进入**编程模式**或**刷机模式**，然后才能上传固件。这是通过在芯片启动时将 GPIO0 引脚连接到 GND 来完成的。

在许多设备上，安装的控制按钮连接到 GPIO0 和 GND，从而轻松进入编程模式。在其他情况下，您需要将 PCB 上的引脚桥接或直接用跳线桥接在芯片上。热门模块的 GPIO0 位置可以在[引脚排列](https://tasmota.github.io/docs/Pinouts/)中找到！
设备特定说明记录在 [Tasmota 支持的设备存储库中](https://templates.blakadder.com/)。
![gpio0图片](/docs/assets/images/tasmota/gpio0图片.png)

要将 ESP 置于编程模式：
1. 断开串行编程器和电源
2. 桥接 GPIO0 和 GND（通过按下板载按钮或与电线连接）
3. 将串行编程器连接到您的计算机
4. 几秒钟后，断开 GPIO0 与 GND 的连接（松开按钮或断开电线连接）。在不提供 GPIO0 连接按钮的设备上，在整个闪烁过程（擦除和上传）中将有线桥接器留在原位可能更容易。这样做不会产生任何问题。固件上传成功后，移除网桥。这允许设备正常启动。

<div style="border-radius: 15px; background-color: cyan; padding: 10px;">
<p>esptool.py 编程模式测试</p>
<p>您可以通过尝试从 ESP82xx 芯片读取信息来测试您的设备是否处于编程模式。这需要 .下面提供了有关安装和使用的说明。例如（将是您的 COM 端口）：esptool.pyesptoolCOM5</p>

<p>esptool.py -p COM5 read_mac（它应该读取 MAC 地址。之后在上传和运行“存根”期间可能会失败。这是正常的。</p>
<p>esptool.py -p COM5 flash_id</p>
</div>

如果一切顺利，您现在处于编程模式并准备好继续闪烁。如果刷新过程无法启动，请断开设备连接并重试这些步骤。

### 常见错误
- 电线连接和焊点 - 仔细检查所有连接，并检查焊料是否溢出。
- 使用 **USB 数据线** - 某些 USB 数据线仅用于充电，不连接将固件加载到设备所需的数据线。
- 串行编程器提供的功率不足。这会导致闪烁失败或完全损坏的闪存。使用单独的 3.3V 电源提供更多电源，或使用具有更好电源的适配器。确保所有直流电压都使用相同的 GND 线。
- 重新检查您的串行编程器，以确保它提供 3.3V 电压而不是 **5V。5V会损坏ESP芯片！**
- 在启动完成之前释放 GPIO0 按钮/电线 - 在整个编程过程中（擦除和上传）将 GPIO0 连接到 GND 是安全的。只需确保在启动设备进行正常操作之前移除 GPIO0 到 GND 桥接器即可。
- 确保 RX 引脚连接到串行适配器和 ESP 设备之间的 TX 引脚，反之亦然。注意：某些设备可以将 TX 和 RX 引脚标记为相反。在这种情况下，请将适配器的 TX 连接到 TX，将 RX 连接到 RX 引脚。
- 在上传 Tasmota 固件二进制文件之前，先擦除闪存并重新启动电源。不擦除可能会留下先前闪存内容的残留物，这可能会干扰新固件操作。


## 安装

如果您遵循了**硬件准备**，您的设备应处于**编程模式**并准备好安装 Tasmota 固件二进制文件。
安装方法：将前往Tasmota的原网页

[Web安装程序](https://tasmota.github.io/docs/Getting-Started/#__tabbed_1_1)

 [TAsmotizer](https://tasmota.github.io/docs/Getting-Started/#__tabbed_1_2)

 [esotool.py](https://tasmota.github.io/docs/Getting-Started/#__tabbed_1_3)

 [OTA转换](https://tasmota.github.io/docs/Getting-Started/#__tabbed_1_4)



## 配置后
运行 Tasmota 的设备现在可以控制了。

查看 Tasmota 的所有功能以及将其与其他平台集成的方法。
<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
<p>⚠️警告</p>

<p>如果您遇到电网中的电源波动，最好立即使用命令 SetOption65 1 立即禁用电源循环恢复功能，否则您最终可能会在设备上使用固件默认值。</p>
</div>