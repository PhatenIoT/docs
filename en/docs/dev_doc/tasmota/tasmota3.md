# Linking with Amazon Alexa
### 1. Configuring Tasmota Devices and MQTT
   In Configuration - Configure Other page in the webUI select emulation type
   
   ![Tasmota Configuration - Emulation Type](/assets/images/tasmota/tasmota_matter/2-1.png)

#### Belkin WeMo

   Belkin WeMo is suitable for devices with a single relay, while Hue Bridge is suitable for devices or fixtures with one or more relays.
   Tasmota devices will be discovered by the Alexa application. You do not need to install the Wemo app or enable the Wemo skill in Alexa.
   Just tell Alexa to discover the appropriate type of device (plug, switch, etc.).
   When asked for the brand of device, scroll to the end and select "Other".

#### Hue Bridge

   For lighting control, supports color control, on/off, and dimming.

   Enable Hue Bridge emulation and perform device discovery in the Alexa app. Alexa does not need to add any skills.

   Choose Hue Bridge V1 as the device type.

### 2. In Alexa, tell Alexa to discover devices. Alexa will search for Tasmota devices, supporting echo speaker voice control
   
   ![Alexa Device Discovery](/assets/images/tasmota/tasmota_matter/2-2.png)