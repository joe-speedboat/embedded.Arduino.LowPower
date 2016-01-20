# HowTo build Low Power Arduino 1MHz


## Buy:
* USB to TTL Adapter
  *  http://www.aliexpress.com/item/USB-to-TTL-UART-Module-CH340G-CH340-3-3V-5V-Serial-Converter-Switch/1856263846.html
  *  http://cdn.arduined.eu/wp-content/uploads/2014/10/CH340G-converter-connection-pinout-for-programming-Arduino-Pro-Mini.jpg

* Arduino Pro Mini 3.3V 8MHz
  *  http://www.aliexpress.com/item/New-Pro-Mini-atmega328-3-3V-8M-Replace-ATmega128-For-Arduino-Compatible-Nano/1859091978.html

* USBasp Programmer
  *  http://www.aliexpress.com/item/USBasp-USB-ISP-3-3V-5V-AVR-Programmer-USB-ATMEGA8-ATMEGA128-New-10PIN-Wire-Support/2036402518.html
  *  http://samopal.pro/wp13_samopal/wp-content/uploads/561/cxema.jpg

## Do:
* Install Arduino IDE 1.6.x
* Copy "hardware" folder into Arduino workspace folder. eg.: /home/mike/Arduino/
* Start Arduino IDE > Tools > Board > ProMini LowPower (Internal Clock) >> select BOD level
* Connect USBASP, Arduino IDE > Tools > Programmer > USBasp
* Arduino IDE > Tools > Burn Bootloader
* Connect TTL Adapter, Start Arduino IDE > Upload sketches

## Get:
* Ultra low Power Arduino Pro Mini

## HowTo Use:
* Start Arduino IDE (tested 1.6.7)
* Tools > Board > ProMini LowPower 
* Tools > Processor > Select your needs
* Select Programmer you own, eg USBASP: Tools > Programmer > USBasp
* Connect Programmer to ProMini 3.3v 8MHz: https://www.google.ch/search?q=usbasp+pro+mini
* Tools > Burn Bootloader
* Verify power consumption
* Remove Power Regulator and Power LED
* Verify power consumption: should be around 1-4 mA
* Verify power consumption in deep sleep mode: should be around 1-4 uA !!!! (Tested with 8MHz ProMini)

## Overview of available mods:
* 1Mhz - BOD dis.  - int. Clock(CKDIV8)
* 1Mhz - BOD 1.8V - int. Clock(CKDIV8)
* 8Mhz - BOD dis.  - int. Clock
* 8Mhz - BOD 1.8V - int. Clock
* 1Mhz - BOD dis.  - ext. Clock(CKDIV8)
* 1Mhz - BOD 1.8V - ext. Clock(CKDIV8)
* 2Mhz - BOD dis.  - ext. Clock(CKDIV8)
* 2Mhz - BOD 1.8V - ext. Clock(CKDIV8)
* 8MHz - BOD dis.  - ext. Clock
* 8MHz - BOD 1.8V - ext. Clock




## Overview of power usage:
<pre>
ORIGINAL PRO MINI - 8MHz, 3.3V
----------------------------------------------------------------
Setting                   IDLE            POWER_DOWN      INPUT
--------------            --------        ----------      --------
Original                  5.0mA           1.5mA           VCC 3.4V
noPower LED               3.6mA           100uA           VCC 3.4V
noPower LED, no PWR Reg.  3.6mA           20uA            VCC 3.4V


ORIGINAL PRO MINI - 8MHz, 3.3V - BOD disabled
----------------------------------------------------------------
Setting                   IDLE            POWER_DOWN      INPUT
--------------            --------        ----------      --------
noPower LED, no PWR Reg.  3.6mA           3uA             VCC 3.4V


ORIGINAL PRO MINI - 1MHz CKDIV8, 3.3V - BOD disabled
----------------------------------------------------------------
Setting                   IDLE            POWER_DOWN      INPUT
--------------            --------        ----------      --------
noPower LED, no PWR Reg.  1.1mA           2uA             VCC 3.4V
</pre>

## Power Test Sketch:
<pre>
#include "LowPower.h"

void setup()
{
    // No setup is required for this library
}

void loop() 
{
    // Enter power down state for 8 s with ADC and BOD module disabled
    LowPower.powerDown(SLEEP_8S, ADC_OFF, BOD_OFF);  
    // Enter idle  state for 8 s
    delay(8000);  
}
</pre>
