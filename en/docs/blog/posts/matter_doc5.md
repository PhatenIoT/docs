---
date: 2024-08-15

categories:
  - matter

---

# How to Perform OTA Upgrades for Matter?

<!-- more -->
## 1. Generating the OTA Firmware Upgrade Package

### 1.1 Change the OTA Firmware Version Number to 3

![](/assets/images/1-matterota.png)

### 1.2 Compile to Generate MatterLightOverThread_V3.ota

Rename the compiled MatterLightOverThread.s37 firmware to MatterLightOverThread_V3.s37 and copy it to the following Windows folder:

```
C:\SiliconLabs\SimplicityStudio\v5\developer\adapter_packs\commander
```

Convert it to a .gbl file:

```
commander gbl create ./MatterLightOverThread_V3.gbl --app ./MatterLightOverThread_V3.s37 --compress lzma
```

Copy MatterLightOverThread_V3.gbl to the VM VirtualBox shared folder, import the .gbl file into the Ubuntu environment, and then copy it to the matter folder.

![](../../assets/images/2-matterota.png)

Convert the .gbl file to a .ota file:

```
./src/app/ota_image_tool.py create -v 0xFFF1 -p 0x8005 -vn 3 -vs "0.3" -da sha256 MatterLightOverThread_V3.gbl MatterLightOverThread_V3.ota
```

![](../../assets/images/3-matterota.png)

## 2. Upgrading Matter Firmware in the Ubuntu Environment

### 2.1 Compile the OTA Upgrade Program

```
./scripts/examples/gn_build_example.sh ./examples/ota-provider-app/linux ./out/debug chip_config_network_layer_ble=false
```

![](../../assets/images/4-matterota.png)
![](../../assets/images/5-matterota.png)

### 2.2 Configure the Matter Device

```
# Clear the chip tool cache. After clearing the cache, both the OTA Provider and the Matter device need to rejoin the network.
sudo rm -r /tmp/chip_*

# Create a Thread network
sudo ot-ctl dataset init new
sudo ot-ctl dataset networkkey 00112233445566778899aabbccddeeff
sudo ot-ctl dataset extpanid 1111111122222222
sudo ot-ctl dataset panid 0x1234
sudo ot-ctl dataset channel 15
# Submit the above configuration as the active configuration
sudo ot-ctl dataset commit active
# Bring up the IPv6 interface
sudo ot-ctl ifconfig up
# Start the Thread protocol
sudo ot-ctl thread start
# View Thread network configuration
sudo ot-ctl dataset active -x
# Assign a node ID of 1001 to the device
sudo ./chip-tool pairing ble-thread 1001 hex:0e08000000000001000035060004001fffe00708fdd0a609c458d59b030f4f70656e5468726561642d3763393004100191ed136516065cfa503db5ed6439320c0402a0f7f8051000112233445566778899aabbccddeeff0208111111112222222201021234000300000f 20202021 3840
```

Start the OTA service in a new terminal window, pointing to the OTA file:
```
sudo ./out/debug/chip-ota-provider-app -f MatterLightOverThread_V3.ota
```

In a new terminal window, assign a node ID of 5678 to the OTA Provider:
```
sudo ./chip-tool pairing onnetwork 5678 20202021
```

Grant all devices in the network access to the OTA Provider cluster (0x0029). 5678 is the node ID of the OTA Provider, and the following 0 is the endpoint.
```
sudo ./chip-tool accesscontrol write acl '[{"fabricIndex": 1, "privilege": 5, "authMode": 2, "subjects": [112233], "targets": null}, {"fabricIndex": 1, "privilege": 3, "authMode": 2, "subjects": null, "targets": null}]' 5678 0
```

Notify the Matter device to upgrade. 5678 is the node ID of the OTA Provider, and 1001 is the node ID of the Matter Lighting.
```
sudo ./chip-tool otasoftwareupdaterequestor announce-otaprovider 5678 0 0 0 1001 0
```

You should see in another window that the OTA upgrade process has begun.

![](../../assets/images/6-matterota.png)

The Matter device will request and update the firmware from the OTA Provider after receiving the announce-otaprovider command.

The firmware upgrade process will take a few minutes…

Copyright Notice: This article is an original work by Zhang Chi Youdu 2016.

Original link: https://blog.csdn.net/zl374216459/article/details/131223300