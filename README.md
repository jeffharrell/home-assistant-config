# Home Automation

Configuration files and setup instructions for my Home Assistant installation.


## Network Diagram

![Network Diagram](https://jeffharrell.github.io/home-assistant-config/HomeNetworkDiagram.svg)


### Hardware Used
- [Home Assistant](https://home-assistant.io/)
- [Synology NAS DS716+II](https://www.amazon.com/Synology-DS716-II-Storage-DiskStation/dp/B01EMPW5Z6/)
- [Aoetec Z-Stick](https://www.amazon.com/Aeotec-Aeon-Labs-ZW090-Stick/dp/B00X0AWA6E/)
- [GE Smart Dimmer Z-Wave Switches](https://www.amazon.com/gp/product/B006LQFHN2/) 
- [Ecolink Z-Wave Sensor](https://www.amazon.com/Ecolink-Intelligent-Technology-Operated-DWZWAVE2-ECO/dp/B00HPIYJWU/)
- [Aoetec Dry Contact Sensor](https://www.amazon.com/gp/product/B0155HSUUY/)
- [Ecobee 3 Smart Thermostat](https://www.amazon.com/Ecobee3-Thermostat-Sensor-Generation-Amazon/dp/B00ZIRV39M/)
- [Wemo Insight Switch](https://www.amazon.com/Insight-Switch-Control-Lights-Appliances/dp/B01DBXNYCS/)
- [Logitech Harmony Hub](https://www.amazon.com/Logitech-Harmony-Companion-Control-Entertainment/dp/B00N3RFC4G/)
- [Amazon Echo Dot](https://www.amazon.com/All-New-Echo-Dot-2nd-Generation/dp/B01DFKC2SO/)


### Setup

After a fun project to automate my house over the last few years I finally feel like I've settled in a solution which works well. If you're just getting started with home automation I recommend you try out a soluton like [SmartThings](https://www.smartthings.com/) as it provides the complete package. If you're willing to dig a bit deeper and provide some elbow grease, read on.

I want to call out a few principles I used to shape my setup. These come from lessons learned and a general sensitivity to network security:

1. **Devices should look and behave like a normal, non-automated device.** More of a personal preference, but I want my light switches and other devices to look and behave like normal light switches and I shouldn't be required to use my phone to turn something on.

2. **Devices must communicate over my local network.** While SmartThings and similar hubs are easy to set up, they often route their traffic through the open internet. This can cause a lag in responsiveness, but more importantly, I don't want other companies understanding my house usage patterns.

3. **Devices should not be exposed directly to the internet.** This is similar to the first, but read up on the latest [Dyn DNS attack](http://dyn.com/blog/dyn-analysis-summary-of-friday-october-21-attack/) if you're not familiar. IoT devices are not safe if exposed to the public internet. 


With those principles in mind, my home network is controlled by [Home Assistant](https://home-assistant.io/). This is an open source application which runs locally and, once configured, can communicate with a variety of devices. 

The application itself is running in a Docker container on my Synology NAS. This could be running on any computer from a Mac Mini to a Raspberry Pi. I'm simply using my NAS because it's low powered and is currently running my DVR and Plex servers locally. 

Out of the box, Home Assistant can easily communicate with any TCP-based device like my Echo Dot, [Harmony Hub](https://github.com/jeffharrell/home-assistant-config/blob/master/packages/media.yaml#L7-L9), and [Ecobee Thermostat](https://github.com/jeffharrell/home-assistant-config/blob/master/packages/climate.yaml#L29-L30). These can be connected just by enabling the platforms in your configuration. 

You'll notice that my light switches and sensors are all [z-wave](https://en.wikipedia.org/wiki/Z-Wave) based. Z-wave devices are low power devices which help me keep to the principles I mentioned of local network and normal look and feel. The NAS can't communicate with z-wave devices on it's own though, so I have a USB Aoetec Z-Stick plugged into it. With the Z-Stick, Home Assistant can be [configured](https://github.com/jeffharrell/home-assistant-config/blob/master/config/zwave.yaml#L3-L4) to communicate with the z-wave network. 


### Automation

### Security

1. As a security precaution, alarm status is read-only and cannot be set from the system
2. Additionally, home cameras are not tied into the system, but are available to access on the local network
