---
layout: post
title:  "WIRESHARK INSTALLATION ON UBUNTU"
date:   2018-04-08 19:45:31 +0530
categories: wireless
---

#### Installing AIRCRACK on UBUNTU
```
root@root$ sudo apt install aircrack-ng
```

#### Creating a interface for monitor mode
```
root@root$ airmon-ng start wlp1s0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
764	avahi-daemon
784	avahi-daemon
870	NetworkManager
1058	wpa_supplicant
22768	dhclient
Process with PID 22768 (dhclient) is running on interface wlp1s0


Interface	Chipset		Driver

wlp1s0		Intel AC	iwlwifi - [phy0]
				(monitor mode enabled on mon0)

root@vieshoth-PC:~# 

```

#### Installing wireshark
```
root@root$ sudo add-apt-repository ppa:wireshark-dev/stable
root@root$ sudo apt-get update
root@root$ sudo apt-get install wireshark

```

#### Instantiate Wireshark
```
root@root$ wireshark
```
