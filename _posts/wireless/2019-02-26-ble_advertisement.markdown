---
layout: post
title:  "BLE ADVERTISEMENT"
date:   2019-02-26 19:45:31 +0530
categories: wireless
---

Bluetooth Low Energy operates on 2.4GHz ISM band, which is seperated by 2MHz each. This 2.4 GHz is seperated by 40 channels.
3 for Advertising and 37 for data transimission.

Both the Advertising and Data transmission follows the same frame structure as shown below.

![GitHub Logo](/images/ble_adv_full_frame.PNG)

However the difference comes in how many bytes used in the PDU as shown below

For Advertisment:

![GitHub Logo](/images/ble_adv_full_frame.PNG)




which comprises of four components.

ADV Types |ADV_IND | ADV_DIRECT_IND | ADV_NONCONN_IND | ADV_SCAN_IND
-------- | ------------ | ------------- | -------------- | ----------
Full Form | Adevertisement Indication | Adevertisement Direct Indication | Adevertisement non connectable Indication |  Adevertisement scannable Indication
Connectable | Yes - Connection request to any Central device | Yes - Connection request to a particular device | Non connectable - Only Beacons |  Non connectable - Only Beacons
scan responses | Yes | Yes | No |  Yes



![GitHub Logo](/images/ble_adv_pdu.PNG)
![GitHub Logo](/images/ble_adv_pdu_header.PNG)
![GitHub Logo](/images/ble_adv_full_pic.PNG)


