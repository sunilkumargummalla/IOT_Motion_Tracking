# Running Arduino with MQTT #


The purpose of this tutorial is to setup both publish and subscribe clients on arduino to shou 
how you can integrate sensors and controllers to MQTT.


## Prerequisites ##

You need an arduino development environment.  
There are many ide that can be used for aruino's but perhaps the fastest way is to use arduino.ide from [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software).
You could use arduino.ide online or download it to your windows, macos or linux machines for development.

The experiments for this document was made using arduino.cc on a MACOS laptop. 
The version that worked was 

```
Version: 2.0.2
Date: 2022-11-17T11:52:49.821Z
CLI Version: 0.29.0 [76251df9]

Copyright © 2022 Arduino SA
```
This version on macos needed to be updated before the serial line on USB started to work.

Add the libraries for ESP32 and ESP8266 by adding two packages into into

Arduinio IDE->prefernecs->Additional Boards Manager URLs 

```
http://arduino.esp8266.com/stable/package_esp8266com_index.json
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
```

Next install the acutal libraries:
using: 
Tools->boards:->BoardManager
Search for esp32 and install
search for esp8266 and install

This adds board info the esp32 and esp8266 MCU.

The experiments worked on "Generic esp8266" and "ESP32 Wrover kit" 

```
ARDUINIO IDE->peferences->Additional Boards Manager URLs
```

when creating the blink example sketch be sure to setup the board and serial line.



Use the blink examples to test the compiling and building and uploading.
For the ESP32,  fix the compile by adding:

```
int LED_BUILTIN = 2;
```

ESP8366 module already has a define for LED_BUILTIN

Adjust the serial line upload speed until the load works.

```
Tools -> Upload Speed  
```
for my experiments I used 
1. Generic ESP8266: Upload Speed =  11520
2. ESP32 Wrover Kit (all types): Upload Speed =  11520

Once you get the arduino upload working continue on to 
1. [MQTT test client](./mqtt_test_client.md)

