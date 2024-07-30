2407121049
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# ARP and Proxy ARP


# ARP and Proxy ARP

## My Understanding
[Space for your own notes and understanding of the topic]

## Fundamentals

### Address Resolution Protocol (ARP)
- Purpose: Maps IP addresses to MAC addresses in local area networks
- Key Components:
  - ARP Request: Broadcast message asking "Who has this IP address?"
  - ARP Reply: Unicast message saying "I have that IP, here's my MAC address"
- ARP Cache: Temporary storage of IP-to-MAC mappings
- Operates at Layer 2 (Data Link Layer) of the OSI model

### Proxy ARP
- Definition: A technique where one host answers ARP requests intended for another
- Purpose: Enables communication between networks without configuring routing or a default gateway
- Key Components:
  - Proxy ARP Router: Responds to ARP requests on behalf of hosts in other networks
  - ARP Spoofing: Potential security risk if misused

## Feynman Method Explanation

Imagine a large office building with many rooms. Each room (computer) has a unique room number (IP address) and a nameplate (MAC address) on the door. 

When you want to deliver a package (data) to a specific room, you know the room number but not the exact location. So, you shout in the hallway (broadcast ARP request), "Who's in room 101?" The person in room 101 hears you and responds, "That's me! I'm John Doe" (ARP reply with MAC address).

Now, Proxy ARP is like having a helpful receptionist at the building entrance. When you ask for a room in a different department (another network), instead of letting you wander around, the receptionist says, "I can take that package for you" and ensures it gets to the right room, even if it's in another part of the building.

## Relevant Cisco Commands

```
# Display the ARP cache
show arp

# Clear the ARP cache
clear arp-cache

# Configure a static ARP entry
arp [ip-address] [mac-address] arpa

# Enable Proxy ARP on an interface
interface [interface-name]
ip proxy-arp

# Disable Proxy ARP on an interface
interface [interface-name]
no ip proxy-arp

# Show IP ARP details
show ip arp
```


## Related RFCs

1. [RFC 826 - An Ethernet Address Resolution Protocol](https://datatracker.ietf.org/doc/html/rfc826)
2. [RFC 1027 - Using ARP to Implement Transparent Subnet Gateways (Proxy ARP)](https://datatracker.ietf.org/doc/html/rfc1027)
3. [RFC 5227 - IPv4 Address Conflict Detection](https://datatracker.ietf.org/doc/html/rfc5227)
4. [RFC 2461 - Neighbor Discovery for IP Version 6 (IPv6)](https://datatracker.ietf.org/doc/html/rfc2461)
5. [RFC 4861 - Neighbor Discovery for IP version 6 (IPv6) - Obsoletes RFC 2461](https://datatracker.ietf.org/doc/html/rfc4861)

## Cisco Whitepapers and Documentation

1. [Address Resolution Protocol (ARP)](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_arp/configuration/15-mt/arp-15-mt-book/arp-config-arp.html)
2. [Configuring Proxy ARP](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_arp/configuration/15-mt/arp-15-mt-book/arp-proxy-arp.html)
3. [Understanding and Configuring ARP](https://www.cisco.com/c/en/us/support/docs/ip/dynamic-address-allocation-resolution/13718-5.html)
4. [How ARP Works](https://www.cisco.com/c/en/us/support/docs/ip/dynamic-address-allocation-resolution/13718-5.html#anc7)
5. [Cisco IOS IP Addressing Services Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr/configuration/15-mt/ipaddr-15-mt-book.html)
---
# Reference