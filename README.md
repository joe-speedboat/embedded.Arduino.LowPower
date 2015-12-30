HowTo build Low Power Arduino 1MHz
===================================

Buy:
* USB to TTL Adapter
*  http://www.aliexpress.com/item/USB-to-TTL-UART-Module-CH340G-CH340-3-3V-5V-Serial-Converter-Switch/1856263846.html
*  http://cdn.arduined.eu/wp-content/uploads/2014/10/CH340G-converter-connection-pinout-for-programming-Arduino-Pro-Mini.jpg

* Arduino Pro Mini 3.3V 8MHz
*  http://www.aliexpress.com/item/New-Pro-Mini-atmega328-3-3V-8M-Replace-ATmega128-For-Arduino-Compatible-Nano/1859091978.html

* USBasp Programmer
*  http://www.aliexpress.com/item/USBasp-USB-ISP-3-3V-5V-AVR-Programmer-USB-ATMEGA8-ATMEGA128-New-10PIN-Wire-Support/2036402518.html
*  http://samopal.pro/wp13_samopal/wp-content/uploads/561/cxema.jpg

Do:
* Install Arduino IDE 1.6.x
* Copy "hardware" folder into Arduino workspace folder. eg.: /home/mike/Arduino/
* Start Arduino IDE > Tools > Board > ProMini LowPower (Internal Clock) >> select BOD level
* Connect USBASP, Arduino IDE > Tools > Programmer > USBasp
* Arduino IDE > Tools > Burn Bootloader
* Connect TTL Adapter, Start Arduino IDE > Upload sketches

Get:
* Ultra low Power Arduino Pro Mini
