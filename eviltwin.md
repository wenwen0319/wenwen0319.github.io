---
layout: page
title: Project 1 Evil Twin
subtitle: Three Ways To Detect Evil Twin In A Real World.
---

## Three Ways To Detect
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

## Small Public Wifi Network
e.g., in Starbucks
Characteristics: The number of hops from the client to a public network(class A IP) is usually fixed. An evil Twin should be connected to the Internet. So it can use the original WIFI, 4G, … None of them have the same hops as the original one does.

Detection Method: It's based on the hops。
Use tracroute(UDP with TTL) to obtain information of every hops.
Calculate how many hops used for the client to arrive a class A IP. Usually 2 hops is OK. client->gateway->class A IP
### Pros and Cons
Pros:
* Client based
* Easy to apply
* Fast
* Low cost
Cons:
* So easy to hack 

## Large Public Wifi Network
e.g., in a company
Characteristics: 
1)Complex network, but the company can give us the information of whole WIFI network. 
2)What’s more, the first two hops in a large WIFI network are usually fixed.
3)The Evil Twin is usually in the Network
Detection: It's based on hops.(Especially the first two hops)
Set a authentication sever in the network. The sever saves legal AP’s IP, routing path and other information.
When a client connects to the network, use traceroute to get the routing information and send the information to the sever.
If the all routing paths is legal
	(1) no extra AP(no extra IP)
	(2) the AP sequence is correct
Then we think it’s a legal connection
Else it’s illegal
### Pros and Cons
Pros:
* Client based
* Easy to apply
* Fast
* Low cost
Cons:
* Needs a sever and all the information, which is only available for a large network and a large company.


