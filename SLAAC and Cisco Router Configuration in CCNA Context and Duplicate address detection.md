
# Slaac
## Overview

Stateless Address Autoconfiguration (SLAAC) is an IPv6 feature that allows devices on a network to automatically configure their IP addresses and certain other parameters without the need for a DHCP server. In CCNA studies, understanding SLAAC is essential for grasping how IPv6 networks operate without manual configuration.

### What is SLAAC?

SLAAC allows a host to create its IPv6 address using a combination of a network prefix from a local router and its interface identifier.

### Functions of SLAAC

1. **Address Configuration**: Automatically configures IPv6 addresses.
2. **Router Discovery**: Discovers available routers on the network.
3. **Default Gateway**: Determines the default gateway automatically.

## Relationship with NDP

SLAAC relies heavily on the Neighbor Discovery Protocol (NDP) for its operation. Router Advertisements (RAs) sent by routers contain prefix information that hosts use to automatically configure their IPv6 addresses. These RAs are part of NDP.

## Cisco Router Configuration for SLAAC

### Step 1: Enable IPv6 Routing

First, you must enable IPv6 unicast routing on the router.



`Router(config)# ipv6 unicast-routing`

### Step 2: Configure the Interface with SLAAC

Next, configure the interface that will provide the SLAAC service.


```
Router(config)# interface GigabitEthernet 0/0
Router(config-if)# ipv6 address autoconfig
Router(config-if)# no shutdown 
``` 

Device uses [[Solicited node multicast address and Neighbor Discovery Protocol#Neighbor Discovery Protocol (NDP) in CCNA Context | NDP]]   to learn the prefix used on the local link.
Then the device will use EUI-64 to generate the interface(host) ID or it will be randomly generated.