
### Challenge 1 : MQTT connection failing with RC -2

**Solution:** 
- Turn off all your firewall protection(McAfee) defending your laptop 
- Add `listener 1883` and `allow_anonymous true` in the MQTT broker configuration file(mosquitto.conf) and startup the mosquitto broker using the updated configuration file from the command line

```
C:\Program Files\mosquitto>mosquitto -c mosquitto.conf -v
```


### Challenge 2 : Arduino IDE not recognising the ESP32 DEV module port


**Solution:** Download the CP210 universal driver from the below link and update the driver in the device manager. Since the port is not recognised you can see the port under the unknown devices tab in device manager.

[https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers?tab=downloads](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers?tab=downloads)


### Challenge 3 : Unable to login to Grafana with default username and password

**Solution:** Grafana has some bug in its login webpage. The default credentails are Username : admin and Password: admin. However when yo try to sign in with the defaults credentials it throws an error saying **Error while signing in**. So I tweaked the config file to skip the initial login page by chnaging the below statements in the defaults.ini file.

```
[auth.anonymous]
enabled = true    // allow anonymous login
[auth]
disable_login_form = true // disable login form
```
Once you are in without login page. You can now sign in and change the default password from the welcome page.
