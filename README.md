# Home Automation

A few years ago I started a project to automate my house and have finally settled on a solution which works for me. If you're just getting started with home automation I recommend you try out something like [SmartThings](https://www.smartthings.com/) or [Wink](https://www.wink.com/) as they provide a complete package. If you're willing to dig a bit deeper and roll up your sleeves, read on.


## Principles 

Before I get started I want to call out a few concepts I used in my setup:

1. **Keep communication local to the network.** While SmartThings and similar hubs are easy to set up they typically achieve that by routing their traffic through the open internet to their servers. This can cause a lag in responsiveness, but more importantly, it means those servers get your data and can understand your home usage patterns. No thanks.

2. **Devices should look and behave like a normal device.** More of a personal preference here, but I want my light switches to look and behave like normal light switches. That applies to every household device. I shouldn't be required to use my phone to turn something on and vistors shouldn't notice that anything is out of the ordinary.


## Setup 

![Network Diagram](https://jeffharrell.github.io/home-assistant-config/HomeNetworkDiagram.svg)

`1` – My home network is controlled by the open source application [Home Assistant](https://home-assistant.io/). Other options were explored like SmartThings, HABmin, and Domoticz, but this is the one which worked for me. It has a vibrant open source community, frequent updates, is highly customizable, and a good looking design for it's apps.

`2` – Home Assistant is running in a Docker container on a [Synology NAS DS716+II](https://www.amazon.com/Synology-DS716-II-Storage-DiskStation/dp/B01EMPW5Z6/). The NAS is not externally accessible from the internet and if you wish to connect to it remotely you need to VPN into the local network. Internal to the local network all traffic is served over SSL.

`3`, `6` – The majority of my home network communicates over [Z-Wave](https://en.wikipedia.org/wiki/Z-Wave) through an [Aoetec Z-Stick](https://www.amazon.com/Aeotec-Aeon-Labs-ZW090-Stick/dp/B00X0AWA6E/) plugged into the Synology NAS. Z-Wave devices are low power and help me stick to the principle of communication on my local network. Plus, they tend to look and feel like normal devices.

- **Light Switches:** All light switches are wired up with [GE Smart Dimmer Z-Wave Switches](https://www.amazon.com/gp/product/B006LQFHN2/). The dimmer switches are a little more flexible than standard switches and can be customized through the Z-Wave parameters to either not dim or dim slower/faster.

- **House Fan:** The house fan is controlled using a [GE Z-Wave Receptacle Outlet](https://www.amazon.com/gp/product/B0013V1SRY). Instant on / off capability.

- **Garage Door Sensors:** ~The door sensors are using [Ecolink Z-Wave Sensors](https://www.amazon.com/Ecolink-Intelligent-Technology-Operated-DWZWAVE2-ECO/dp/B00HPIYJWU/). I'm a little obsessive about if I left my garage door open so these help a lot, but can be a little flakey sometimes and report open. I need to fix their placement.~ The door sensors have been replaced with [Z-wave Garage Door Tilt Sensors](https://www.amazon.com/gp/product/B01MRZB0NT/) which are more reliable.

- **Doorbell:** This was a fun one. I found out about dry contact sensors and ended up using an [Aoetec Dry Contact Sensor](https://www.amazon.com/gp/product/B0155HSUUY/) with a magnetic relay switch that's connected to my existing doorbell magnet. This causes it to trigger a Z-Wave event when rung. Win!


`4`, `5` – The remainder of the devices communicate over some form of HTTP/TCP/MQTT. 

- **Media Center:** If you're in the market for a smart remote then the [Logitech Harmony Hub](https://www.amazon.com/Logitech-Harmony-Companion-Control-Entertainment/dp/B00N3RFC4G/) is great. Plus, it can be controlled locally through Home Assistant.

- **Thermostat:** I opted to go with a [Ecobee 3 Smart Thermostat](https://www.amazon.com/Ecobee3-Thermostat-Sensor-Generation-Amazon/dp/B00ZIRV39M/) since it can use occupancy and room sensors.

- **Voice Input:** [Amazon Echo Dot](https://www.amazon.com/All-New-Echo-Dot-2nd-Generation/dp/B01DFKC2SO/) is connected into the system and able to control all of the devices.

- **Weather:** [Dark Sky](https://darksky.net/) is used for outside weather and tied into automations.


`7` – [Plex](https://www.plex.tv/) is used to stream movies locally. It will be connected into the Home Assistant instance eventually.


`8`- [Channels DVR](https://community.getchannels.com/dvr) is used to record TV shows. It will be connected into the Home Assistant instance eventually.
