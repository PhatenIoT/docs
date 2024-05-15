# Matter认证
Matter 认证表示产品符合连接标准联盟 （CSA） 规范，并允许使用认证产品徽标并在联盟网站上列出产品以进行验证。

在申请 Matter 认证之前，您需要成为 CSA 的成员并向 CSA 认证申请供应商 ID 代码。然后，您需要选择授权的测试提供商（必须经过 Matter 测试验证）并提交您的产品进行测试。以下是 Matter 认证测试的一些提示。

## 1 测试工具简介 （TH）
RaspberryPi 上的 Test Harness 用于 Matter 认证测试。您可以从此处获取 TH RaspberryPi 映像，并使用 Raspberry Pi Imager 将映像安装到 micro SD 卡上。

测试用例可以通过 4 种方法进行验证，包括 UI-Automated、UI-SemiAutomated、UI-Manual 和 Verification Steps Document。网站 UI 用于前三种方法。您可以按照 TH 用户指南中的说明使用网站 UI。对于最后一种方法，您应该在 TH 的路径中使用芯片工具，并逐步执行验证步骤文档中的命令。~/apps

## 2 Matter 工厂分区二进制
Matter 工厂分区二进制文件包含可委托信息（鉴别器、盐、迭代计数和 spake2+ 验证器）和设备证明信息（认证声明 （CD）、产品证明中间 （PAI） 证书、设备证明证书 （DAC） 和 DAC 私钥）、设备实例信息（供应商 ID、供应商名称、产品 ID、产品名称等）和设备信息（固定标签、支持的区域设置等）。这些信息用于识别产品并确保调试的安全性。

### 2.1 认证声明
认证声明 （CD） 是一种加密文档，允许 Matter 设备断言其协议合规性。可以通过以下步骤生成它。我们需要生成与 DAC 中的供应商 ID 和产品 ID 以及基本信息集群中的供应商 ID 和产品 ID 相匹配的 CD。

Matter 认证测试需要由 connectedhomeip SDK 存储库中的测试 CD 签名密钥签名的测试 CD，因此它的 1（临时）。通过 Matter 认证测试的官方产品中的 CD 由 CSA 颁发，并且是 2（官方）。certification_typecertification_type

生成测试 CD 文件
```
cd path/to/esp_matter/connnectedhomeip/connnectedhomeip
out/host/chip-cert gen-cd --format-version 1 --vendor-id 0x131B --product-id 0x1234 \
                          --device-type-id 0x010c --certificate-id CSA00000SWC00000-01 \
                          --security-level 0 --security-info 0 --version-number 1 \
                          --certification-type 1 \
                          --key credentials/test/certification-declaration/Chip-Test-CD-Signing-Key.pem \
                          --cert credentials/test/certification-declaration/Chip-Test-CD-Signing-Cert.pem \
                          --out path/to/test_CD_file
```
<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
注意

对于 Matter 认证测试，该选项必须为 1。--certification-type

选项 （vendor_id） 应为供应商从 CSA 接收的供应商 ID （VID），（product_id） 应为供应商选择的产品 ID （PID）。它们应与基本信息聚类中的属性值相同。--vendor_id--product_id

如果产品使用受信任的第三方认证机构提供的 DAC 和 PAI 认证，则 DAC 中的 VID 和 PID 与基本信息集群中的 VID 和 PID 不同。然后，应在生成测试 CD 文件的命令中添加 and 选项。--dac-origin-vendor-id--dac-origin-product-id
</div>

## 2.2 证书和密钥

对于 Matter 认证测试，供应商应生成自己的测试产品认证机构 （PAA） 证书、产品认证中间 （PAI） 证书和设备认证证书 （DAC），但不能使用 connectedhomeip SDK 存储库中的默认测试 PAA 证书。因此，您需要生成一个 PAA 证书，按照 DCL Primer 中的说明将其上传到 TestNet，并使用它来签署和证明 PAI 证书，这些证书将用于签署和证明 DAC。PAI 证书、DAC 和 DAC 的私钥应存储在您提交测试的产品中。

以下是使用 chip-cert 和 mfg_tool 生成证书和密钥的步骤。

#### 2.2.1 生成PAA证书
建议将供应商范围的 PAA 证书用于 Matter 证书测试。它可以在上述步骤的帮助下生成。

生成供应商范围的 PAA 证书和密钥，请确保根据正在使用的选项更改 （vendor_id） 选项。--subject-vid
```

cd path/to/connnectedhomeip/out/host/
./chip-cert gen-att-cert --type a --subject-cn "Example PAA CN" --subject-vid 0x131B \
                         --valid-from "2021-06-28 14:23:43" --lifetime 4294967295 \
                         --out-key /path/to/PAA_key \
                         --out /path/to/PAA_certificate
```
#### 2.2.2 生成工厂分区二进制文件
获取PAA证书和密钥后，可以使用mfg_tool生成包含PAI证书、DAC和DAC密钥的出厂分区二进制文件。

安装要求并导出依赖工具路径（如果尚未完成）

cd path/to/esp_matter/tools/mfg_tool
python3 -m pip install -r requirements.txt
export PATH=$PATH:$PWD//connectedhomeip/connectedhomeip/out/host
生成工厂分区二进制文件
```
./mfg_tool.py -n <count> -cn Espressif --paa -c /path/to/PAA_certificate -k /path/to/PAA_key \
              -cd /path/to/CD_file -v 0x131B --vendor_name Espressif -p 0x1234 \
              --product-name Test-light --hw-ver 1 --hw-ver-str v1.0
```
<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
注意

有关参数的详细信息，可以使用./mfg_tool.py --help

选项 （count） 是生成的二进制文件的数量。在上面的命令中，mfg_tool将生成 PAI 证书和密钥，然后使用它们生成不同的 DAC 和密钥。它将使用生成的证书和密钥生成具有不同 DAC、鉴别器和设置引脚码的工厂分区二进制文件。将出厂二进制文件刷新到设备的 NVS 分区。然后，设备将在调试期间将供应商的 PAI 证书和 DAC 发送给专员。-ncountcount
</div>

#### 2.2.3 在测试工具（TH）中使用供应商的PAA
手动测试（通过UI手册和验证步骤文档进行验证）

使用 chip-tool 配对设备进行手动测试时，应添加该选项。--paa-trust-store-path

cd path/to/connnectedhomeip/out/host/
./chip-tool pairing ble-wifi 0x7283 <ssid> <passphrase> <setup-pin-code> <discriminator> --paa-trust-store-path <paa-certificate-path>

<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
注意

pincode并且位于 /out/<vid>-<pid>/<UUID>/<uuid>-onb_codes.csv 中。discriminator

PAA 证书应使用 转换为 DER 格式并存储在 中。chip-certpaa-certificate-path
</div>

- 自动化测试（通过 UI-Automated 和 UI-SemiAutomated 验证）


以下是上传 PAA 证书并将其用于自动化测试的步骤：

启用用于芯片-工具配对的 PAA 证书
```
cd ~/chip-certification-tool
./scripts/stop.sh
./scripts/pi-setup/update-paa-certs.h
rm .env
./scripts/install-default-env.sh
echo "CHIP_TOOL_USE_PAA_CERTS=true" >> .env
./scripts/start.sh
```
将 PAA 证书复制到/var/paa-root-certs/
```
sudo cp /path/to/PAA_certificate.der /var/paa-root-certs/
```
运行自动芯片工具测试，并验证配对命令是否正在使用该选项。--paa-trust-store-path

### 2.3 Menuconfig 选项
请咨询工厂数据提供商，并相应地调整 menucofig 选项以进行认证测试。
## 3 Matter OTA镜像生成
如果产品支持 Matter 的 OTA 请求器功能，则应测试 OTA 软件更新的测试用例。因此，您需要提供用于 OTA 测试的图像以及降级的方法。

以下是生成 OTA 映像的两种方法。

### 3.1 使用 menuconfig 选项
启用 in 、 set 和 in ，并在项目的 CMakelists 中编辑 和 。构建示例，OTA 映像将生成在包含应用二进制文件的构建路径中。Generate Matter OTA image→ Component config → CHIP Device Layer → Matter OTA ImageDevice Vendor IdDevice Product Id→ Component config → CHIP Device Layer → Device Identification OptionsPROJECT_VERPROJECT_VER_NUMBER
<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
注意

必须始终是增量的。它必须高于要更新的固件的版本号。PROJECT_VER_NUMBER
</div>

### 3.2 使用ota_image_tool脚本
在使用脚本生成 OTA 映像时，我们还应该在项目的 CMakelists 中编辑 和 。PROJECT_VERPROJECT_VER_NUMBER

构建示例并生成 OTA 映像
```
cd path/to/example
idf.py build
cd path/to/esp_matter/connectedhomeip/connectedhomeip/src/app
./ota_image_tool.py create -v <vendor-id> -p <product-id> -vn 2 -vs v1.1 -da sha256 \
                           /path/to/original_app_bin /path/to/out_ota_bin
```
<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
注意

（version-number） 和 （version-string） 应与项目的 CMakelists 中的值匹配。-vn-vs
</div>


## 4 PICS文件
PICS 文件定义产品的 Matter 功能。授权测试提供商将根据提交的 PICS 文件确定要在 Matter 认证测试中测试的测试用例。

PICS 工具网站是用于打开、修改、验证和保存 XML PICS 文件的工具。参考 XML PICS 文件包括所有参考 PICS 文件，每个 XML 文件定义产品上一个或多个集群的功能。

打开包含产品所有集群的参考 PICS 文件，选择产品支持的功能。单击按钮 ，PICS 工具将验证所有 XML 文件，并生成要在 Matter 认证测试中测试的测试用例列表。Validate All

## 5 路由信息选项 （RIO） 注释
对于使用 LwIP 的 Wi-Fi 产品，应测试 TC-SC-4.9，以验证产品是否可以接收带有 RIO 的路由器通告 （RA） 消息，并添加路由表，指示是否可以通过路由器访问前缀。它可以使用定期发送 RA 消息的线程边界路由器 （BR） 和用于验证 Wi-Fi 产品是否可以通过 Thread BR 到达 Thread 网络的线程终端设备进行测试。某些 Wi-Fi 路由器可能会出现无法转发 Thread-BR 发送的 RA 消息的问题，因此在测试 TC-SC-4.9 时，请使用可以转发 RA 消息的 Wi-Fi 路由器。

以下是设置螺纹 BR 和螺纹终端设备的步骤。您应该准备 2 个无线电协处理器 （RCP） 来设置 ot-br-posix 和 ot-cli-posix。这里建议使用 ESP32-H2 上的 RCP。您还可以使用其他平台（例如 nrf52840、efr32 等）作为 RCP。

### 5.1 设置线程 BR
otbr-posix 可以在 RaspberryPi 或 Ubuntu 机器上运行。将 RCP 连接到主机时，它的端口将是 或 。RCP_PORT1/dev/ttyUSBX/dev/ttyACMX

- 在主机上构建 otbr-posix
```
git clone https://github.com/openthread/ot-br-posix
cd ot-br-posix
./script/bootstrap
./script/setup
```
然后，将构建 otbr-posix，并在主机上创建名为 otbr-agent 的服务。您可以禁用该服务并手动启动 otbr-posix。
```
sudo systemctl disable otbr-agent.service
sudo ./build/otbr/src/agent/otbr-agent -I wpan0 -B eth0 -v spinel+hdlc+uart://{RCP_PORT1}
```
在上面的命令中：

- wpan0是基础结构网络接口。将在主机上创建名为 wpan0 的网络接口作为线程网络接口。

- eth0是骨干网接口，始终是主机上的以太网或WiFi网络接口，请确保骨干网接口连接到Wi-Fi产品也连接的AP。

- RCP_PORT1是 Thread BR 的 RCP 端口。

otbr-posix 现在正在主机上运行。打开另一个终端，启动 otbr-posix 控制台，形成 Thread 网络，获取数据集。
```
sudo ot-ctl
> ifconfig up
> thread start
> dataset active -x
```
请记录您使用最后一个命令获得的数据集，otcli-posix 将在下一步使用它来加入 BR 的网络。

### 5.2 设置螺纹终端设备
我们使用 Posix 线程命令行界面 （CLI） 作为线程终端设备。将另一个 RCP 连接到主机并获取其端口RCP_PORT2。

在主机上构建 otcli
```
git clone --recursive https://github.com/openthread/openthread.git
cd openthread/
./script/bootstrap
./bootstrap
./script/cmake-build posix
./build/posix/src/posix/ot-cli 'spinel+hdlc+uart:///dev/{RCP_PORT2}?uart-baudrate=115200' -v
```

ot-cli 的控制台将启动。使用您在上述步骤中获得的数据集将 ot-cli 连接到 otbr 的 Thread 网络。
```
> dataset set active <PROVIDE THE DATASET OF THE BR THAT YOU NEED TO JOIN>
> dataset commit active
> ifconfig up
> thread start
> srp client autostart enable
```

在 ot-cli 控制台中，发现产品 IP 地址。
```
> dns service 177AC531F48BE736-0000000000000190 _matter._tcp.default.service.arpa.
DNS service resolution response for 177AC531F48BE736-0000000000000190 for service _matter._tcp.default.service.arpa.
Port:5540, Priority:0, Weight:0, TTL:6913
Host:72FF282E7739731F.default.service.arpa.
HostAddress:fd11:66:0:0:22ae:27fe:13ac:54df TTL:6915
TXT:[SII=35303030, SAI=333030, T=30] TTL:6913
```

<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
注意

177AC531F48BE736-0000000000000190可以用命令获取。 是结构 ID，也是节点 ID。avahi-browse -rt _matter._tcp177AC531F48BE7360000000000000190
</div>

Ping Wi-Fi 设备的 IP 地址。
```
> ping fd11:66:0:0:22ae:27fe:13ac:54df
16 bytes from fd11:66:0:0:22ae:27fe:13ac:54df : icmp_seq=2 hlim=64 time=14ms
1 packets transmitted, 1 packets received. Packet loss = 0.0%. Round-trip min/avg/max = 14/14.0/14 ms.
Done
```
ping 命令应该会成功。

## 6 固件/SDK配置说明
- Enable OTA Requestor在→ Component config → CHIP Core → System Options

- 用于启用 OTA 请求程序的选项。如果在 PICS 文件中选择了 OTA 请求程序功能，则应启用此选项。

- Enable Extended discovery Support在→ Component config → CHIP Device Layer → General Options如果选择了 PICS 选项，则应启用此选项。MCORE.DD.EXTENDED_DISCOVERY

- Enable Device type in commissionable node discovery在→ Component config → CHIP Device Layer → General Options如果选择了 PICS 选项，则应启用此选项。MCORE.SC.EXTENDED_DISCOVERY

- LOG_DEFAULT_LEVEL在→ Component config → Log output建议将 OnOff、LevelControl 和 ColorControl 集群的测试用例设置为 log level。这是相关问题。No output

## 7 附录常见问题
以下是您在 Matter 认证测试中可能遇到的一些问题以及针对这些问题的快速解决方案。

- TC-CNET-3.11

预计对步骤 7 没有响应（相关问题）。

步骤 17 可能会在提交 85abe2c 之前返回示例的 Timeout。您可以将 esp-matter 或 cherry-pick commit d7cd5aa 更新到 connectedhomeip 存储库。

所有 NetworkCommissioning 命令都是故障安全必需的。如果命令失败并显示状态代码。您需要发送命令，然后发送 NetworkCommissioning 命令。FAILSAFE_REQUIREDarm-fail-safe

- TC-SU-2.7

由于 OTA 重新启动时间太短，可能会错过 StateTransition 事件。您可以从修复拉取请求中挑选提交来修复问题。Applying