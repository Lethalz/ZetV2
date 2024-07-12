 2407121434
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# CEF primer

# Cisco Express Forwarding (CEF)

## My Understanding
[Space for your own notes and understanding of the topic]

## Fundamentals

### Definition
Cisco Express Forwarding (CEF) is an advanced layer 3 IP switching technology used in Cisco routers and switches to optimize network performance.

### Key Concepts and Components
1. Forwarding Information Base (FIB):
   - A copy of the routing table optimized for fast lookup
   - Contains pre-computed paths for known destinations

2. Adjacency Table:
   - Contains layer 2 addressing information for next-hop destinations
   - Includes MAC addresses for directly connected neighbors

3. Load Balancing:
   - Per-destination: Based on destination IP address
   - Per-packet: Round-robin distribution across equal-cost paths

4. Distributed CEF (dCEF):
   - Used in high-end routers with multiple line cards
   - Each line card maintains its own copy of FIB and adjacency table

### Importance
- Improves packet forwarding performance
- Reduces CPU utilization in routers and switches
- Enables fast route convergence
- Supports advanced features like QoS and encryption

## Feynman Method Explanation

Imagine you're a taxi dispatcher in a big city. You have two essential tools:

1. A city map with all the best routes pre-calculated (this is like the FIB)
2. A list of landmarks near common destinations (this is like the Adjacency Table)

When a customer calls for a ride, instead of calculating the route from scratch each time, you quickly look at your pre-calculated map (FIB) to find the best path. Then, you check your landmark list (Adjacency Table) to give the driver an easily recognizable next stop.

This system allows you to dispatch taxis much faster than if you had to plan each route individually. That's essentially what CEF does for network packets - it pre-calculates routes and stores information about the next stop, allowing for much faster forwarding decisions.

## Relevant Cisco Commands

```
# Enable CEF (usually on by default in modern Cisco devices)
ip cef

# Enable distributed CEF on supported platforms
ip cef distributed

# Verify CEF status
show ip cef

# Display CEF FIB
show ip cef [detail]

# Display CEF adjacency table
show adjacency

# Display CEF statistics
show ip cef switching statistics

# Clear CEF tables and perform a full rebuild
clear ip cef

# Disable CEF on an interface
interface [interface-name]
no ip route-cache cef
```

## Related RFCs

1. [RFC 4594 - Configuration Guidelines for DiffServ Service Classes](https://datatracker.ietf.org/doc/html/rfc4594) (Relevant for QoS aspects of CEF)
2. [RFC 2328 - OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328) (Relevant for routing aspects that CEF optimizes)
3. [RFC 2992 - Analysis of an Equal-Cost Multi-Path Algorithm](https://datatracker.ietf.org/doc/html/rfc2992) (Relevant for load balancing in CEF)

## Cisco Whitepapers and Documentation

1. [How to Verify Cisco Express Forwarding Switching](https://www.cisco.com/c/en/us/support/docs/routers/12000-series-routers/47321-cef-config.html)
2. [Cisco Express Forwarding Overview](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipswitch_cef/configuration/xe-3s/isw-cef-xe-3s-book/isw-cef-overview.html)
3. [Configuring Cisco Express Forwarding](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipswitch_cef/configuration/xe-16/isw-cef-xe-16-book/isw-cef-config.html)
4. [IP Switching Cisco Express Forwarding Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipswitch_cef/configuration/xe-16/isw-cef-xe-16-book.html)
5. [Troubleshooting Cisco Express Forwarding-Related Error Messages](https://www.cisco.com/c/en/us/support/docs/ip/express-forwarding-cef/13706-20.html)

---
# Reference