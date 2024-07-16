2407121420
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# MTU(maximum transmission Unit)


# MTU (Maximum Transmission Unit)

## My Understanding
MTU (Maximum Transmission Unit) is the maximum size of data that can be encapsulated within an Ethernet frame. TCP MSS (Maximum Segment Size) is different in the sense that it does not include the IP or transport header, just the payload.

MTU affects network performance and efficiency:

- Lower MTU: Fewer errors but more overhead due to the higher header-to-data ratio.
- Higher MTU: Less overhead but potentially more errors because each packet contains more data.

If a packet is larger than the set MTU on your ingress interface, you will need to fragment the packet or increase the MTU of that interface to accept the larger frame.

MTU is important to understand because it affects certain services like GRE tunnels. Due to the extra overhead or headers that GRE uses, you cannot use the original default MTU. This is because the size of the data would be 1524 bytes or more, which is too big. Therefore, you need to lower the MTU to something like 1476 bytes to avoid problems with communication across the tunnel.

```ad-note
icon:note
GRE adds 24 bytes of overhead (20 bytes for the new IP header and 4 bytes for the GRE header).
```

Networks often benefit from using the largest MTU possible that doesn't cause fragmentation along the path, as this can improve efficiency by reducing packet overhead. Path MTU Discovery (PMTUD) is used to determine the maximum MTU size that can be used along the entire path between the source and destination without requiring fragmentation


## Fundamentals

### Definition
- MTU: The largest size packet or frame that can be transmitted in a single network layer transaction

### Key Concepts and Components
- Measured in bytes
- Typically ranges from 576 to 1500 bytes for Ethernet networks
- Affects network performance and efficiency
- Path MTU Discovery (PMTUD): Process to determine the MTU size on the path between two IP hosts
- Fragmentation: Process of breaking larger packets into smaller ones when they exceed the MTU
- Jumbo frames: Ethernet frames with more than 1500 bytes of payload (up to 9000 bytes)
- There are 3 different types of MTU; System, IP, and Ethernet.

### Importance
- Optimizes network performance
- Reduces fragmentation and overhead
- Impacts throughput and latency

## Feynman Method Explanation

Imagine you're moving houses and need to transport your belongings using a truck. The MTU is like the maximum load capacity of the truck. 

If you try to load an item that's too big (a packet larger than the MTU), you have two options:
1. Break it down into smaller pieces (fragmentation)
2. Find a bigger truck (increase MTU)

Just as you want to maximize the truck's capacity without overloading it, networks aim to use the largest MTU possible without causing issues. This ensures efficient transportation of data, much like making fewer trips with a well-packed truck is more efficient than many trips with a half-empty one.

## Relevant Cisco Commands

```
# Show interface MTU
show interface [interface-name]

# Set MTU size on an interface
interface [interface-name]
mtu [bytes]

# Enable jumbo frames on a switch port
interface [interface-name]
mtu 9216

# Show IP MTU for an interface
show ip interface [interface-name]

# Configure IP MTU on an interface
interface [interface-name]
ip mtu [bytes]
```

## Related RFCs

1. [RFC 791 - Internet Protocol](https://datatracker.ietf.org/doc/html/rfc791) (Defines original IPv4 MTU)
2. [RFC 1191 - Path MTU Discovery](https://datatracker.ietf.org/doc/html/rfc1191)
3. [RFC 1981 - Path MTU Discovery for IP version 6](https://datatracker.ietf.org/doc/html/rfc1981)
4. [RFC 2923 - TCP Problems with Path MTU Discovery](https://datatracker.ietf.org/doc/html/rfc2923)
5. [RFC 4821 - Packetization Layer Path MTU Discovery](https://datatracker.ietf.org/doc/html/rfc4821)

## Cisco Whitepapers and Documentation

1. [Resolve IP Fragmentation, MTU, MSS, and PMTUD Issues with GRE and IPSEC](https://www.cisco.com/c/en/us/support/docs/ip/generic-routing-encapsulation-gre/25885-pmtud-ipfrag.html)
2. [IP Fragmentation and PMTUD](https://www.cisco.com/c/en/us/support/docs/ip/generic-routing-encapsulation-gre/25885-pmtud-ipfrag.html)
3. [Configuring IEEE 802.1Q and Layer 2 Protocol Tunneling](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst3750x_3560x/software/release/12-2_55_se/configuration/guide/3750xscg/swl2tun.html) (Includes MTU considerations)
4. [Configuring Jumbo/Giant Frame Support on Catalyst Switches](https://www.cisco.com/c/en/us/support/docs/switches/catalyst-6000-series-switches/24048-148.html)
5. [IP Addressing: IPv4 Addressing Configuration Guide, Cisco IOS XE Release 3S](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_ipv4/configuration/xe-3s/ipv4-xe-3s-book.html) (Includes MTU configuration)

---
# Reference

![[Pasted image 20240716122114.png]]