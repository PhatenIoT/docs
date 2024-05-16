

# 编译
ESP82XX芯片上的闪存和存储空间是有限的，但非常有价值。正因为如此，我们的预编译二进制文件包括 Tasmota 最流行的功能，但没有一个版本可以包含所有这些功能。

要包含您需要的功能（或构建完全自定义的 Tasmota），您必须配置和编译自己的版本。

首先，您将需要 Tasmota 的源代码（开发或主分支）和一个编译工具。

## 编译工具
如果要修改代码或默认设置，可以使用：

PlatformIO - 设置和配置 PlatformIO 以进行 Tasmota 编译和上传
PlatformIO CLI - 如何在 Linux 上使用 PlatformIO 命令行界面刷新 Tasmota
PlatformIO-Core - 使用 PlatformIO-Core 和 esptool 闪存自动构建固件
Visual Studio Code - 使用 PlatformIO for Tasmota 设置和配置 Visual Studio Code
Docker Tasmota - 使用 PlatformIO 从 Docker 容器编译
### 在线编译器
_只能创建固件二进制文件。使用其中一个工具将其刷写到您的设备或尝试 Webserial ESPTool。

Gitpod - 使用 Gitpod 在云中编译您自己的二进制文件.
TasmoCompiler - 简单的 Web GUI，可使用您自己的设置编译 Tasmota
最简单的编译方法是使用 GitPod，只需要一个 Web 浏览器。

设置开发环境后，将源代码解压缩到文件夹中。

## 自定义您的构建
主要有 2 种可能的定制类型：

更改 Tasmota 首次在空白设备上运行时将使用的默认设置（闪存中没有先前的现有配置或闪存擦除）。这可以在任何变体上完成，因为它不会更改代码库、内存占用或所需的库。此类自定义包括：默认 Wi-Fi 设置、默认 MQTT 设置、包括 
```
.SetOption<x>
```

添加或删除功能。这基本上仅在基本 tasmota/tasmota32 环境中受支持）。其他变体已经过微调，尝试向它们添加/删除功能很可能会失败，Tasmota 开发团队将不提供支持。典型的失败是尝试向 添加传感器或向 添加显示器。正确的方法是将传感器和显示器都添加到 
```
.tasmota-displaytasmota-sensorstasmota
```
<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
请勿尝试向变体添加或删除功能，而只能添加或删除 tasmota 或 tasmota32
</div>

### 一般定制原则
在名为 的文件夹中创建一个新文件。您可以复制已经存在的示例文件，其中包括一些示例定义，用于在 Tasmota 固件中编码您自己的 Wifi、SSID 和密码。
```
/tasmotauser_config_override.huser_config_override_sample.h
```

在选定的开发环境中打开文件进行编辑。
<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
不要修改 my_user_config.h
</div>
强烈建议不要通过更改来自定义您的构建，因为如果您下载/克隆较新版本的 Tasmota 代码库，您在那里所做的更改将被覆盖。至少这会使任何合并变得复杂。仅在 中添加自定义配置。文件 my_user_config.h 是可用设置和功能的绝佳参考。my_user_config.huser_config_override.h

避免处理源代码文件的一个好方法是在 platformio_tasmota_cenv.ini 中传递 defined 作为标志。这需要一个特殊的字符串化，在常量值中使用转义双引号 （“ -> \\”），并用单引号换行。

```
>build_flags                 = ${env:tasmota32_base.build_flags}
>                              -DOTA_URL='""'
>                              '-DUSER_BACKLOG="so11 1; br load(\\"setup.be\\")"'
>
```

### 更改默认设置~
大多数默认设置都在 my_user_config.h 中定义，并附有说明和用于动态更改它的命令。例如：
```
#define WIFI_CONFIG_TOOL       WIFI_RETRY        // [WifiConfig] Default tool if Wi-Fi fails to connect (default option: 4 - WIFI_RETRY)
                                                 // (WIFI_RESTART, WIFI_MANAGER, WIFI_RETRY, WIFI_WAIT, WIFI_SERIAL, WIFI_MANAGER_RESET_ONLY)
                                                 // The configuration can be changed after first setup using WifiConfig 0, 2, 4, 5, 6 and 7.
#define WIFI_SCAN_AT_RESTART   false             // [SetOption56] Scan Wi-Fi network at restart for configured AP's
```
第一行显示 是与命令匹配的宏。如 WifiConfig 的文档所述，默认值为 （value ）。WIFI_CONFIG_TOOLWifiConfigWIFI_RETRY4
另一行显示默认值，默认值为 （或 ）。SetOption56falseOFF0

如果要在自己的二进制文件中覆盖其中的任何内容，请在 ：user_config_override.h
```
#ifdef %identifier%
#undef %identifier%
#endif
#define %identifier%   %the_new_value%
```

例：
```
#ifdef WIFI_CONFIG_TOOL
#undef WIFI_CONFIG_TOOL
#endif
#define WIFI_CONFIG_TOOL  WIFI_WAIT   // Change WifiConfig to wait (5)
```

### 启用功能tasmota
可以通过 #defining 匹配的宏来启用功能。可以通过 #undefining 相同的宏来禁用它。所有功能及其标识符都可以在 my_user_config.h 中找到。USE_featurename

启用功能的最佳做法是使用：
```
#ifndef %identifier%
#define %identifier%
#endif
```
禁用某项功能的最佳做法是使用：
```
#ifdef %identifier%
#undef %identifier%
#endif
```
如果要自定义的功能具有如下所示的值，例如： ，修改它的最佳做法是使用：#define WIFI_CONFIG_TOOL WIFI_WAIT
```
#ifdef %identifier%
#undef %identifier%
#endif
#define %identifier% %value
```


|指令	 | 描述 |
| ----- | -------- |
| #define %identifier% | 启用该功能 |
| #undef %identifier% |	禁用该功能 |
| #ifdef %identifier% |	检查是否在代码中定义了该功能 |
| #ifndef %identifier% | 检查是否未定义功能 |
| #endif |	关闭 #if 语句 |

<div style="border: 1px solid purple; border-radius: 15px; background-color: white; padding: 10px;">
<p>启用百叶窗和百叶窗支持</p>
```
#ifndef USE_SHUTTER
#define USE_SHUTTER             // Add Shutter support for up to 4 shutter with different motortypes (+6k code)
#endif
```
<p>标识符 =USE_SHUTTER</p>

<p>1. 检查是否已定义USE_SHUTTER如果尚未定义，请继续</p>
<p>2. 从 my_user_config.h 复制的这一行然后取消注释，告诉编译器包含 （#define） 快门支持</p>
<p>3. 关闭第 1 行的 IF 语句</p>
</div>

<p></p>

<div style="border: 1px solid purple; border-radius: 15px; background-color: white; padding: 10px;">
<p>禁用 Domoticz 支持</p>
```
#ifdef USE_DOMOTICZ
#undef USE_DOMOTICZ                              
#endif 
```
<p>标识符 =USE_DOMOTICZ</p>

<p>1. 检查是否已定义，如果已定义，请继续USE_DOMOTICZ</p>
<p>2. 告诉编译器删除 （#undef） Domoticz 支持</p>
<p>3. 关闭第 1 行的 IF 语句</p>
</div>

<p></p>

<div style="border: 1px solid orange; border-radius: 15px; background-color: white; padding: 10px;">
不建议改动，仅供参考my_user_config.h
</div>

保存文件，编译自定义二进制文件并刷新它

注意
可以包含的功能数量是有限制的！如果过火，代码可能由于功能冲突而无法编译，或者如果超过ESP8266限制，则可能无法刷新。

## 高级定制~
### USER_BACKLOG~
USER_BACKLOG允许在空白设备上首次运行二进制文件（闪存中没有设置）或使用 / 重置设置后自动执行一组命令。它应定义为以 分隔的命令列表。不需要任何命令。例如，它可以用于没有可更改默认值的设置。一个有趣的用法是在 / 之后从保存的配置文件自动重新配置设备。reset 1reset 2;Backlogreset 1reset 2
<div style="border: 1px solid purple; border-radius: 15px; background-color: white; padding: 10px;">
根据设备的 MAC 地址自动加载配置备份 （*.dmp） 文件

#define USER_BACKLOG "WebGetConfig http://myserver/tasmota/conf/%id%.dmp"
</div>
<p></p>

### USER_RULE~
如果需要在二进制文件中自动填充某些规则，可以定义 .USER_RULE<x>
```
#define USER_RULE1 "On Switch1#state DO publish cmnd/otherdevice/POWER %value% ENDON"
```

### 定义多个自定义固件~
您可能希望生成多个自定义固件，例如一个用于开关/继电器，一个用于传感器，其方式与 Tasmota 提供不同的二进制文件类似。这可以非常简单地实现。

1. 打开文件 。您可以在此处定义自己的二进制文件。 代表自定义环境，其中环境是要生成的特定二进制文件。platformio_tasmota_cenv.inicenv
2. 在您的中，您可以为每种类型的固件创建具有特定设置的部分。SSID 和 MQTT 可以在该部分之外，因此它们适用于每个二进制文件。user_config_override.h

#### 样本platformio_tasmota_cenv.ini
```
; *********************************************************************
[platformio]
; For best Gitpod performance remove the ";" in the next line. Needed 
; Platformio files are cached and installed at first run
;core_dir = .platformio

; *** Build/upload environment
default_envs =
; *** Uncomment the line(s) below to select version(s) that will be build
;     by default. Commented versions can still be build individually from
;     VSCode or command line
                tasmota-foo
                tasmota-bar
                tasmota32-foo
                tasmota32-grizzly

; *********************************************************************
; Common section can override global parameters for all builds
[common]

; *** Upload Serial reset method for Wemos and NodeMCU
upload_port               = COM4

; *********************************************************************
; This section show how to create 2 alternative binaries : tasmota-foo.bin
; and tasmota-bar.bin. Those binaries are derived form tasmota.bin and 
; customization is defined in user_config_override.h 
; Those binaries are for ESP8266
; The name after the env: tag will give its name to the binary
[env:tasmota-foo]
build_flags = ${env.build_flags} -DFIRMWARE_FOO

[env:tasmota-bar]
build_flags = ${env.build_flags} -DFIRMWARE_BAR

; *********************************************************************
; Similar example for ESP32
; Note that you must explicitly state that they derive from `tasmota32`
[env:tasmota32-foo]
extends = env:tasmota32_base
build_flags             = ${env:tasmota32_base.build_flags} -DFIRMWARE_FOO

[env:tasmota32-grizzly]
extends = env:tasmota32_base
build_flags             = ${env:tasmota32_base.build_flags} -DFIRMWARE_GRIZZLY
```

#### 样本user_config_override.h
```
#ifndef _USER_CONFIG_OVERRIDE_H_
#define _USER_CONFIG_OVERRIDE_H_

// force the compiler to show a warning to confirm that this file is included
#warning **** user_config_override.h: Using Settings from this File ****

// ***********************************************
// ** Global settings for all binaries ***********

// -- Setup your own Wifi settings  ---------------
#undef  STA_SSID1
#define STA_SSID1         "YourSSID"             // [Ssid1] Wifi SSID
#undef  STA_PASS1
#define STA_PASS1         "YourWifiPassword"     // [Password1] Wifi password

// You can also define your IP settings or your MQTT settings

// ***********************************************
// ** Firmware specific settings *****************

// -- Options for firmware tasmota-foo and tasmota32-foo ------
#ifdef FIRMWARE_FOO
    // This line will issue a warning during the build (yellow in 
    // VSCode) so you see which section is used
    #warning **** Build: FOO ****
    // -- CODE_IMAGE_STR is the name shown between brackets on the 
    //    Information page or in INFO MQTT messages
    #undef CODE_IMAGE_STR
    #define CODE_IMAGE_STR "foo"

    // Put here your override for firmware tasmota-foo
    #define USE_I2C
    #define USE_SENSOR_FOO  // Beware this doesn't exist !!!

#endif

// -- Options for firmware tasmota-bar ------
#ifdef FIRMWARE_BAR
    #warning **** Build: BAR ****
    #undef CODE_IMAGE_STR
    #define CODE_IMAGE_STR "bar"

    // Put here your override for firmware tasmota-bar

#endif

// -- Options for firmware tasmota32-grizzly ------
#ifdef FIRMWARE_GRIZZLY

    // If these settings are only for ESP32, you can check these
    // are used only when building for ESP32
    #ifndef ESP32
    #error *** This setup of for tasmota32 only ***
    #endif

    #warning **** Build: GRIZZLY ****
    #undef CODE_IMAGE_STR
    #define CODE_IMAGE_STR "grizzly"

    // Put here your override for firmware tasmota32-grizzly

#endif

#endif  // _USER_CONFIG_OVERRIDE_H_
```