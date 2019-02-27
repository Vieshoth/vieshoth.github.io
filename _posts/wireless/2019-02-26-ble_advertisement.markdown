---
layout: post
title:  "BLE ADVERTISEMENT"
date:   2019-02-26 19:45:31 +0530
categories: wireless
---

Bluetooth Low Energy operates on 2.4GHz ISM band, which is seperated by 2MHz each. This 2.4 GHz is seperated by 40 channels.
3 for Advertising and 37 for data transimission.

The length of both the advertising and data transmission frame is 37 bytes.

Both the Advertising and Data follows the same frame structure which comprises of four components.

ADV Types |ADV_IND | ADV_DIRECT_IND | ADV_NONCONN_IND | ADV_SCAN_IND
-------- | ------------ | ------------- | -------------- | ----------
Full Form | Adevertisement Indication | Adevertisement Direct Indication | Adevertisement non connectable Indication |  Adevertisement scannable Indication
Connectable | Yes - Connection request to any Central device | Yes - Connection request to a particular device | Non connectable - Only Beacons |  Non connectable - Only Beacons
Connectable | Connectable to any device | Connectable to a particular device | Non connectable - Only Beacons |  Non connectable - Only Beacons

Content in the first column | Content in the second column

---
ADV_IND: xxxx
ADV_DIRECT_IND: yyyy
ADV_NONCONN_IND: zzzz
ADV_SCAN_IND: aaaa
---

