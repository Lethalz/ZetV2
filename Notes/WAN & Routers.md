2212101739
	Status: #Exam
		Tags: [[CCNA 200-301]] [[Networking]]

# WAN & Routers



### HDLC and Leased lines

*High-Level Data-Link Control*
A leased line provides a **layer 1** service.
This is only used over the **WAN**
A leased line is usually from a telephone company (telco)
Not as prevalent as before
Leased Line Protocols: HDLC and Point-to-Poing Protocol (PPP)
These protocols control the **correct delivery** of data over a physical link of a particular type
ISO standard HDLC **does not have a Type field**, and routers need to know the type of packet inside the frame.
Cisco routers use a **proprietary version of HDLC** that **adds** a type field.

## Ethernet as WAN

functions as a Layer 2 service
Logically behaves like a point-to-point connection between two routers
Physically behaves as if a physical fiber ethernet link existed between the two routers

**Ethernet over MPLS** (EoMPLS): A term that refers to Multiprotocol Label Switching
(MPLS), a technology that can be used to create the Ethernet service for the customer.


![[b3a289a094c040232cef06445262cd7f.png]]


## IP Routing

All routers use the same general process to **route** the packet. Each router keeps an **IP rout-
ing table**. This table lists IP *address groupings*, called IP *networks* and IP *subnets*.

**Address Resolution Protocol (ARP)** as the method by which any host or
router on a LAN can dynamically learn the MAC address of another IP host or router on the
same LAN.

## Key Terms

Serial Interface—A type of interface on a router, used to connect to some types of WAN
links, particularly leased lines to complete a point-to-point connection.







---
# Reference