

# 连接Home Assistant
1.配置Tasmota设备

- 刷入Tasmota固件： 确保你的设备已经刷入了Tasmota固件。这可以通过串口或者OTA方法完成。
- 配置MQTT连接： 在Tasmota的Web界面中，进入"Configuration"（配置） -> "Configure MQTT"（配置MQTT），输入你的MQTT服务器的地址、端口和认证信息（如果有的话）。保存设置并重启设备，确保Tasmota能够通过MQTT与你的Home Assistant通信
      
![](/assets/images/tasmota/tasmota_matter/1-1.PNG)

2.配置Home Assistant

- 集成MQTT： 在Home Assistant的配置文件（通常是configuration.yaml）中添加MQTT集成。

---
     示例配置如下：
        mqtt:
        broker: [MQTT Broker的IP地址或域名]
        port: [MQTT Broker的端口，通常是1883]
        username: [MQTT Broker的用户名，如果有的话]
        password: [MQTT Broker的密码，如果有的话]
---

- 保存配置文件并重启Home Assistant，确保MQTT集成正常工作。

![](/assets/images/tasmota/tasmota_matter/1-2.PNG)

3.配置Home Assistant集成

- 添加Tasmota设备： 在Home Assistant的Web界面中，进入"Configuration"（配置） -> "Integrations"（集成），点击添加新的集成，搜索并选择MQTT集成。按照指导填写MQTT broker的信息，然后选择你希望集成的Tasmota设备。Home Assistant会尝试通过MQTT发现和集成你的Tasmota设备。
- 验证集成： 在Home Assistant中查看你的Tasmota设备是否成功集成。可以尝试控制设备，确保一切正常工作。
![](/assets/images/tasmota/tasmota_matter/1-3.PNG)
![](/assets/images/tasmota/tasmota_matter/1-4.PNG)

注意事项：

- 固件和硬件支持： 确保你选择的Tasmota设备支持你计划使用的协议（如Matter）
- 网络设置： 确保设备和Home Assistant在同一个网络中，以便能够顺利进行通信。
- 安全性： Tasmota的 MQTT 配置和Home Assistant 的MQTT 保持一致。


