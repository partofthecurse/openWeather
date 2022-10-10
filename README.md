# openWeather
Open Source Weather Station that also looks quite nice.
Concept:
We are requesting Temperature and Weather ID with an openWeatherMap API Call . Weather is Displayed through Neopixel LEDs under a PMMA-Screen with engraved Icons. Temperature is resembled with LED Colour.

Parts needed:

    - ESP8266 or ESP32 Board, alternatively arduino nano with wifi shield will do as well but not coded here
    - Optional: DHT22 or DHT11 Sensor to measure Indoor Temp and Humidity
    - 4x WS2812 (aka NeoPixel) LED

Solder the 4 LEDs into a tiny LED Strip and connect to Dev Board:

    Board LED   LED   LED   LED
    3V3 - VCC - VCC - VCC - VCC
    GND - GND - GND - GND - GND
    D8 -  I/0 - I/O - I/O - I

Connect DHT22 / DHT11 to

    Board DHT
    3V3 - +
    GND - -
    D4  - OUT

Pixel-ID Icon reference (take care when assembling or switch in the code)

    0 - clear sky
    1 - cloudy
    2 - rainy
    3 - snow

Outdoortemperature & Colours:

    > 30°C - Red
    > 21°C - Warm yellow
    < 18°C - Light blue
    < 00°C - Blue
    Thunderstorm: Yellow
    Fog: White

    Red: error
    green: connecting

Optional: Send the measured DHT Data to an MQTT Broker (topics are customizable in captive portal)
    
    receive Data:
    temperature: stat/openWeather/Temperatur
    Humidity: stat/openWeather/Feuchtigkeit
    HeatIndex: stat/openWeather/HeatIndex
    
    controll openWeather:
    light on: cmnd/openWeather/power - payload on
    light off: cmnd/openWeather/power - payload off
    switch to party mode: cmnd/openWeather/state - PixelParty1 or PixelParty2
    
    upon receiving a command it sends back on stat/openWeather/power and stat/openWeather/state which mode it is in.
    
Dependencies:

    PubSubClient
    ArduinoJson
    ESP8266 Libs
    ESP32 Libs
    DHT Sensor library for ESPx
    WifiManager
    LittleFS
    
Now with WifiManager
