---
layout: post
title:  "How SSL certificate works"
date:   2019-02-06 19:45:31 +0530
categories: Linux
---
This blog explains how ssl certificate works when you entered a web address with https in the browser.

The moment you press enter after typing website address lets say amazon.com in the browser. The brower will send a webpage request to amazon server. The amazon server in return sends ssl certificate and the public key to the browser.
![GitHub Logo](/images/ssl_certificate/page_request.PNG)

Upon receiving the public key and the ssl certificate from amazon server the browser must verify this ssl certificate by sending it to a CA. The Browser encrypts this ssl certificate with the CA's public key before sending it to CA.
A point to worth noting is all the browser comes with the public keys of all major CAs.

![GitHub Logo](/images/ssl_certificate/verifying_withCA.PNG)

After successfull verification the browser will create a two symmertic key. 
It keeps one with it and encrypts the other with the amazon server's public key and sends it to the amazon server.
![GitHub Logo](/images/ssl_certificate/symmetrical_key.PNG)

The amazon server decrypts this symetric key with its private key and from now on both the browser and the amazon server uses this symmetric key to encrypt and decrypt data exchange to be exchanged between them.
![GitHub Logo](/images/ssl_certificate/symm_key_sharing.PNG)
