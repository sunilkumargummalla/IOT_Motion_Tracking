## MQTT setup Tutorial

MQTT is an OASIS standard messaging protocol for the Internet of Things (IoT). It is designed as an extremely lightweight publish/subscribe messaging transport that is ideal for connecting remote devices with a small code footprint and minimal network bandwidth. MQTT today is used in a wide variety of industries, such as automotive, manufacturing, telecommunications, oil and gas, etc.

### Installation
Download the suitable MQTT broker from [https://www.mosquitto.org/download/](https://www.mosquitto.org/download/) and install it on your PC/Laptop.


### Tweaking the Configuration files
For the lastest mosquitto servers you need to tweek the config files to allow for external access.
To listen on addresses other than localhost, you need to have a config file with 
a "listener" line plus some authentication option. At its most wide-open, 
you could have:

```
listener 1883
allow_anonymous true
```
By default the mosquitto broker runs on port **1883**, but it can be modified inside _C:\Program Files\mosquitto\mosquitto.conf_
MQTT connection can be blocked by firewalls. So temporarily turn off the all firewall protection(McAfee) on your laptop.

### Startup
To starup the MQTT service, open the command prompt and run the command `mosquitto -c mosquitto.conf -v`



