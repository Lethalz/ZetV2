# EtherChannel Configuration Guide: Layer 2 & Layer 3

## Introduction
EtherChannel is a port link aggregation technology that allows grouping of multiple physical Ethernet links into one logical link for increased bandwidth and redundancy. This document covers both Layer 2 and Layer 3 configurations.

## Overview

### Key Concepts
* Maximum of 8 ports per EtherChannel
* All ports must have identical speed and duplex settings
* Load balancing can be based on MAC addresses, IP addresses, or port numbers
* Supports both manual configuration and dynamic protocols (LACP/PAgP)

### Supported Protocols
* LACP (Link Aggregation Control Protocol) - IEEE 802.3ad
* PAgP (Port Aggregation Protocol) - Cisco proprietary
* Static configuration (manual)

## Prerequisites

### Hardware Requirements
* Compatible Cisco switches
* Identical port types and speeds
* Physical connectivity between switches

### Software Requirements
* Compatible IOS versions
* Proper licensing if required

## Layer 2 EtherChannel Configuration

### LACP Configuration Example
```cisco
! Switch 1
Switch1(config)# interface range GigabitEthernet1/0/1-2
Switch1(config-if-range)# channel-group 1 mode active
Switch1(config-if-range)# no shutdown

! Switch 2
Switch2(config)# interface range GigabitEthernet1/0/1-2
Switch2(config-if-range)# channel-group 1 mode passive
Switch2(config-if-range)# no shutdown

! Configure Port-Channel Interface
Switch1(config)# interface port-channel 1
Switch1(config-if)# switchport mode trunk
Switch1(config-if)# switchport trunk allowed vlan 10,20,30
```

### PAgP Configuration Example
```cisco
! Switch 1
Switch1(config)# interface range GigabitEthernet1/0/1-2
Switch1(config-if-range)# channel-group 2 mode desirable
Switch1(config-if-range)# no shutdown

! Switch 2
Switch2(config)# interface range GigabitEthernet1/0/1-2
Switch2(config-if-range)# channel-group 2 mode auto
Switch2(config-if-range)# no shutdown
```

## Layer 3 EtherChannel Configuration

### Layer 3 EtherChannel Example
```cisco
! Switch 1
Switch1(config)# interface range GigabitEthernet1/0/1-2
Switch1(config-if-range)# no switchport
Switch1(config-if-range)# channel-group 3 mode active
Switch1(config-if-range)# no shutdown

Switch1(config)# interface port-channel 3
Switch1(config-if)# no switchport
Switch1(config-if)# ip address 192.168.1.1 255.255.255.0
```

## Protocols and Load Balancing

### LACP Modes
* Active: Initiates LACP negotiations
* Passive: Responds to LACP negotiations
* Both ends must not be passive

### PAgP Modes
* Auto: Responds to PAgP negotiations
* Desirable: Initiates PAgP negotiations
* Both ends must not be in auto mode

### Load Balancing Methods
```cisco
! Configure load-balancing method
Switch(config)# port-channel load-balance src-dst-mac
! Other options include:
! - src-dst-ip
! - src-dst-port
! - src-mac
! - dst-mac
```

## Troubleshooting

### Common Commands
```cisco
! Verify EtherChannel status
Show etherchannel summary
Show etherchannel detail
Show etherchannel load-balance
Show interface port-channel [number]
```

### Common Issues and Solutions

1. **Mismatched Configurations**
   * Verify identical speed/duplex settings
   * Check VLAN configurations
   * Ensure consistent channel-group numbers

2. **Protocol Mismatches**
   * Verify LACP/PAgP modes are compatible
   * Check for consistent protocol usage

3. **Load Balancing Issues**
   * Verify load-balancing method
   * Monitor traffic distribution

### Best Practices
1. Document all EtherChannel configurations
2. Use LACP over PAgP when possible (industry standard)
3. Implement redundant links across different modules/switches
4. Monitor EtherChannel performance regularly
5. Use description commands for documentation

## Reference Documentation

## Official Documentation
* [Cisco EtherChannel Configuration Guide](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/16-12/configuration_guide/lag/b_1612_lag_9300_cg/configuring_etherchannel.html)
* [Cisco Layer 3 and Layer 2 EtherChannel Configuration](https://www.cisco.com/c/en/us/support/docs/lan-switching/etherchannel/98469-ios-etherchannel.html)
* [Cisco EtherChannel Load Balancing](https://www.cisco.com/c/en/us/support/docs/lan-switching/etherchannel/12023-4.html)
* [IEEE 802.3ad Standard](https://standards.ieee.org/standard/802_3ad-2000.html)

[Previous content remains the same...]

## Reference Documentation

### Related RFCs and Standards
* [IEEE 802.3ad - Link Aggregation Control Protocol](https://standards.ieee.org/standard/802_3ad-2000.html)
* [RFC 7424 - LACP Extensions](https://datatracker.ietf.org/doc/rfc7424/)
* [Cisco EtherChannel Design Guidelines](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus5000/sw/configuration/guide/cli/CLIConfigurationGuide/EtherChannel.html)
* [Cisco Port Channel Technical Implementation Guide](https://www.cisco.com/c/en/us/support/docs/switches/catalyst-6500-series-switches/12027-53.html)

### Additional Resources
* [Cisco Configuration Examples and TechNotes](https://www.cisco.com/c/en/us/support/docs/lan-switching/etherchannel/98469-ios-etherchannel.html)
* [Cisco Nexus EtherChannel Configuration](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus9000/sw/93x/interfaces/configuration/guide/b-cisco-nexus-9000-nx-os-interfaces-configuration-guide-93x/b-cisco-nexus-9000-nx-os-interfaces-configuration-guide-93x_chapter_0101.html)
* [LACP Configuration Best Practices]([https://www.cisco.com/c/en/us/support/docs/switches/catalyst-3750-series-switches/98469-ios-etherchannel.html](https://www.cisco.com/c/en/us/td/docs/ios/12_2sb/feature/guide/gigeth.html))

