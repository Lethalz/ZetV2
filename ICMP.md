2407221342
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# ICMP

# ICMP (Internet Control Message Protocol) and ICMPv6

## My Understanding
[Space for your own notes and understanding of the topic]

## Fundamentals

ICMP (Internet Control Message Protocol) is a network layer protocol used for error reporting and operational information about IP packet processing. ICMPv6 is the ICMP version for IPv6.

Key Concepts:
1. ICMP is integral to IP operations, providing feedback about network problems.
2. ICMP messages are encapsulated within IP packets with a protocol number of 1.
3. There are two main types of ICMP messages: Error messages and Query messages.


### ICMP Header 

ICMP Header Format
Octet                 0           1            2-3
Octet    Bit       0-7      8-15       16-31
0           0        Type     Code    Checksum
4           32            Rest of header

```ad-info
In error messages, the IP header + the first 64 bits of the IP payload of the packet that caused the error are sent.
```


ICMP Message Types:

Error Messages:
1. Destination Unreachable (Type 3)
   - Indicates a packet couldn't be delivered to its destination
   - Various codes specify the reason (e.g., network unreachable, port unreachable)
    ![[Pasted image 20240722140717.png]]

2. Redirect (Type 5)
   - Sent by routers to inform hosts of a better route for a destination
![[Pasted image 20240723142347.png]]

3. Time Exceeded (Type 11)
   - Sent when a packet's TTL reaches zero
   - Used by the traceroute utility

Query Messages:
1. Echo Request (Type 8) and Echo Reply (Type 0)
   - Used by the ping utility to test connectivity (Can have a 0-byte payload)
   - In Echo messages, the data in the Echo Request must be echoed back in the Echo Reply.

ICMPv6 Specific Messages:
1. Neighbor Solicitation and Advertisement (Types 135 and 136)
   - Used for address resolution, similar to ARP in IPv4

2. Router Solicitation and Advertisement (Types 133 and 134)
   - Used for stateless address autoconfiguration

```ad-info
title: ICMP and Security
collapse: closed
icon: shield-alt

ICMP can be used for network reconnaissance and attacks. Many firewalls restrict ICMP traffic as a security measure.
```

```ad-seealso
collapse:closed
Traceroute used to be an ICMP message type!
```
## Feynman Method Explanation

Imagine the internet as a vast postal system. IP is like the addressing and routing system that gets packages (data) from one place to another. Now, ICMP is like the feedback system in this postal network.

If a package can't be delivered (Destination Unreachable), ICMP sends a message back to the sender explaining why - maybe the address doesn't exist, or the route is blocked.

If a postal worker knows a quicker route (Redirect), they might send a note suggesting this better path for future deliveries.

If a package has been in transit too long (Time Exceeded), ICMP sends a message saying it's been discarded to prevent endless circulation.

The Echo Request and Reply are like sending a postcard to yourself from a distant location. If it comes back, you know the postal system can successfully deliver to that address.

ICMPv6 adds some new features, like helping devices introduce themselves to their neighbors (Neighbor Discovery), which is crucial in the IPv6 world where devices often configure their own addresses.

## Relevant Commands

Display ICMP statistics:
```
show ip icmp statistics
```

Enable ICMP redirects (Cisco IOS):
```
ip redirects
```

Disable ICMP redirects:
```
no ip redirects
```

Configure ICMP unreachable messages:
```
ip unreachables
```

Disable ICMP unreachable messages:
```
no ip unreachables
```

Debug ICMP:
```
debug ip icmp
```

```ad-warning
title: Debugging Caution
collapse: closed
icon: exclamation-triangle

Debugging can be resource-intensive. Use with caution on production networks.
```

Rate limit how often the router will send unreacheables:
```
ip icmp rate-limit unreachables milliseconds
```

Rate limit how often the router will send unreacheables but only code 4:
```
ip icmp rate-limit unreachables df milliseconds



## Related RFCs

1. [RFC 792 - Internet Control Message Protocol](https://datatracker.ietf.org/doc/html/rfc792)
   - Defines the original ICMP for IPv4

2. [RFC 4443 - Internet Control Message Protocol (ICMPv6) for IPv6](https://datatracker.ietf.org/doc/html/rfc4443)
   - Defines ICMPv6

3. [RFC 4861 - Neighbor Discovery for IP version 6 (IPv6)](https://datatracker.ietf.org/doc/html/rfc4861)
   - Describes the Neighbor Discovery Protocol, which uses ICMPv6 messages

4. [RFC 4884 - Extended ICMP to Support Multi-Part Messages](https://datatracker.ietf.org/doc/html/rfc4884)
   - Defines extensions to ICMP to support multi-part messages

## Cisco Documentation and Whitepapers

1. [IP Addressing: ICMP Configuration Guide, Cisco IOS XE Release 3S](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_icmp/configuration/xe-3s/iad-icmp-xe-3s-book.html)
   - Comprehensive guide on ICMP configuration in Cisco IOS XE

2. [Configuring ICMP](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_icmp/configuration/15-mt/iad-icmp-15-mt-book/iad-icmp-cfg.html)
   - Detailed instructions on configuring ICMP on Cisco devices

3. [IP Addressing: IPv6 Addressing Configuration Guide, Cisco IOS XE Release 3S](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipv6_basic/configuration/xe-3s/ip6b-xe-3s-book.html)
   - Includes information on ICMPv6 configuration

4. [Cisco IOS IP Configuration Guide, Release 12.2: Configuring IP Services](https://www.cisco.com/c/en/us/td/docs/ios/12_2/ip/configuration/guide/fipr_c/1cfip.html)
   - Contains sections on ICMP configuration and best practices

```ad-tip
title: Best Practice
collapse: closed
icon: lightbulb

While ICMP is crucial for network diagnostics, consider limiting ICMP traffic from untrusted networks to prevent potential security issues.
```

## Conclusion

ICMP and ICMPv6 are essential protocols for network diagnostics and error reporting in IP networks. They provide valuable feedback about network conditions and problems, enabling tools like ping and traceroute. However, they can also be exploited for network reconnaissance, so careful configuration and monitoring are necessary in production environments.

---
# Reference

https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol