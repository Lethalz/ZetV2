2408031955
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# VTP AND DTP

# VTP (VLAN Trunking Protocol) and DTP (Dynamic Trunking Protocol)

## My Understanding
[Space for your own notes and understanding of the topic]

## Fundamentals

### VTP (VLAN Trunking Protocol)

VTP is a Cisco proprietary Layer 2 messaging protocol used to manage the addition, deletion, and renaming of VLANs on a network-wide basis.

Key Concepts:
1. VTP Domain: A group of switches sharing VLAN information
2. VTP Modes: Server, Client, Transparent, Off (VTPv3 only)
3. VTP Advertisements: Summary, Subset, Request
4. VTP Version: v1, v2, v3 (each with different capabilities)

### DTP (Dynamic Trunking Protocol)

DTP is a Cisco proprietary protocol that allows switches to dynamically negotiate the formation of a trunk link.

Key Concepts:
1. DTP Modes: Auto, Desirable, Trunk, Access, Nonegotiate
2. Negotiation Process: Determines whether a link should be a trunk or access port
3. Encapsulation: Negotiates between ISL and 802.1Q (on supported platforms)

```ad-warning
title: Security Consideration
collapse: closed
icon: shield-alt

Both VTP and DTP can be exploited in VLAN hopping attacks. Consider disabling them in high-security environments.
```

## VTP Deep Dive

### VTP Modes

1. Server Mode:
   - Can create, modify, and delete VLANs
   - Sends and forwards VTP advertisements
   - Synchronizes VLAN information

2. Client Mode:
   - Cannot create, modify, or delete VLANs
   - Sends and forwards VTP advertisements
   - Synchronizes VLAN information

3. Transparent Mode:
   - Can create, modify, and delete local VLANs
   - Forwards VTP advertisements
   - Does not synchronize its VLAN information

4. Off Mode (VTPv3 only):
   - Similar to transparent mode but doesn't forward VTP advertisements

### VTP Pruning

VTP pruning increases available bandwidth by restricting flooded traffic to links that the traffic must use to reach the destination devices.

### VTP Version Comparison

| Feature                   | VTPv1 | VTPv2 | VTPv3 |
|---------------------------|-------|-------|-------|
| Supports Private VLANs    | No    | No    | Yes   |
| Supports Extended VLANs   | No    | No    | Yes   |
| Hidden Password           | No    | No    | Yes   |
| Instance-based Operation  | No    | No    | Yes   |

```ad-tip
title: VTPv3 Primary Server
collapse: closed
icon: lightbulb

In VTPv3, only the primary server can make and propagate changes to the VLAN database.
```

### VTP Configuration and Verification

Basic VTP Configuration:
```cisco
Switch(config)# vtp domain mydomain
Switch(config)# vtp mode {server | client | transparent | off}
Switch(config)# vtp version {1 | 2 | 3}
Switch(config)# vtp password mypassword
```

VTP Verification Commands:
```cisco
Switch# show vtp status
Switch# show vtp password
Switch# show vtp counters
```

## DTP Deep Dive

### DTP Modes and Resulting Link Types

| Switch 1   | Switch 2   | Resulting Link Type |
|------------|------------|---------------------|
| Access     | Access     | Access              |
| Access     | Dynamic Auto | Access            |
| Access     | Dynamic Desirable | Access       |
| Access     | Trunk      | Limited Connectivity |
| Dynamic Auto | Dynamic Auto | Access          |
| Dynamic Auto | Dynamic Desirable | Trunk      |
| Dynamic Auto | Trunk     | Trunk              |
| Dynamic Desirable | Dynamic Desirable | Trunk |
| Dynamic Desirable | Trunk | Trunk             |
| Trunk      | Trunk      | Trunk               |

### DTP Configuration and Verification

Basic DTP Configuration:
```cisco
Switch(config-if)# switchport mode {access | dynamic auto | dynamic desirable | trunk}
Switch(config-if)# switchport nonegotiate
```

DTP Verification Command:
```cisco
Switch# show dtp interface gigabitethernet 1/0/1
```

### Understanding 'show dtp interface' Output

```ad-info
title: DTP Interface Status Abbreviations
collapse: closed
icon: info-circle

TOS: Trunk Operating Status
TAS: Trunk Administrative Status
TNS: Trunk Negotiation Status
TOT: Trunk Operating Type
TAT: Trunk Administrative Type
TNT: Trunk Negotiation Type
```

Example output interpretation:

```
TOS/TAS/TNS: ON/ON/NA
TOT/TAT/TNT: 802.1Q/802.1Q/NA
```

This indicates:
- The interface is operating as a trunk (TOS: ON)
- It's administratively set as a trunk (TAS: ON)
- Negotiation is not applicable (TNS: NA)
- It's using 802.1Q encapsulation for both operation and administration
- Negotiation type is not applicable (forced trunk mode)

## Relevant Commands

VTP Commands:
```cisco
vtp mode {server | client | transparent | off}
vtp domain domain-name
vtp password password
vtp pruning
show vtp status
```

DTP Commands:
```cisco
switchport mode {access | trunk | dynamic auto | dynamic desirable}
switchport nonegotiate
show interfaces trunk
show dtp interface interface-id
```

## Related RFCs

While VTP and DTP are Cisco proprietary protocols and don't have specific RFCs, understanding related standards is beneficial:

1. [RFC 2674 - Definitions of Managed Objects for Bridges with Traffic Classes, Multicast Filtering and Virtual LAN Extensions](https://datatracker.ietf.org/doc/html/rfc2674)
   - Provides definitions for managing VLANs

2. [IEEE 802.1Q - Virtual LANs](https://standards.ieee.org/standard/802_1Q-2018.html)
   - The standard for VLAN tagging, which VTP and DTP work alongside

## Cisco Documentation and Whitepapers

1. [Configuring VTP](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/16-12/configuration_guide/vlan/b_1612_vlan_9300_cg/configuring_vtp.html)
   - Comprehensive guide on VTP configuration for Catalyst 9300 switches

2. [Understanding VLAN Trunk Protocol (VTP)](https://www.cisco.com/c/en/us/support/docs/lan-switching/vtp/10558-21.html)
   - In-depth explanation of VTP concepts and operation

3. [Configuring VLAN Trunks](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/16-12/configuration_guide/vlan/b_1612_vlan_9300_cg/configuring_vlan_trunks.html)
   - Detailed information on configuring VLAN trunks, including DTP

4. [LAN Switching Configuration Guide, Cisco IOS XE Amsterdam 17.3.x](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/17-3/configuration_guide/vlan/b_173_vlan_9300_cg.html)
   - Comprehensive guide covering various aspects of LAN switching, including VTP and DTP

```ad-warning
title: Version Compatibility
collapse: closed
icon: exclamation-triangle

Ensure all switches in a VTP domain are running compatible VTP versions. Mixing versions can lead to unexpected behavior.
```

## Conclusion

Understanding VTP and DTP at a CCNP level involves not just knowing their basic operations, but also comprehending their security implications, version differences, and detailed configuration options. While these protocols can simplify VLAN management and trunk negotiation, they also introduce potential vulnerabilities that need to be carefully considered in network design and security posture.


---
# Reference