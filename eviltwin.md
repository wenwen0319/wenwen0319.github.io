---
layout: page
title: Project 1 Evil Twin
subtitle: Three Ways To Detect Evil Twin In A Real World.
---

# Three Ways To Detect
1. detection for a private wifi network
2. detection for a small public wifi network
3. detection for a large public wifi network

## For A Private Wifi Network
e.g., in home
Characteristics: We can get all the information of the available AP.(e.g., MAC address, password, encryption, channel, frequency)
### Evil Twins are different from the original AP
Detection Method: It’s just like fingerprint. We save all the information in a dataset, and check if all information is right.

### Evil Twins are the same with the original AP
MSDU is in a beacon frame
Sequence number of the MSDU should be a continuous number. From 0x000 to 0xFFF
It’s hard to change an AP’s MSDU sequence number.
Even if you change the sequence number, they can not be a continuous sequence.

### Pros and Cons
Pros:
* It’s useful as long as AP broadcasts beacon frame.

Cons:
* Wireless network card should have the sniffer mode.
* It’s hard for a cellphone to start the sniffer mode.
* Too many packets may cause congestion. Hard to be implemented into an online algorithm. Even I use producer and consumer model.
* This means it’s hard to be implemented in a public area.
	
