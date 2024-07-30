 2407252205
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# CCNP VLANS (BIG BOYYY)

# Virtual Local Area Networks (VLANs)

## My Understanding
[Space for your own notes and understanding of the topic]

## Fundamentals

VLANs are a method of creating logically independent networks within a single physical network infrastructure. They allow network administrators to partition a single physical network into multiple distinct broadcast domains.

Key Concepts:
1. Broadcast Domain Segmentation: VLANs create separate broadcast domains within a switch.
2. Improved Network Management: VLANs enhance security, performance, and efficiency.
3. Traffic Isolation: Different departments or groups can be isolated logically.
4. 802.1Q Standard: Defines VLAN tagging for Ethernet frames.
5. Access and Trunk Ports: Different port types for VLAN traffic handling.

VLAN Types:
1. Data VLAN: Carries user-generated traffic.
2. Default VLAN: VLAN 1, default for all ports.
3. Native VLAN: Untagged VLAN on a trunk link.
4. Management VLAN: Used for switch management traffic.

```ad-info
title: VLAN Range
collapse: closed
icon: info-circle

Normal VLAN range: 1-1001
Extended VLAN range: 1006-4094
VLANs 1002-1005 are reserved for legacy protocols
```

## Feynman Method Explanation

Imagine a large office building with many departments. Initially, all departments share the same hallway (network), and whenever someone shouts (broadcasts), everyone hears it, causing distraction (network congestion).

Now, let's say we install magical doors that only allow people from the same department to hear each other when they shout. This is what a VLAN does - it creates separate "virtual hallways" within the same physical building.

Each department (VLAN) can communicate freely within itself, but to talk to another department, they need to go through a special room (router) that connects all departments. This way, we've organized the office (network) more efficiently, reduced noise (broadcast traffic), and improved security (departments can't directly access each other).

The magical doors (switches) can be configured to allow certain people (ports) to access specific departments (VLANs) or even multiple departments (trunk ports).

## Relevant Commands

Create a VLAN:
```
vlan <vlan-id>
name <vlan-name>
```

Assign a port to a VLAN (Access Mode):
```
interface <interface-id>
switchport mode access
switchport access vlan <vlan-id>
```

Configure a Trunk Port:
```
interface <interface-id>
switchport mode trunk
switchport trunk allowed vlan <vlan-list>
```

Verify VLAN Configuration:
```
show vlan
show interfaces trunk
```

Configure Inter-VLAN Routing (Router-on-a-Stick):
```
interface <interface-id>.<subinterface-id>
encapsulation dot1q <vlan-id>
ip address <ip-address> <subnet-mask>
```

```ad-tip
title: Native VLAN Configuration
collapse: closed
icon: lightbulb

Configure native VLAN on a trunk:
switchport trunk native vlan <vlan-id>
Always ensure native VLAN matches on both ends of a trunk link.
```

Shut down a VLAN on a local switch:
```
vlan <vlan-id>
shutdown
```

Suspend a VLAN across the VTP domain:
```
vlan <vlan-id>
state suspend
```

Reactivate a suspended VLAN:
```
vlan <vlan-id>
state active
```

Verify VLAN status:
```
show vlan
```

```ad-info
title: VLAN Shutdown vs. Suspend
collapse: closed
icon: info-circle

- Shutdown: Affects the VLAN only on the local switch
- Suspend: Affects the VLAN across the entire VTP domain (if VTP is in use)
```

```ad-note
title: VLAN Status in 'show vlan brief'
collapse: closed
icon: terminal

When you use the 'show vlan brief' command:
- A shutdown VLAN will show status as 'act/lshut' (active but locally shut down)
- A suspended VLAN will show status as 'sus' (suspended)
```
## Related RFCs

1. [RFC 5517 - Cisco Systems' Private VLANs: Scalable Security in a Multi-Client Environment](https://datatracker.ietf.org/doc/html/rfc5517)
   - Describes the concept and implementation of Private VLANs

2. [RFC 3069 - VLAN Aggregation for Efficient IP Address Allocation](https://datatracker.ietf.org/doc/html/rfc3069)
   - Discusses techniques for efficient IP address allocation in VLAN environments

3. [IEEE 802.1Q - Virtual LANs](https://standards.ieee.org/standard/802_1Q-2018.html)
   - While not an RFC, this IEEE standard defines VLAN tagging and is crucial for understanding VLANs

## Cisco Documentation and Whitepapers

1. [Configuring VLANs](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/16-12/configuration_guide/vlan/b_1612_vlan_9300_cg/configuring_vlan.html)
   - Comprehensive guide on VLAN configuration for Catalyst 9300 switches

2. [InterVLAN Routing](https://www.cisco.com/c/en/us/support/docs/lan-switching/inter-vlan-routing/14976-50.html)
   - Detailed explanation of inter-VLAN routing concepts and configuration

3. [Understanding VLAN Trunk Protocol (VTP)](https://www.cisco.com/c/en/us/support/docs/lan-switching/vtp/10558-21.html)
   - In-depth look at VTP, its modes, and configuration

4. [LAN Switching Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/lanswitch/configuration/xe-16/lanswitch-xe-16-book.html)
   - Comprehensive guide covering various aspects of LAN switching, including VLANs

```ad-warning
title: Security Consideration
collapse: closed
icon: shield-alt

Be aware of VLAN hopping attacks. Mitigate by:
1. Disabling DTP (Dynamic Trunking Protocol) on non-trunk ports
2. Using dedicated VLAN IDs for trunk links
3. Configuring unused ports in a protected VLAN
```

## Conclusion

VLANs are a fundamental concept in modern network design, offering improved security, performance, and manageability. By logically segmenting a network, VLANs allow for more efficient use of network resources and better traffic isolation. Understanding VLAN configuration, including access and trunk ports, inter-VLAN routing, and VLAN tagging, is crucial for network administrators and a key component of the CCNP ENCOR exam.

---
# Reference