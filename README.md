# esp-usb-light
Turning on/off NY USB light with esp-01 board, ESPHome and Home Assistant

## Scheme
 
![SCHEME](https://github.com/eulampy/esp-usb-light/blob/main/Schematic.png)

## ESPHome config file

```yaml
esphome:
  name: $devicename
  platform: ESP8266
  board: esp01_1m

substitutions:
  devicename: esp_01_1

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password

  manual_ip:
    static_ip: 10.10.10.68
    gateway: 10.10.10.10
    subnet: 255.255.255.0

# Enable logging
logger:

# Enable Home Assistant API
api:
  password: !secret ha_api_password

ota:

web_server:
  port: 80

#вывод GPIO2
switch:
  - platform: gpio
    name: ${devicename} output
    pin: GPIO2
    icon: "mdi:string-lights"
    restore_mode: ALWAYS_OFF
```
