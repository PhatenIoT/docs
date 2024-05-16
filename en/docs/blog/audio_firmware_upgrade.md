
# Audio Firmware Upgrade Guide

This is a firmware upgrade guide for Windows environments; for other computer systems, please refer to the following links

For other computer systems, please refer to the following links:

https://www.xmos.com/documentation/XM-014926-PC-1/html/doc/programming_guide/tutorials/freertos/examples/dfu.html#dfu

[进上方链接](https://www.xmos.com/documentation/XM-014926-PC-1/html/doc/programming_guide/tutorials/freertos/examples/dfu.html#dfu)

必要条件：电脑环境必须是 Windows 7 及以上，越新越好

## 一 准备

Windows 下升级  需要如下工具：

1. Zadig
2. dfu-util

它们都可以通过[dfu-util官网](https://dfu-util.sourceforge.net)获取

## 二 下载 dfu-util 可执行文件

1、 进入官网，找到如下段落 中的 releases  点击可进入网页

![releases图片]()

2、 我已找好[点击进入releases 网页](https://dfu-util.sourceforge.net/releases/)

3、 找到如下文件：

dfu-util-0.11-binaries.tar.xz   

由于官方可能会更新，所以越往下的越新，请使用最新的版本即可

4、 一定要选择带 **binaries** 命名的二进制文件

5、 下载后直接解压两次，即可看到文件内容，请根据自己电脑配置，在具体选择，64位或32位

## 三 下载 Zadig

1、 进入官网，找到如下段落 中的  **libusb wiki** 点击可进入网页

![Zadig图片]()

2、 我已找好[点击进入libusb wiki 网页](https://github.com/libusb/libusb/wiki/Windows#How_to_use_libusb_on_Windows)

3、 进入网页后找到  [Zadig](https://zadig.akeo.ie/)

4、 进入后，在Download下，点击 Updated 2023.03.01下显示的[Zadig 2.8 (5.0 MB)](https://github.com/pbatard/libwdi/releases/download/v1.5.0/zadig-2.8.exe)

5、 点击上方蓝字可直接下载当前示例版本，如果后期更新，可更具我的步骤进入官网下载

## 四 升级固件

### 4.1 zadig设置

1、 升级固件前，请先将数据线连接正常。

2、 再打开的 Zadig 工具上 选择如图

![zadig设置图片]()

3、 点击图中的 Reinstall Driver 等待提示成功即可

### 4.2 通过 dfu-util 升级

1、 进入到 dfu-util 可执行文件的根目录 

如 C:Users\PC-01\Downloads\dfu-util-0.11-binaries.tar dfu-util-0.11-binaries\win64>

2、 输入命令 dfu-prefix.exe--version

3、 得到提示：就表示成功
    please report bugs to http://sourceforge.net/p/dfu-util/tickets/

4、 接下来将要升级的固件 复制到 此文件根目录下C:Users\PC-01\Downloads\dfu-util-0.11-binaries.tar dfu-util-0.11-binaries\win64>

5、 同样在此目录 输入命令：dfu-util -e -d 4000 -a 1 -D example_ffva_ua_adec_upgrade.bin

其中 example_ffva_ua_adec_upgrade.bin 是可以替换的内容，也是需要升级的固件名

运行后 **得到下面的提示，表示升级成功**

    dfu-util 0.11

    Copyright 2005-2009 Weston Schmidt, Harald Welte and OpenMoko Inc.
    Copyright 2010-2021 Tormod Volden and Stefan Schmidt
    This program is Free Software and has ABSOLUTELY NO WARRANTY
    Please report bugs to http://sourceforge.net/p/dfu-util/tickets/

    Warning: Invalid DFU suffix signature
    A valid DFU suffix will be required in a future dfu-util release
    Opening DFU capable USB device...
    Device ID 20b1:4001
    Run-Time device DFU version 0101
    Claiming USB DFU Interface...
    Setting Alternate Interface #1 ...
    Determining device status...
    DFU state(2) = dfuIDLE, status(0) = No error condition is present
    DFU mode device DFU version 0101
    Device returned transfer size 4096
    Copying data from PC to DFU device
    Download        [=========================] 100%       331776 bytes
    Download done.
    DFU state(7) = dfuMANIFEST, status(0) = No error condition is present
    DFU state(2) = dfuIDLE, status(0) = No error condition is present
    Done!