# BatAn
<strong>Solar and Battery Bank Monitoring</strong> (IoT)

This is a project to monitor a Battery Bank (Lithium Battery Packs) in a solar installation. It traces current individually for each Battery Pack. It also communicates with solar charger and calculates live values of power going to home and battery bank. It includes a web server with charts, internal historical data, and optionally, uploads data to Thingspeak and Blynk.


<img src="photos/collage.jpg" width="900"/>

<strong>Hardware used:</strong> <a href="photos/hardware/">see hardware pics</a>

- ESP8266 with OLED display board (Nodemcu, D-Duino?) 
- DHT11 Inside temperature and Humidity sensor
- DS18B20 external Temperature Sensor
- ADS1115 16 bit 4 channel Analog Input Boards (2x) (To read current and voltage sensors)
- ACS712 5V 20A Hall Effect current meters (5x) (*1)
- Voltage Sensor <25V Voltage Divider 5V
- DC-DC Voltage Converter Step-down Module 4-24V->5V (To supply ESP8266 board)
- Solid State Relay Module (optional, to control an AC Load via Web) (*2)
- TTL-to-RS485 Converter Module 3.3V-5V (To communicate with Solar Charger)
- Epever Tracer 2206AN (Solar Charger MPPT 20A)
- Lithium Battery Packs LiitoKala 24V 12ah 6S6P (5x) (Lithium Battery Bank, total capacity 1250 wh)

(*1) Current sensors are rated 20A but probably it's too much for sensor board. There are thermal switches for each battery pack limiting current to 10A. 5x10 = 50A, aprox. 1000 Watts maximum power.  
(*2) In pics is a regular relay but it was changed because coil interfered with hall current detectors.

<strong>ESP8266 embedded Web server:</strong>

- Raw Measures from current meters and modbus Communication with charger. It is possible to control   an AC Solid State Relay and DC Load output in solar charger, also to enable/disable Blynk or Modbus communications.

  <img src="photos/web1.png"/>

- Power Distribution from Photovoltaic Panels to Home, Battery Bank and Packs:

  <img src="photos/web2.png"/>

- Chart Live Data:

  <img src="photos/web3a.png"/>
  
- Chart Historical Data:

  <img src="photos/web3b.png"/>
  
- Chart Historical Data Selected View (Bank & Packs):
  
  <img src="photos/web3c.png"/>
  
<strong>Mobile App with Blynk</strong>
 
 <img src="photos/blynk_SS.png"/>

 1. Download Blynk App: http://j.mp/blynk_Android or http://j.mp/blynk_iOS
 2. Touch the QR-code icon and point the camera to the code below
 
 <img src="photos/blynk_QR.png"/>

<strong>ThingsPeak</strong>

Data is uploaded to ThingsPeak database for persistent historical records
 
 <img src="photos/thingspeak.png"/>

---------------------------------------------------------------

<strong>Schematic</strong> <a href="schematic/">see schematic files</a>

<a href="schematic/schem.pdf"><img src="schematic/schem.svg"  width="500"/></a>


---------------------------------------------------------------
<strong>Notes about the program</strong>

Special libraries used:

- Adafruit_ADS1015 (Analog Inputs) https://github.com/adafruit/Adafruit_SSD1306
- NtpClientLib (NTP Client with DST support) https://github.com/gmag11/NtpClient 
- TimeLib (Time functions) https://github.com/PaulStoffregen/Time
- Adafruit SSD1306 (OLED Display Driver) https://github.com/adafruit/Adafruit_SSD1306
- RemoteDebug (Telnet debug logs) https://github.com/JoaoLopesF/RemoteDebug
- Modbus Master https://github.com/4-20ma/ModbusMaster

For Modbus RS485 comms with Tracer, these references have been very useful: https://github.com/dpoulson/EPSolar
https://github.com/jaminNZx/Tracer-RS485-Modbus-Blynk

---------------------------------------------------------------
This project is part of an experiment, to check the behaviour and lifetime of Li-ion battery packs (BMS included) connected in parallel in a solar installation. Lithium Chemistry used is not LiFePo4 3.65V/Cell , recommended for solar installations, but regular Li-ion batteries 4.2V/Cell, with more capacity and also risks. As can be seen in photos Battery Packs are inside safety bags bellow <strong>Battery Analyzer</strong> and everything is in the roof. 

Solar Controller (Tracer 2206AN) chosen settings to charge these battery packs can be seen at  <a href="tracer.txt">Tracer Settings</a>

<strong>More info about the project in external links</strong> 
<ul>
<li><a href="https://circuitdigest.com/microcontroller-projects/iot-based-lithium-battery-monitoring-system">Circuit Digest. iot-based-lithium-battery-monitoring-system</a></li>
<li><a href="https://fritzing.org/projects/solar-and-battery-bank-monitoring">Fritzing. Solar-and-battery-bank-monitoring</a></li>
<li><a href="https://www.hackster.io/iotsoa/battery-bank-analyzer-af06d2">Hackster.io. Battery Bank Analyzer</a></li>
</ul>

