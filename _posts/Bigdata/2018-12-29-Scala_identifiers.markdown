---
layout: post
title:  "SCALA IDENTIFIERS"
date:   2018-12-29 19:45:31 +0530
categories: Bigdata
---

#### What is Scala
Scala is a 
	* jvm based language - Scala project binary can be run directly in the jvm environment
	* Functional programming language - Functional programming means avoiding mutability. Scala 	language has provision to avoid mutability.
	* Pure OOL (Object Oriented Language) - In Scala everything is object. There is no primitive datatypes in Scala

#### Functional Programing

functional programing literary means avoiding changing the surroundings.
In short this features is called as avoiding mutability.
Mutability means modifying.
However it doesnot mean it is always avoiding mutability. ofcourse it is possible to write a function 
which modifies the sorrounding data. but there should be a clear cut seperation of what is mutabiliy and immutability.
write a seperate function for mutability and imutability.

Basically this a function is used to process some data. This processed data either we can save
the data or return the data.
saving the data means saving it to a file or variale or dB or global datastructure. This is nothing but modifying 
the surrounding.

return - immutability.
non return - mutability.

So Scala is more suitable for distributed application. 
- Running the same prg in different env. since it follows immutability it doesnot change environment. so it is safe.

#### Values and Variables

what is pure. In scala there is no primitive datatype.
Everything is object in Scala.
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


