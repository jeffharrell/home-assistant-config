# Home Automation

After a fun project to automate my house over the last few years I finally feel like I've settled in a solution which works well. If you're just getting started with home automation I recommend you try out a soluton like [SmartThings](https://www.smartthings.com/) as it provides the complete package. If you're willing to dig a bit deeper and provide some elbow grease, read on.

## Principles 

Before I get started I want to call out a few principles I used to shape my setup. These come from lessons learned and a general sensitivity to network security:

1. **Keep communication local to the network.** While SmartThings and similar hubs are easy to set up, they often route their traffic through the open internet. This can cause a lag in responsiveness, but more importantly, I don't want other companies understanding my house usage patterns.

2. **Devices should look and behave like a normal device.** More of a personal preference, but I want my light switches and other devices to look and behave like normal light switches and I shouldn't be required to use my phone to turn something on.

3. **Security devices should be read only.** Fairly self explanatory, but any home alarm or cameras tied into the system should be read only and for automation purposes.


## Setup 

![Network Diagram](https://jeffharrell.github.io/home-assistant-config/HomeNetworkDiagram.svg)

`1` - My home network is controlled by the open source application [Home Assistant](https://home-assistant.io/). I explored a few other options like HABmin and Domoticz, but this is the one which worked for me. It has a vibrant open source community, frequent updates, and a good looking design for it's apps.

`2` - Home Assistant is running in a Docker container on a [Synology NAS DS716+II](https://www.amazon.com/Synology-DS716-II-Storage-DiskStation/dp/B01EMPW5Z6/). The NAS is not externally accessible from the internet and if you wish to connect to the NAS remotely you need to VPN into the local network.

`3`, `6` - The majority of my home network communicates over [Z-Wave](https://en.wikipedia.org/wiki/Z-Wave) through a [Aoetec Z-Stick](https://www.amazon.com/Aeotec-Aeon-Labs-ZW090-Stick/dp/B00X0AWA6E/) plugged into the Synology NAS. Z-Wave devices are low power devices which help me stick to the principle I mentioned of communication on my local network. Plus they tend to look and feel like normal devices so it helps with that as well.

- Light Switches: [GE Smart Dimmer Z-Wave Switches](https://www.amazon.com/gp/product/B006LQFHN2/) 
- Garage Door Sensors: [Ecolink Z-Wave Sensor](https://www.amazon.com/Ecolink-Intelligent-Technology-Operated-DWZWAVE2-ECO/dp/B00HPIYJWU/)
- Door Bell: [Aoetec Dry Contact Sensor](https://www.amazon.com/gp/product/B0155HSUUY/)


`4`, `5`

- Media Center: [Logitech Harmony Hub](https://www.amazon.com/Logitech-Harmony-Companion-Control-Entertainment/dp/B00N3RFC4G/)
- Thermostat: [Ecobee 3 Smart Thermostat](https://www.amazon.com/Ecobee3-Thermostat-Sensor-Generation-Amazon/dp/B00ZIRV39M/)
- Voice Input: [Amazon Echo Dot](https://www.amazon.com/All-New-Echo-Dot-2nd-Generation/dp/B01DFKC2SO/)
