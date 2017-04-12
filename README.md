# Home Automation

Configuration for [Home Assistant](https://home-assistant.io/).


## Network Architecture

![Network Diagram](https://jeffharrell.github.io/home-assistant-config/HomeNetworkDiagram.svg)

### Principles

1. The home network devices should not be exposed directly to the internet and must remain behind a firewall


### Security Considerations

1. The home alarm status is read-only and cannot be set from the system
2. Home cameras are not tied into the system, but are available to access on the local network
