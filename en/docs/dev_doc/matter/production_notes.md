
# 生产注意事项
## 1 先决条件
所有 Matter 示例都使用某些测试或评估值，使您能够快速构建和测试 Matter。当您准备投入生产时，必须将这些值替换为实际值。这些值通常是设备中制造分区的一部分。

### 1.1 供应商 ID 和产品 ID
供应商标识符 （VID） 是一个 16 位数字，用于唯一标识特定 产品制造商或供应商。它由连接标准分配 联盟 （CSA）。为此，请联系 CSA。

产品标识符 （PID） 是一个 16 位数字，用于唯一标识产品 供应商。它由供应商（您）分配。

VID-PID 组合唯一标识 Matter 产品。

### 1.2 证书
设备证明证书 （DAC） 证明设备的真实性 制造商以及设备硬件和软件的认证状态。 每个 Matter 设备都必须有一个 DAC 和相应的私钥，这是它唯一的。 设备还应具有产品认证中间体 （PAI） 证书 用于签署和证明 DAC。PAI证书依次签名 并由产品认证机构 （PAA） 证明。 PAA 证书是隐式受信任的自签名根证书。

请联系您的乐鑫代表，了解详情 采购DAC。

### 1.3 认证声明（CD）
认证声明 （CD） 是一种加密文档，允许 Matter 设备来声明其协议合规性。一旦您的产品获得认证，CSA 为该设备创建 CD。然后，CD 应包含在设备固件中 由设备制造商提供。

### 1.4 设置密码、鉴别器和载入有效负载
唯一的设置密码用作所有权证明，也用于计算 调试期间的共享密钥。相应的 SPAKE2+ 验证器 密码安装在设备上，而不是实际的密码。

鉴别器用于轻松区分设备，以提供无缝的 调试期间的经验。

载入有效负载是辅助的二维码和手动配对码 一个专员（如手机应用程序），允许将设备加入 Matter 网络。 二维码和/或手动配对码一般印在包装上 装置。

### 1.5 制造分区
乐鑫 SDK for Matter 使用单独的制造分区来存储所有信息 上述。由于DAC对于每个器件都是唯一的，因此制造分区 每个设备也将是唯一的。因此，通过将所有典型的每个设备的唯一字段移动到 制造分区、其余组件（如引导加载程序）、固件映像 在您的所有设备上都很常见。您可以参考下面的“制造”部分进行创建 大量制造分区镜像。

您的生产线需要确保这些唯一的制造分区映像是 正确写入每个设备以及与每个设备关联的相应二维码图像。 您也可以选择乐鑫的预配置服务，预先配置这些独特的 在发货模块之前提供图像，并提供清单（CSV 文件）以及 QR 码图像 捆。

## 2 无线 （OTA） 更新
Matter 设备必须支持 OTA 固件更新，方法是使用基于 Matter 的 OTA 或供应商特定方式。

在 Matter OTA 的情况下，有一个 OTA 提供商 协助 OTA 请求者升级。SDK 示例支持 Matter OTA 开箱即用的请求者角色。OTA 提供商可以是特定于制造商的 手机应用程序或任何具有互联网连接的 Matter 节点。

另外，ESP RainMaker OTA 服务也可用于远程升级设备上的固件。与 Matter OTA 相反，ESP RainMaker OTA 允许您灵活地以增量方式或向设备组提供 OTA 升级。

## 3 制造业
### 3.1 大规模制造效用
要将设备调试到 Matter Fabric 中，设备需要以下信息：

设备认证证书 （DAC） 和认证声明 （CD）：由专员验证，以确定设备是否是 Matter 认证产品。

鉴别器：在调试期间进行广告宣传，以便于区分广告设备。

Spake2+ 参数：用作所有权证明。

这些细节通常在唯一的制造分区中编程 每台设备。ESP-Matter 提供了一个实用程序 （mfg_tool.py） 来创建这些分区映像 以每台设备为基础，用于大规模制造目的。

使用该实用程序时，默认情况下，上述详细信息将包含在生成的制造分区映像中。该实用程序还规定使用CSV文件在同一图像中包含其他详细信息。

有关使用大规模制造实用程序的详细信息，请访问：mfg_tool。

### 3.2 预置模块
ESP32 模组可以预录用制造分区映像 在模块制造过程中，然后发货给您。

这为您节省了安全生成、加密和 将分区编程到设备中。

请联系您的乐鑫联系人了解更多信息。

### 3.3 mfg_tool示例
在乐鑫 Matter 预配模块中，DAC 密钥对、DAC 和 PAI 证书默认预刷新。

本节给出了一些关于如何生成工厂分区二进制文件的示例，其中包括：
设备唯一数据（鉴别器、验证器、序列号等）
制造信息（供应商名称、产品名称、硬件版本等）
注意

示例中列出的项目都是必需的，如果在固件中硬编码，则可以删除一些常见的制造信息。

以下是预配置后生成出厂映像的示例：

生成通用工厂映像

./mfg_tool.py -cd ~/test_cert/CD/Chip-CD-131B-1000.der -v 0x131B --vendor-name ESP -p 0x1000 --product-name light --hw-ver 1 --hw-ver-str v1.0 --mfg-date 2022-10-25 --passcode 19861989 --discriminator 601 --serial-num esp32c_dev3
生成多个通用工厂映像

./mfg_tool.py -n 10 -cd ~/test_cert/CD/Chip-CD-131B-1000.der -v 0x131B --vendor-name ESP -p 0x1000 --product-name light --hw-ver 1 --hw-ver-str v1.0 --mfg-date 2022-10-25
使用旋转设备唯一标识生成工厂图像

./mfg_tool.py -cd ~/test_cert/CD/Chip-CD-131B-1000.der -v 0x131B --vendor-name ESP -p 0x1000 --product-name light --hw-ver 1 --hw-ver-str v1.0 --mfg-date 2022-10-25 --passcode 19861989 --discriminator 601 --serial-num esp32c_dev3 --enable-rotating-device-id --rd-id-uid c0398f4980b07c9460f71c5421e1a3c5
使用 csv 和 mcsv 生成多个工厂映像

./mfg_tool.py -cd ~/test_cert/CD/Chip-CD-131B-1000.der -v 0x131B --vendor-name ESP -p 0x1000 --product-name light --hw-ver 1 --hw-ver-str v1.0 --enable-rotating-device-id --mfg-date 2022-10-25 --csv mfg.csv --mcsv mfg_m.csv
csv 和 mcsv 文件示例

CSV：
serial-num，data，string
rd-id-uid，数据，十六进制2bin
鉴别器，数据，U32
MCSV：
串行编号，rd-id-uid，鉴别器
esp32c_dev3，c0398f4980b07c9460f71c5421e1a3c5,1234
esp32c_dev4，c0398f4980b07c9460f71c5421e1a3c6,1235
esp32c_dev5，c0398f4980b07c9460f71c5421e1a3c7,1236
esp32c_dev6，c0398f4980b07c9460f71c5421e1a3c8,1237
esp32c_dev7，c0398f4980b07c9460f71c5421e1a3c9,1238


