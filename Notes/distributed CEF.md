 2407121501
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# distributed CEF

# Distributed CEF (dCEF)

## My Understanding

dCEF (Distributed Cisco Express Forwarding) is used in conjunction with higher-end networking equipment like chassis routers. Chassis routers typically have different modules: one for route processing and others for line cards used in packet forwarding. dCEF places a copy of the FIB (Forwarding Information Base) and adjacency table on each forwarding line card. When the Route Processor receives a routing update, it updates the FIB and the adjacency table (which is derived from ARP). This distribution allows for faster routing, improved scalability, and some fault tolerance. If one of the line cards goes down, the router can still route properly using the other line cards.
## Fundamentals

### Definition
Distributed CEF (dCEF) is an enhanced version of Cisco Express Forwarding designed for high-end routers and switches with multiple line cards or forwarding engines. It distributes forwarding decisions across multiple processing units to improve scalability and performance.

### Key Concepts and Components

1. Distribution of Forwarding Information:
   - Each line card maintains its own copy of the Forwarding Information Base (FIB) and adjacency table
   - Central Route Processor (RP) synchronizes information across all line cards

2. Line Card Independence:
   - Each line card can make forwarding decisions independently
   - Reduces reliance on the central route processor

3. Scalability:
   - Supports higher throughput compared to centralized CEF
   - Better suited for large-scale networks and high-traffic environments

4. Consistency Checking:
   - Periodic verification to ensure FIB consistency across all line cards

5. Load Sharing:
   - Supports both per-destination and per-packet load sharing across multiple paths

### Importance
- Enables wire-speed packet forwarding on high-end platforms
- Reduces central CPU utilization
- Improves network scalability and performance
- Supports faster convergence in large networks

## Feynman Method Explanation

Imagine a large library with multiple floors, where each floor represents a line card in a router. In a regular library (like standard CEF), there's one central catalog (the FIB) that all librarians consult to find books.

Now, in our distributed library (dCEF), each floor has its own complete catalog. When a new book arrives or a book location changes, the head librarian (Route Processor) informs all floor librarians to update their catalogs.

When a visitor asks for a book, the librarian on that floor can immediately help without checking with the central desk. This makes the process much faster, especially when the library is busy.

If a floor gets really crowded (high traffic on a line card), it doesn't slow down the other floors. And if one floor's catalog gets damaged (line card failure), the other floors can still operate normally.

This is how dCEF works - by distributing the forwarding information to each line card, allowing for faster, more scalable packet forwarding in large networks.

## Relevant Cisco Commands

```
# Enable dCEF (on supported platforms)
ip cef distributed

# Verify dCEF status
show cef state

# Display dCEF FIB on a specific line card
show ip cef [prefix] internal

# Check FIB consistency
show ip cef consistency-check

# Display dCEF adjacency table
show adjacency

# Display dCEF statistics
show cef interface [interface-name] statistics

# Clear dCEF tables and perform a full rebuild
clear ip cef linecard [slot-number] *

# Disable dCEF on an interface
interface [interface-name]
no ip route-cache distributed
```

## Related RFCs

1. [RFC 3222 - Terminology for Forwarding Information Base (FIB) based Router Performance](https://datatracker.ietf.org/doc/html/rfc3222)
2. [RFC 4655 - A Path Computation Element (PCE)-Based Architecture](https://datatracker.ietf.org/doc/html/rfc4655) (Relevant for understanding distributed network architectures)


## Cisco Whitepapers and Documentation

1. [Cisco Express Forwarding Overview](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipswitch_cef/configuration/xe-3s/isw-cef-xe-3s-book/isw-cef-overview.html)
2. [Configuring Cisco Express Forwarding](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipswitch_cef/configuration/xe-16/isw-cef-xe-16-book/isw-cef-config.html)
3. [IP Switching Cisco Express Forwarding Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipswitch_cef/configuration/xe-16/isw-cef-xe-16-book.html)
4. [Distributed Cisco Express Forwarding Load Sharing](https://www.cisco.com/c/en/us/support/docs/ip/express-forwarding-cef/18285-loadsha-dCEF.html)
5. [How to Verify Cisco Express Forwarding Switching](https://www.cisco.com/c/en/us/support/docs/routers/12000-series-routers/47321-cef-config.html)

---
# Reference