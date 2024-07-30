
# 连接Amazon的Alexa
### 1. 配置Tasmota设备和MQTT
     In Configuration - Configure Other page in the webUI select emulation type

![](/assets/images/tasmota/tasmota_matter/2-1.png)

#### Belkin WeMo 

   Belkin WeMo适用于带有单个继电器的设备，Hue Bridge适用于带有一个或多个继电器的设备或灯具。
   Tasmota设备将被Alexa应用程序发现。您不需要安装Wemo应用程序或在Alexa中启用Wemo技能。
   只需告诉Alexa发现合适类型的设备（插头、开关等）
   当它询问什么品牌的设备时，滚动到末尾并选择“其他”。

#### Hue桥接

对于灯光控制，支持颜色控制 、开/关和调光。

启用Hue Bridge模拟并在Alexa应用程序中执行设备发现。Alexa不需要添加任何技能。

选择Hue Bridge V1作为设备类型。

### 2. 在 Alexa 里面 语音 告诉 Alexa发现设备，Alexa 会搜索到 Tasmota的设备，支持echo 音响语音控制
![](/assets/images/tasmota/tasmota_matter/2-2.png)