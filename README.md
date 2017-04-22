# Home Automation

Configuration for [Home Assistant](https://home-assistant.io/).


## Network Architecture

![Network Diagram](https://jeffharrell.github.io/home-assistant-config/HomeNetworkDiagram.svg)

### Setup
- Synology NAS DS716+II
- Home Assistant
- Aoetec Z-Stick
- GE Smart Dimmer Z-Wave Lightswitches 
- Ecolink Z-Wave Sensor
- Ecobee 3 Smart Thermostat
- Wemo Insight
- Logitech Harmony Hub
- Amazon Alexa

### Principles

1. Devices should not be exposed directly to the internet and must remain behind a firewall
2. Devices should be able to communicate locally on the home network

### Security Considerations

1. As a security precaution, alarm status is read-only and cannot be set from the system
2. Additionally, home cameras are not tied into the system, but are available to access on the local network
