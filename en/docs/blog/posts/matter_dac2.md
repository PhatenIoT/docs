---
date: 2024-07-17
categories:
  - matter
  - Matter DAC
---

# What's the Relationship Between Matter DAC and CD?

<!-- more -->
## What is DAC Logic?

In the Matter ecosystem (formerly known as CHIP), DAC typically refers to "Device Access Control," which ensures secure interoperability among smart home devices through various security and access management mechanisms.

Specifically, the logic of Matter DAC can be summarized as follows:

1. Authentication and Authorization:
   - Communication and interaction between devices must undergo authentication to ensure each device's identity is legitimate. This may involve using secure keys, digital certificates, or other security mechanisms to validate device identities.

2. Access Control and Permission Management:
   - Once a device's identity is authenticated, Matter DAC defines how to control access and operations between devices. This includes determining which devices are authorized to access others and the specific scope of access permissions.

3. Secure Communication and Data Protection:
   - DAC ensures secure communication between devices, typically achieved through encrypted channels and data integrity checks. This prevents data leaks, tampering, or unauthorized access.

4. Event and Permission Auditing:
   - DAC may include logging events and auditing permissions to track and monitor interactions between devices. This helps detect anomalous activities and maintain system security.

5. Security Management and Updates:
   - Finally, DAC may involve security management practices such as key management, security update strategies, and remote device management to ensure system-wide security throughout the lifecycle.

![](../../assets/images/安全图片.png)

Matter DAC logic ensures secure interoperability among smart home devices through multiple security mechanisms and management practices, enhancing device security and providing users with a reliable smart home experience.

## Relationship Between DAC and CD

Typically, the VID and PID in device DAC will match at least one value in the `vendor_id` and `product_id_array` included in device CD. These values must also match any VID and PID values included in PAI and PAA certificates. VID and PID must align with values contained in the BasicInformation Cluster. Therefore, provisioning nodes and the users of provisioning nodes will be able to certify the device is the device it claims to be and that it has CSA certification.

However, there is an exception. If the CD has an optional “original equipment” field (dac_origin_vendor_id and dac_origin_product_id fields), then those fields must match the VID and PID values in DAC, PAI, and PAA.

This optional feature allows one company to rename products made by another company.

DAC on a device can be installed at the time of manufacture without knowing which brand the product will have. Subsequently, the correct brand of CD can be installed on the device, which may be part of a device firmware update. The provisioning node will verify that the product complies with all rules clearly defined in the aforementioned specifications. Then all devices in a household can be certain the device has VID and PID contained in the Basic Information functional set and will use those values when communicating with the consumer.

![](../../assets/images/DAC证书流程.png)

<!-- ## Feiteng Cloud Can Provide You With A Complete DAC Service

![](../../assets/images/Matter设备ai.jpg) -->
