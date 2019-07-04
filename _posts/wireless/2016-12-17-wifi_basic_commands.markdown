---
layout: post
title:  "BASIC WIFI COMMANDS"
date:   2016-11-23 19:45:31 +0530
categories: wireless
---

#### To see list of saved connections
```
nmcli c
```

#### To see list of available WiFi hotspots
```
nmcli d wifi list
```
or:

```
sudo iwlist wlan0 scanning
```

#### To see list of interfaces 
```
ifconfig -a
```

#### To connect to a saved SSID
```
nmcli con up id vieshoth
```

#### To check the connected ssid
````
iw dev wlan0 link
````
