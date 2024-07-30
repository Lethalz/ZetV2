2407121428
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# TCP MSS

# TCP Maximum Segment Size (MSS)

## My Understanding
[
The term TCP MSS (Maximum Segment Size) is somewhat of a misnomer in the sense that "segment size" doesn't actually refer to the entire segment when it comes to this concept. The MSS is the maximum amount of data in bytes that a node can receive or send within a TCP segment, NOT including the TCP or IP headers.



### Definition
- MSS: The largest amount of data, specified in bytes, that a computer or communications device can receive in a single TCP segment, excluding the TCP header and IP header.

### Key Concepts and Components
- Typically negotiated during the TCP 3-way handshake
- Related to but different from MTU (Maximum Transmission Unit)
- Default MSS is typically 536 bytes for IPv4 and 1220 bytes for IPv6
- MSS = MTU - (IP header size + TCP header size)
- MSS clamping: technique used to avoid fragmentation in some network scenarios

### Importance
- Optimizes TCP performance
- Helps prevent fragmentation
- Affects throughput and efficiency of data transfer

## Feynman Method Explanation

Imagine you're packing boxes to ship items through a delivery service. The MSS is like the maximum size of the box's contents, while the MTU is like the total size of the box including its packaging.

The delivery service (the network) has a limit on how big each box can be (MTU). You want to pack as much as possible into each box (MSS) while leaving enough room for the packing material and label (TCP and IP headers).

If you try to pack more than the MSS allows, you'll have to use multiple boxes (fragmentation), which is less efficient and increases the chance of items getting lost.

Just as you'd adjust your packing strategy based on the delivery service's box size limits, networks adjust their MSS to optimize data transfer within the constraints of the MTU.

## Relevant Cisco Commands

```
# Show TCP MSS for a specific interface
show ip interface [interface-name]

# Set TCP MSS adjustment (clamping) on an interface
interface [interface-name]
ip tcp adjust-mss [max-segment-size]

# Show TCP connections and their MSS values
show tcp brief all

# Configure TCP MSS for BGP
router bgp [AS-number]
neighbor [IP-address] maximum-prefix [max-prefix-value]

# Show TCP parameters including MSS
show tcp parameters
```

## Related RFCs

1. [RFC 879 - The TCP Maximum Segment Size and Related Topics](https://datatracker.ietf.org/doc/html/rfc879)
2. [RFC 6691 - TCP Options and Maximum Segment Size (MSS)](https://datatracker.ietf.org/doc/html/rfc6691)
3. [RFC 793 - Transmission Control Protocol](https://datatracker.ietf.org/doc/html/rfc793) (Original TCP specification)
4. [RFC 1191 - Path MTU Discovery](https://datatracker.ietf.org/doc/html/rfc1191) (Relevant for MSS calculation)
5. [RFC 2923 - TCP Problems with Path MTU Discovery](https://datatracker.ietf.org/doc/html/rfc2923)

## Cisco Whitepapers and Documentation

1. [IP Fragment Attacks on Cisco IOS Software](https://tools.cisco.com/security/center/viewAlert.x?alertId=19756)
2. [Resolve IP Fragmentation, MTU, MSS, and PMTUD Issues with GRE and IPSEC](https://www.cisco.com/c/en/us/support/docs/ip/generic-routing-encapsulation-gre/25885-pmtud-ipfrag.html)
3. [TCP MSS Adjustment Feature for BGP Neighbors](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/iproute_bgp/configuration/xe-16/irg-xe-16-book/bgp-tcp-mss.html)
4. [Configuring TCP](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipapp/configuration/xe-16/iap-xe-16-book/iap-tcp.html)
5. [IP Addressing: IPv4 Addressing Configuration Guide, Cisco IOS XE Release 3S](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_ipv4/configuration/xe-3s/ipv4-xe-3s-book.html) (Includes MSS configuration)


## References


---
# Reference