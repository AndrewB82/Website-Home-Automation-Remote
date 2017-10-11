# Web Home Automation Remote
Web app for controlling different protocol based home devices in one place.

I am a hobby programmer, who learnt to write this project from a scratch. Half a year ago I did not know either what Raspberry Pi or Git is. Neither did I know JavaScript syntax at all as I had built my last (and only, laying WordPress experiments aside) website when there were still dinosaurs on Earth and HTML4 entered the scene on a white horse back in 1997. Therefore the project is nothing close to a clean code, it is just the result of my how-to-code learning curve steepening.

The idea of the project was to gather smart home device controllers in one place. All providers of smart home solutions provide GUI and/or smartphone/tablet app for controlling their products, some ofe them allow for 3rd party devices integration via various APIs. There are also open source home automation systems available like [Domoticz](http://domoticz.com) or [Home Assistant](http://home-assistant.io) that cover numerous devices, but I was not able a solution that served all devices I have at my place, or integrated all of them smoothly, so I decided to work on one myself. The result is simple GUI for controlling home devices, that were set up before in their native environments.

The app allows to control devices from devices in LAN. Communications that are covered:
- infrared via Logitech Harmony Hub,
- bluetooth, Sony Playstation 4 specifically via Logitech Harmony Hub,
- ISCP communication over LAN for ONKYO AVR,
- RF 433 mhz via RFXtrx433e transmitter connected to Raspberry Pi,
- z-wave via Fibaro Home Center 2 gateway,
- zigbee lighting via Philips Hue Bridge,
- camera live view and control over IP.

## Prerequisites

### Hardware
#### Controllers / Hubs / Gateways
The following devices are used in the project:
- Raspberry Pi - main hub of the project, host for the app as well as several servers listening for and processing commands,
- RFXtrx433E RF transceiver for RF 433 mhz communication (manual can be found in this repository),
- Logitech Harmony Hub - used for handling IR remotes and most commands for Sony PlayStation 4 (excluding Power On/Off functions which are covered in a different in a different way,
- Fibaro Home Center 2 gateway used for controlling z-wave based devices,
- Philips Hue bridge used for controlling Philips Hue and compatible Zigbee lighting,
- EXTRA: Amazon Echo Dot for providing voice commands for the whole system.
#### Devices controlled
- RF 433 mhz power strip that provides power for my home entertainment system,   
- RF 433 mhz smart socket providing power for air humifier,
- RF 433 mhz window blind motors with YOODA compatible DC306 remote (remote programming manual can be found in this repository),
- Philips Hue lighting: multiple bulbs and color spots grouped in lamps + Hue Go lamp,
- Zigbee lighting compatible with Philips Hue found on AliExpress, eg [here](https://www.aliexpress.com/item/Jiawen-Zigbee-bulb-smart-bulb-wireless-bulb-for-philip-hubs-control-by-Apple-homekit-Siri-and/32810632827.html?spm=2114.search0104.3.9.QIGuBQ&ws_ab_test=searchweb0_0,searchweb201602_4_10152_10065_10151_10068_10344_10345_10342_10343_10340_10341_10304_10307_10301_10060_10155_10154_10056_10055_10054_10059_10534_10533_10532_100031_10099_10338_10103_10102_5590020_10052_10053_10142_10107_10050_10051_10171_10084_10083_5370020_10080_10082_10081_10110_10111_10112_10113_10114_10312_10313_10314_10078_10079_10073,searchweb201603_17,ppcSwitch_2&btsid=48e6236d-6e4d-4715-ba0b-c557b9db3b5b&algo_expid=b62e7ced-8cac-4ea3-82b2-aed51b6f1fad-1&algo_pvid=b62e7ced-8cac-4ea3-82b2-aed51b6f1fad) - several bulbs grouped in lamp,
- z-wave Fibaro smart wall plug with table lamp connected,
- z-wave Fibaro RGBW controller with RGBW light strips connected,
- z-wave Danfoss thermostat,
- Sony Bravia TV KDL-40W5500 - only Power On/Off functions, as other operations are handled by AVR,
- ONKYO TX-NR616 AVR,
- UPC Mediabox - cable STB,
- WD TV Media Player,
- Sony Bravia TV KDL-40W5500,
- Sony PlayStation 4,
- Foscam FI9816P v. 2 IP camera.

### Software
The following software was used in the project and installed on Raspberry Pi:
- Raspbian Jessie OS,
- Domoticz Home Automation System,
- Node.js,
- Serialport Node module,
- Queue Node module,
- [RFXcom Node module](https://github.com/rfxcom/node-rfxcom) (deprecated, not used in current version) by and credited to Maxwell Hadley - @rfxcom,
- [PS4-waker Node module](https://github.com/dhleong/ps4-waker) by and credited to Daniel Leong - [@dhleong](https://github.com/dhleong),
- Apache2 web server,
- PHP5,
- PHP5 cURL,
- Python3 package,
- Python3-dev package,
- [ONKYO-eISCP package](https://github.com/miracle2k/onkyo-eiscp) by and credited to Michael Elsdörfer - [@miracle2k](https://github.com/miracle2k),
- [HA Bridge](https://github.com/bwssystems/ha-bridge) by and credited to BWS Systems - [@bwssystems](https://github.com/bwssystems),
- [RESTful Harmony API](https://github.com/bwssystems/restful-harmony) by and credited to BWS Systems - [@bwssystems](https://github.com/bwssystems),
- [PHP proxy script](https://github.com/cowboy/php-simple-proxy) by and credited to Ben Alman - [@cowboy](https://github.com/cowboy).
