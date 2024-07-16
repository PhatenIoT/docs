---
date: 2024-07-09
categories:
  - tasmota
---

# How to Set Up Tasmota?

Learn how to set up Tasmota devices here, with detailed steps for connecting your Tasmota device even with limited local resources.

<!-- more -->

## Preparation:

- (Optional, for Matter integration) Smart speaker devices supporting the Matter protocol (such as Apple, Alexa, or Google smart speakers).
- Ensure a stable network connection using Wi-Fi 2.4G.
- Enable Bluetooth, Wi-Fi, and location services on your mobile device.

## 1. Setting up Tasmota Device:

1. Power on the device for the first time or perform a reset.
   
2. On your smartphone, locate and connect to a Wi-Fi network named similar to `tasmota-6927C4-1988`.

3. Once connected, your phone may prompt that the network requires authentication and automatically redirect to a webpage.

   ![Image](/assets/images/tasmota/Tasmota连接1.PNG)

   If there's no automatic redirection, open a browser and enter `192.168.4.1` while connected to the Wi-Fi.

4. Choose your desired Wi-Fi network, enter the password, and click `Save`. If your preferred Wi-Fi network isn't displayed, click `Scan for all WiFi Networks` and select it again.

   ![Image](/assets/images/tasmota/Tasmota连接2.PNG)

5. Upon successful connection, the webpage will display the IP address for Tasmota's web control interface.

   ![Image](/assets/images/tasmota/Tasmota连接3.PNG)

6. Once connected, the webpage will close automatically, and the `tasmota-6927C4-1988` network name will disappear.
   **Ensure your smartphone remains connected to the same Wi-Fi network.**

7. Access the IP address `192.168.123.217` in your browser to view device information.

   ![Image](/assets/images/tasmota/Tasmota连接4.jpg)

## 2. Connecting to Matter:

After setting up Tasmota, the web interface will display a QR code.

![Image](/assets/images/tasmota/Tasmota连接5.PNG)

1. You can use the manual pairing code `3529-964-6346` to connect.

2. If the QR code is not fully visible due to UI issues, copy the code `MT:UHBA04QI14IBXZ0.M10` and generate a complete QR code using the following link:
   [Click Here](https://project-chip.github.io/connectedhomeip/qrcode.html?data=MT:UHBA04QI14IBXZ0.M10), and modify the parameters as needed.

Matter QR codes are valid for 10 minutes. After expiration, double-click the switch button to restart Matter pairing mode.

For more details on Matter connection procedures, refer to the article: "[Matter Smart Speaker Networking Guide](../../blog/posts/matter_networking.md)".
