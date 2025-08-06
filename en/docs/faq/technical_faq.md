---
title: WiFi Audio + Bluetooth Module Technical FAQ
description: This document compiles common technical questions and answers about wireless WiFi modules and Bluetooth modules regarding infrared remote control, power consumption, chip architecture, TX/RX conversion, Bluetooth TWS, helping developers quickly locate and resolve issues.
keywords: 8711, wireless speakers, infrared remote control, module power consumption, WiFi BT chip, TX RX conversion, Bluetooth TWS, technical FAQ
---

--8<-- "common/phaten_xmos_support_img.md"

# WiFi Audio + Bluetooth Module Technical FAQ

## Q1: Does the module support infrared remote control decoding?

**Yes, infrared decoding functionality is supported.**

---

## Q2: Module power consumption during operation and standby

=== "Sleep Mode 1"
    - **Operating State**: Both TX/RX sleep, WiFi off, TX and RX BLE active
    - **Sleep Entry Methods**:
        - Application actively calls Sleep interface
        - Automatically enters when I2S data absence is detected for a period
    - **Wake-up Methods**:
        - UART/GPIO interrupt wakes TX → TX wakes RX
        - UART/GPIO interrupt wakes RX → RX wakes TX (bidirectional wake-up)
    - **Current Consumption**:
        - Unidirectional wake-up: TX ≤1mA, RX ≤3mA
        - Bidirectional wake-up: TX ≤3mA, RX ≤3mA
  
=== "Sleep Mode 2"
    - **Operating State**: TX WiFi doesn't sleep, RX WiFi sleeps, TX/RX BLE off
    - **Sleep Entry Methods**:
         - Application actively calls Sleep interface
         - Automatically enters when I2S data absence is detected for a period
    - **Wake-up Methods**:
        - Application calls playback interface (TX automatically wakes RX)
        - Automatically wakes RX when I2S data is detected
    - **Current Consumption**: RX ≤1mA

---

## Q3: Module WiFi and BT chip architecture

Single SOC chip integrating both WiFi and BT functionality.

---

## Q4: Online TX/RX conversion support

### Support Status:
- Supports online TX/RX conversion in WiFi mode
- BT mode limitations:
    - SOC only supports BLE5.0
    - Classic BT not supported
    - Cannot transmit audio via mobile phone Bluetooth

### Operating Mode Description:

=== "**TV Mode**:"
     - Transmitter box as WiFi TX
     - Receiver speakers as dual RX (left/right channels)

     ![TV Mode](/assets/images/faq/wifiaudio_bl/FCM362K_problem_4-1.png)

=== "**BT Mode**:"
     - Left speaker:
         - Receives mobile phone signal via BT
         - Simultaneously acts as WiFi TX transmitting to right speaker
     - Right speaker: Pure WiFi RX mode

     ![BT Mode](/assets/images/faq/wifiaudio_bl/FCM362K_problem_4-2.png)

---

## Q5: Bluetooth TWS functionality implementation

- **Does not support** native Bluetooth TWS functionality
- **Alternative Solution**:
  - Left speaker (with remote control receiver) acts as TX in BT mode
  - Transmits right channel to right speaker via TWS method
  - Right speaker (without remote control receiver) acts as RX receiving TWS signal

![TWS Solution](/assets/images/faq/wifiaudio_bl/FCM362K_problem_5.png)


## Q6: WiFi transmission related issues

### WiFi packet loss retransmission mechanism
**Q**: Does WiFi have packet loss retransmission, and how many retransmission attempts?

**A**: WiFi supports packet loss retransmission, but retransmission attempts only once. This design ensures fast response while avoiding excessive resource consumption.

### WiFi Alliance Certification
**Q**: Is there WiFi Alliance certification?

**A**: We generally assist customers with certification, and other customers already have relevant certification experience.

---

## Q7: Sleep and wake-up related issues

### Individual sleep wake-up time
**Q**: What is the wake-up time when TX/RX individually enters sleep?

**A**:

- System sleep wake-up speed is typically less than 100ms
- Practical application approach:
    - TX turns off
    - RX enters sleep and performs BLE scanning
    - TX power consumption: <11mA
    - RX power consumption: approximately 15mA (mainly caused by BLE scanning)

### Sleep wake-up while maintaining connection
**Q**: What is the wake-up time when TX and RX maintain connection during sleep wake-up?

**A**:

- TX as AP (Access Point) cannot enter sleep, must remain active to maintain connection
- Only RX can enter sleep
- Wake-up speed is typically less than 100ms

---

## Q8: Pairing and transmission related issues

### Pairing time influencing factors
**Q**: Is the pairing time between TX and RX related to distance?

**A**: Pairing time is not related to distance, mainly depends on hardware and protocol configuration.

### Transmission stability
**Q**: What is the stability when two routers transmit at full bandwidth?

**A**:

- No noise or disconnection occurs when TX/RX are 30cm apart
- Stable connection can be achieved within 2 meters transmission distance
- Environmental factors must be considered (signal interference, device quality, etc.)

---

## Q9: Audio processing related issues

### Electronic crossover
**Q**: What is the concept of electronic crossover?

**A**:

- Active crossover: Tweeter and woofer driven by independent amplifiers
- Full-range: Tweeter and woofer to the same amplifier output

### RX reception frequency
**Q**: Is RX reception full-range?

**A**:

- RX receives full-range signals
- Crossover processing:
    - Can be implemented through software calculation
    - Can be processed by backend DSP
    - Processing solution needs to be selected based on software computing power
    - Professional speakers handle audio effects processing through DSP

### Audio channel power
**Q**: How is the power of FL, FR and other channels determined?

**A**:

- Must be determined based on amplifier power and speaker performance
- Reference configuration:
    - Tweeter: Maximum power 25W×7
    - Woofer: Power 60W×2
- Can be designed according to actual requirements and device parameters

### Audio Output Format Support
**Q**: Can PDM output be used? Is it possible to use I2S for all 10 channels?

**A**:

- All channels use I2S output method
- PDM output format is not supported
- Using I2S output for all 10 channels is possible

### Multi-channel Support Capability
**Q**: How many channels can be supported maximum when each RX is at 96kHz?

**A**:

- At 96kHz sampling rate, 4-6 channels can be supported
- The specific number of channels depends on system load and processing capacity
- Testing and verification based on actual application requirements is recommended

---

## Q10: Data format and hardware issues

### I2S data format
**Q**: The I2S data output by TX is in PCM format, does it need decoding?

**A**:

- TX output is in PCM format, no decoding required
- RX directly passes signal to amplifier
- Audio processing (crossover, equalization, etc.) is performed at software level
- Processing solution needs to match amplifier and speaker power requirements


<!-- Structured data markup -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Does the module support infrared remote control decoding?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes, infrared decoding functionality is supported."
      }
    },
    {
      "@type": "Question",
      "name": "Module power consumption during operation and standby?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Sleep Mode 1: Both TX/RX sleep, WiFi off, TX and RX BLE active, unidirectional wake-up TX≤1mA, RX≤3mA, bidirectional wake-up TX≤3mA, RX≤3mA. Sleep Mode 2: TX WiFi doesn't sleep, RX WiFi sleeps, TX/RX BLE off, RX≤1mA."
      }
    },
    {
      "@type": "Question",
      "name": "Module WiFi and BT chip architecture?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Single SOC chip integrating both WiFi and BT functionality."
      }
    },
    {
      "@type": "Question",
      "name": "Online TX/RX conversion support?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Supports online TX/RX conversion in WiFi mode, BT mode only supports BLE5.0, Classic BT not supported, cannot transmit audio via mobile phone Bluetooth."
      }
    },
    {
      "@type": "Question",
      "name": "How to implement Bluetooth TWS functionality?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Does not support native Bluetooth TWS functionality, can be implemented through left speaker acting as TX in BT mode, transmitting right channel to right speaker via TWS method."
      }
    }
  ]
}
</script>