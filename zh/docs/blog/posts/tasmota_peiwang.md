---
date: 2024-07-09
categories:
  - tasmota
---

# Tasmota 如何配网？

Tasmota 设备如何配网？在国内资源缺乏的情况下，这里为您详细解释如何连接Tasmota设备的
<!-- more -->

## 准备:

- （可选，连接Matter才用）支持 Matter 协议的智能音箱设备（如苹果音箱、Alexa音箱、Google音箱）。
- 确保网络畅通，使用 Wi-Fi 2.4G。
- 打开手机蓝牙、Wi-Fi、定位。

## 一、设备tasmota配网:

1. 初次通电设备或重置设备。

2. 打开手机，在 Wi-Fi 中找到类似 tasmota-6927C4-1988 的 Wi-Fi 名称，并连接。

3. 连接上网络后，手机提示网络需要认证，自动跳转网页。

   ![图片](/assets/images/tasmota/Tasmota连接1.PNG)

   若没有自动跳转，可以在连接该 Wi-Fi 时，在浏览器输入 192.168.4.1 进入网页。

4. 选择要连接的 Wi-Fi，输入密码后点击 Save；若未显示想要连接的 Wi-Fi，请点击 “Scan for all WiFi Networks” 再次选择。

   ![图片](/assets/images/tasmota/Tasmota连接2.PNG)

5. 连接成功后，显示 Tasmota 的网页控制端 IP。

   ![图片](/assets/images/tasmota/Tasmota连接3.PNG)

6. 成功连接后，网页将自动关闭，tasmota-6927C4-1988 网络名称也会消失。
**请再确保手机继续连接到相同的 Wi-Fi。**

7. 在浏览器中访问 IP： 192.168.123.217，查看设备信息。

   ![图片](/assets/images/tasmota/Tasmota连接4.jpg)

## 二、连接 Matter:

连接好 Tasmota 后，网页端将显示二维码信息。

![图片](/assets/images/tasmota/Tasmota连接5.PNG)

1. 可使用手动配对码：3529-964-6346 连接。

2. 若二维码显示不全，可能是UI界面显示问题。复制编码 MT:UHBA04QI14IBXZ0.M10 到以下网址生成完整的二维码：
   [点击进入](https://project-chip.github.io/connectedhomeip/qrcode.html?data=MT:UHBA04QI14IBXZ0.M10)，修改后面的参数即可。

Matter 二维码信息每次有效期为 10 分钟。过期后，双击开关按钮可重新开启 Matter 配网模式。

更多关于 Matter 连接操作的信息，请参考文章：“[Matter 音响-配网说明](../../blog/posts/matter_networking.md)”。
