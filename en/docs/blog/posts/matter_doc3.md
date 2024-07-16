---
date: 2024-07-06
categories:
  - matter
---

# Why Tech Giants are so Enthusiastic about Matter

Why are tech giants so enthusiastic about Matter? Let's start with what Matter can change <!-- more -->. If you purchase a Matter-certified product:

- This product can join any ecosystem that supports Matter, such as HomeKit, Google Home, Alexa, or other third-party ecosystems that support Matter. It can utilize all basic and advanced features of its ecosystem across different platforms.
- There's no need to purchase a gateway specific to each ecosystem; gateways from different ecosystems can manage products from other ecosystems. Devices like HomePod, Apple TV, Nest speakers, and even eero routers can serve as Matter gateways supporting all Matter devices.
- It can exchange data directly with any other brand's Matter products in your home, perform operations, or act as part of automation without the need for translation through a "gateway," significantly reducing latency and data exchange overhead across different communication protocols.
- It operates securely locally without needing to connect to any vendor's cloud services, enabling control, automation, and firmware updates within your home.
- It uses Wi-Fi, Ethernet, and Thread protocols, with Thread being the most advanced IoT communication protocol, offering extremely low response latency.
- It features a secure authentication process that is user-friendly for homes with multiple ecosystems and administrators.

We'll explain the specific technical details of these implementations in future articles. Matter aims to unify the IoT market from its inception and address pain points for all previous smart home users. It shifts manufacturers away from monopolistic competition in ecosystem construction towards a healthy competition focused on product strength and depth.

## Structure of Matter
Once we have a foundational understanding of what Matter can achieve, let's examine its structure:
![](../../assets/images/matter/Matter构成.png)

At the top layer, Matter represents the application layer. Below it are various communication protocols at the network and physical layers. This may be confusing for those unfamiliar, so let's explain what each represents.

At the top layer, Matter can be imagined as a language: the way smart homes communicate with each other. Any smart home using Matter can communicate smoothly without the need for a translator—a "gateway." TCP/UDP can be likened to different forms of mail and parcels, delivered by different postal methods, which correspond to various transmission technologies at the bottom layer—IPv6 delivering to each smart home's address. Further down, various network technologies can be seen as different delivery methods, which may differ in speed but ultimately deliver mail to the correct address.
