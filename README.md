# homebridge-http

Supports https devices on the HomeBridge Platform and provides a readable callback for getting the "On" and brightness level characteristics to Homekit.

# Installation

1. Install homebridge using: npm install -g homebridge
2. Install homebridge-http using: npm install -g homebridge-http
3. Update your configuration file. See sample-config.json in this repository for a sample. 

# Configuration

This module has recently been updated to support an additional method to read the power state of the device, the brightness level and color. 

Specify the `status_url` in your config.json that returns the status of the device as an integer (0 = off, 1 = on). 

Specify the `brightnesslvl_url` to return the current brightness level as an integer.

`hueset_url` and `saturationset_url` are for setting hue and saturation levels respectively. Both take an integer as a parameter, with the first one being in range `0-360` and the second in `0-100`. `hue_url` and `saturation_url` return current values of those settings.

Switch handling brightness handling, and color handling support 3 methods, yes for polling on app load, realtime for constant polling or no polling

Configuration sample:

 ```
"accessories": [ 
	{
		"accessory": "Http",
		"name": "Alfresco Lamp",
		"switchHandling": "realtime",
		"http_method": "GET",
		"on_url":      "http://localhost/controller/1700/ON",
		"off_url":     "http://localhost/controller/1700/OFF",
		"status_url":  "http://localhost/status/100059",
		"service": "Light",
		"brightnessHandling": "yes",
		"brightness_url":     "http://localhost/controller/1707/%b",
		"brightnesslvl_url":  "http://localhost/status/100054",
		"colorHandling": "yes",
		"hueset_url":     "http://localhost/hue/set/1707/%b",
		"hue_url":  "http://localhost/hue/status/100054",
		"saturationset_url":     "http://localhost/saturation/set/1707/%b",
		"saturation_url":  "http://localhost/saturation/status/100054",
		"sendimmediately": "",
		"username" : "",
		"password" : ""					    
       } 
    ]
```

#ToDo

Complete documentation and review a number of  forks