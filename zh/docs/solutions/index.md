---
title: 飞腾云 应用解决方案
---

## 飞腾云科技|Wi-Fi IOT模组|Wi-Fi IOT方案|Wi-Fi Matter方案
<!-- 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Grid Template</title>
<link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="grid-container" id="gridContainer">
         第一页格子 
        <div class="grid-item" onclick="window.location.href='/zh/solutions/8720df/vr_glasses_solution/';">
            <img src="../assets/images/fangan-tu/汽车VR.jpg" alt="Image 1">
            <h2>RTL 8720DF 5.8G 汽车VR数据透传 </h2>
            <p>本方案基于RTL8720DF 是双频Wi-Fi(2.4G+5G)和BLE5.0 的Soc 芯片。具有超低功耗、完整的加密策略和丰富的外设资源，相比与传统的2.4G 通讯具有低延迟，高传输速度，完全可以满足VR眼镜实时数据处理和低延迟的传输的要求。</p>
        </div>
        <div  class="grid-item" onclick="window.location.href='/zh/solutions/8720cf/rtl8720cf_solution/';">
            <img src="../assets/images/fangan-tu/Wi-Fi透传.jpg" alt="Image 2">
            <h2>RTL8720CF 通用透传应用</h2>
            <p>利用AT指令集通过WIFI网络实现数据透明传输的技术。这种方案广泛应用于物联网（IoT）设备，如智能家电、传感器网络等，它允许设备通过WIFI网络与其他设备或服务器进行通信，无需用户干预。</p>
        </div>
        <div class="grid-item" onclick="window.location.href='/zh/solutions/matter/socket1_5/';" >
            <img src="/assets/images/fangan-tu/插座2.jpg" alt="Image 2">
            <h2>Matter 1-5路 插座</h2>
            <p>可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome</p>
        </div>
        <div  class="grid-item" onclick="window.location.href='/zh/solutions/matter/rgbcw_light/';" >
            <img src="/assets/images/matter/5灯泡.png" alt="Image 2">
            <h2>Matter 5路 球灯泡</h2>
            <p>可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome</p>
        </div>
        <div  class="grid-item" onclick="window.location.href='/zh/solutions/matter/8720df_matter_socket/';">
            <img src="/assets/images/fangan-tu/插座3.jpg" alt="Image 2">
            <h2>8720DF Matter 1-5路 插座</h2>
            <p>可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome</p>
        </div>
        <div  class="grid-item" onclick="window.location.href='/zh/solutions/matter/8720df_matter_light/';">
            <img src="/assets/images/matter/5灯泡.png" alt="Image 2">
            <h2>8720DF Matter 5路 球灯泡</h2>
            <p>可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome</p>
        </div>
        <div  class="grid-item" onclick="window.location.href='/zh/solutions/tasmota/socket/';">
            <img src="/assets/images/fangan-tu/插座4.jpg" alt="Image 2">
            <h2>Tasmota 电量计量插座</h2>
            <p>便捷省事： 无需在官方购买拆卸、费时搞定硬件配置、定制化需求、提供预置固件 、完善的Tasmota功能支持</p>
        </div>
        <div  class="grid-item" onclick="window.location.href='/zh/solutions/tasmota/tasmota-matter/';">
            <img src="/assets/images/fangan-tu/插座3.jpg" alt="Image 2">
            <h2>Tasmota-Matter 计量插座</h2>
            <p>可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome</p>
        </div>
        <div  class="grid-item" onclick="window.location.href='/zh/solutions/tasmota/tasmota-matter-light/';">
            <img src="/assets/images/matter/5灯泡.png" alt="Image 2">
            <h2>Tasmota-Matter 5路灯</h2>
            <p>可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome</p>
        </div>
         其他格子根据需要添加 
    </div>
    <div class="pagination" id="pagination">
        <a href="#" id="page1"></a>
        <a href="#" id="page2"></a> 
        <a href="#">3</a> 
        根据需要添加更多页码
    </div>
    <script>
    document.addEventListener("DOMContentLoaded", function() {
        const gridContainer = document.getElementById('gridContainer');
        const pagination = document.getElementById('pagination');
        const items = gridContainer.querySelectorAll('.grid-item');
        const itemsPerPage = 6; // 每页显示的项数
        // 计算总页数
        const totalPages = Math.ceil(items.length / itemsPerPage);
        // 初始化，显示第一页，隐藏其余页的项
        let currentPage = 1;
        showPage(currentPage);
        // 创建分页链接
        for (let i = 1; i <= totalPages; i++) {
            const pageLink = document.createElement('a');
            pageLink.href = '#';
            pageLink.textContent = i;
            pageLink.addEventListener('click', function(event) {
                event.preventDefault();
                currentPage = i;
                showPage(currentPage);
            });
            pagination.appendChild(pageLink);
        }
        // 初始化当前页的页码样式
        pagination.querySelector(`a:nth-child(${currentPage})`).classList.add('active');
        // 显示指定页的项
        function showPage(pageNumber) {
            // 首先隐藏所有项
            items.forEach(function(item) {
                item.style.display = 'none';
            });
            // 计算当前页应该显示的项的索引范围
            const startIndex = (pageNumber - 1) * itemsPerPage;
            const endIndex = startIndex + itemsPerPage;
            // 显示当前页的项
            for (let i = startIndex; i < endIndex && i < items.length; i++) {
                items[i].style.display = 'block';
            }
            // 更新活动页码样式
            const pageLinks = pagination.querySelectorAll('a');
            pageLinks.forEach(function(link) {
                if (parseInt(link.textContent) === pageNumber) {
                    link.classList.add('active');
                } else {
                    link.classList.remove('active');
                }
            });
        }
    });
</script> 
</body>
</html>  -->


<div class="grid cards" markdown>

-   ![](../assets/images/fangan-tu/ESP-AT-fangan.png)

    **ESP-AT透传固件方案**

    它打破了技术壁垒，让开发者无需深陷底层硬件与通信协议的繁琐泥潭，即可快速搭建具备强大联网功能的物联网设备，极大缩短产品上市周期，助力抢占市场先机。

    [点击查看详情](../solutions/iot_passthrough/esp-AT.md)

-   ![](/assets/images/fangan-tu/AU316.png)

    **Wi-Fi 5.8G 7.1.2无线音响方案**

    WIFI 5.8G无线7.1.2音响应用方案凭借其卓越的性能和灵活的应用场景，必将为用户带来前所未有的音频体验。无论是音乐爱好者还是影音发烧友，都能在此方案中找到理想的解决方案。

    [点击查看详情](../solutions/speaker/index.md)

-   ![](/assets/images/fangan-tu/汽车VR.jpg)

    **RTL 8720DF 5.8G 汽车VR数据透传**

    本方案基于RTL8720DF 是双频Wi-Fi(2.4G+5G)和BLE5.0 的Soc 芯片。具有超低功耗、完整的加密策略和丰富的外设资源，相比与传统的2.4G 通讯具有低延迟，高传输速度，完全可以满足VR眼镜实时数据处理和低延迟的传输的要求。

    [点击查看详情](../solutions/8720df/vr_glasses_solution.md)

-   ![](/assets/images/fangan-tu/Wi-Fi透传.jpg)

    **RTL8720CF 通用透传应用**

    利用AT指令集通过WIFI网络实现数据透明传输的技术。这种方案广泛应用于物联网（IoT）设备，如智能家电、传感器网络等，它允许设备通过WIFI网络与其他设备或服务器进行通信，无需用户干预。

    [点击查看详情](../solutions/8720cf/rtl8720cf_solution.md)

-    ![](/assets/images/fangan-tu/插座2.jpg)
    **Matter 1-4路 插座**

    可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome

    [点击查看详情](../solutions/matter/socket1_5.md)

-   ![](/assets/images/fangan-tu/通断器.jpg)

    **Matter 通断器**

    可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome

    [点击查看详情](../solutions/matter/circuit_breaker.md)

-   ![](/assets/images/matter/5灯泡.png)

    **Matter 5路 球灯泡**

    可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome

    [点击查看详情](../solutions/matter/rgbcw_light.md)


-   ![](/assets/images/fangan-tu/插座3.jpg)

    **8720DF Matter 1-5路 插座**

    可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome

    [点击查看详情](../solutions/matter/8720df_matter_socket.md)

-   ![](/assets/images/matter/5灯泡.png)

    **8720DF Matter 5路 球灯泡**

    可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome

    [点击查看详情](../solutions/matter/8720df_matter_light.md)

-   ![](/assets/images/fangan-tu/插座4.jpg)
    
    **Tasmota 电量计量插座**

    便捷省事： 无需在官方购买拆卸、费时搞定硬件配置、定制化需求、提供预置固件 、完善的Tasmota功能支持

    [点击查看详情](../solutions/tasmota/socket.md)

-   ![](/assets/images/fangan-tu/插座3.jpg)
    
    **Tasmota-Matter 计量插座**

    可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome

    [点击查看详情](../solutions/tasmota/tasmota-matter.md)

-   ![](/assets/images/matter/5灯泡.png)

    **Tasmota-Matter 5路灯**

    可定制、有Matter认证证书、互联互通homekit、Alexa、GoogleHome

    [点击查看详情](../solutions/tasmota/tasmota-matter-light.md)


</div>

## 更多方案敬请期待🤩