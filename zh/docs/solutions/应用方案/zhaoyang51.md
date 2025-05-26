---
title: WiFi 5.8G家庭影院无线连接方案
hide:
    -toc
---

--8<-- "common/phaten_xmos_support_img.md"

# WiFi 5.8G家庭影院无线连接方案

__基于WiFi 5.8G技术的无线家庭影院解决方案，支持5.1声道音频传输__

<div class="result" markdown>
<!-- ![方案效果图](/assets/images/solutions/wifi_51_solution.png "WiFi 5.8G家庭影院解决方案"){align=right width=235} -->

## 方案概述

WiFi 5.8G家庭影院无线连接方案是一套完整的无线音频传输解决方案，专为现代家庭影院系统设计。该方案采用WiFi 5.8G技术，实现Soundbar主系统与后置环绕音箱及低音炮的无线连接，最高支持10个声道音频数据传输。通过创新的无线传输技术，为用户带来便捷、高品质的沉浸式音频体验。

本方案兼容5.1、3.1、2.1等多种场景配置，满足不同用户的需求，特别适合追求高品质家庭影院体验的音乐爱好者和影音发烧友。

</div>

## 方案亮点

<div class="grid cards" markdown>

-   :material-wifi: __高速无线传输__

    ---

    采用WiFi 5.8G技术，确保稳定可靠的音频传输
    
    * 支持最高10声道音频数据传输
    * 低延迟，高保真音频传输
    * 抗干扰能力强
    * 传输距离远

-   :material-speaker-multiple: __灵活的系统配置__

    ---

    支持多种声道配置，满足不同场景需求
    
    * 5.1声道标准配置
    * 3.1声道紧凑配置
    * 2.1声道简约配置
    * 可扩展至7.1.2声道

-   :material-music-note: __高品质音频规格__

    ---

    支持多种高解析度音频格式
    
    * PCM 最高192kHz/24bit
    * 无损音频传输
    * 低延迟音频处理
    * 动态范围优化

-   :material-connection: __便捷的连接方式__

    ---

    * 支持WiFi 5.8G无线连接
    * 支持蓝牙连接
    * 支持HDMI ARC输入
    * 支持光纤/同轴输入

</div>

## 应用实例

=== "标准5.1无线家庭影院应用"

    标准的5.1声道家庭影院应用，自动连接，断电回连。

    采用方式：

    -  1、采用[a316_hf_i2s_v1](https://phaten-audio.com/zh/products/evb/a316_hf_i2s_v1/)与[8711开发板](https://phateniot.github.io/zh/products/dev_board/RTL8711dev_board/)。
    -  2、采用[a316_hf_dac_v1](https://phaten-audio.com/zh/products/evb/a316_hf_dac_v1/)与[8711开发板](https://phateniot.github.io/zh/products/dev_board/RTL8711dev_board/)。

    ### 相关资源
    | 类型 | 标题                      | 下载                                                                                            |
    | ---- | ------------------------- | ----------------------------------------------------------------------------------------------- |
    | 固件 | 5.1标准固件     | [:octicons-arrow-right-24: 下载](../../assets/download/firmware/application_5.1/5.1_standard_firmware_0.1_20250514..7z)|
    | 文档  | 8711开发板连接设计说明   | [:octicons-arrow-right-24: 查看](../../services_support/audio/shaolu.md)                     |
    | 文档 | 套装5.1标准调试硬件连接说明 | [:octicons-arrow-right-24: 查看](../../dev_doc/hifi_audio/a316_1926v1/A316-8711-5.1解码无线音频套装制作说明.md)                |
    | 文档  | 电脑音频设备声道&属性设置   | [:octicons-arrow-right-24: 查看](../../services_support/audio/used.md)                     |
    
=== "标准5.1无线功放音响应用"

    标准的5.1声道功放音响应用，额外加入数据透传功能，可自定义更多功能

    -  采用[a316_hf_i2s_v1](https://phaten-audio.com/zh/products/evb/a316_hf_i2s_v1/)与[8711开发板](https://phateniot.github.io/zh/products/dev_board/RTL8711dev_board/)。
    -  采用[a316_hf_dac_v1](https://phaten-audio.com/zh/products/evb/a316_hf_dac_v1/)与[8711开发板](https://phateniot.github.io/zh/products/dev_board/RTL8711dev_board/)。

    ### 相关资源
    | 类型 | 标题                      | 下载                                                                                            |
    | ---- | ------------------------- | ----------------------------------------------------------------------------------------------- |
    | 固件 | 5.1标准带透传固件     | [:octicons-arrow-right-24: 下载](../../assets/download/firmware/application_5.1/5.1_tc_firmware.7z) |
    | 文档  | 8711开发板连接设计说明   | [:octicons-arrow-right-24: 查看](../../services_support/audio/shaolu.md)                     |
    | 文档 | 套装5.1标准调试硬件连接说明 | [:octicons-arrow-right-24: 查看](../../dev_doc/hifi_audio/a316_1926v1/A316-8711-5.1解码无线音频套装制作说明.md)                |
    | 文档  | 电脑音频设备声道&属性设置   | [:octicons-arrow-right-24: 查看](../../services_support/audio/used.md)                     |

<!-- === "标准3.1无线家庭影院应用"

    标准的3.1声道家庭影院应用，采用USB接口，可外接不同USB设备。

    采用8730E与8711开发板，实现3.1声道家庭影院的应用。

    ### 相关资源
    | 类型 | 标题                      | 下载                                                                                            |
    | ---- | ------------------------- | ----------------------------------------------------------------------------------------------- |
    | 固件 | 3.1标准固件     | [:octicons-arrow-right-24: 下载](../../assets/download/firmware/application_5.1/3.1_standard_firmware.7z) |
    | 文档  | 8711开发板连接设计说明   | [:octicons-arrow-right-24: 查看](../../services_support/audio/shaolu.md)                     |            |
    | 文档  | OTA使用说明   | [:octicons-arrow-right-24: 查看](../../services_support/audio/OTA升级dongle-8711工具使用说明.md)                     | -->