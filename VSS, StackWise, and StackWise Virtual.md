2407171455
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# VSS, StackWise, and StackWise Virtual


# VSS, StackWise, and StackWise Virtual

## My Understanding

## Overview

These technologies allow multiple physical switches to operate as a single logical switch, providing benefits in terms of management, redundancy, and performance.

## Virtual Switching System (VSS)

VSS allows two physical chassis switches to operate as a single logical switch.

Key features:
1. Supports Cisco Catalyst 4500-X and 6500 series switches
2. Uses Virtual Switch Link (VSL) for inter-switch communication
3. Provides active/standby supervisor redundancy

```ad-info
title: VSS Origin
collapse: closed
icon: history

VSS was introduced by Cisco in 2008 on the Catalyst 6500 series, revolutionizing the concept of switch virtualization in enterprise networks.
```

## StackWise

StackWise is a stacking technology for fixed configuration switches.

Key features:
1. Supports up to 9 switches in a stack (model dependent)
2. Uses a specialized stacking cable for interconnection
3. Provides distributed forwarding across the stack

```ad-tip
title: StackWise Compatibility
collapse: closed
icon: puzzle-piece

Ensure all switches in a StackWise configuration are running the same IOS version to avoid compatibility issues and unexpected behavior.
```

## StackWise Virtual

StackWise Virtual combines elements of VSS and StackWise, designed for newer switch models.

Key features:
1. Supports Catalyst 3850, 9000 series, and some Nexus switches
2. Uses StackWise Virtual Link (SVL) for inter-switch communication
3. Provides active/active supervisor redundancy

## Comparison

| Feature | VSS | StackWise | StackWise Virtual |
|---------|-----|-----------|-------------------|
| Max Switches | 2 | Up to 9 | 2 |
| Switch Types | Chassis | Fixed | Both |
| Redundancy | Active/Standby | N+1 | Active/Active |
| Link Type | VSL | Stack Cable | SVL |

## Configuration Examples

### VSS Configuration

1. Configure switch identifiers:
```
switch 1 priority 110
switch 2 priority 100
```

2. Configure VSL:
```
interface port-channel 10
 switchport
 switch virtual link 1
!
interface TenGigabitEthernet1/1/1
 channel-group 10 mode on
 no shutdown
```

### StackWise Configuration

StackWise is typically plug-and-play, but you can set switch priorities:

```
switch 1 priority 15
switch 2 priority 14
switch 3 priority 13
```

### StackWise Virtual Configuration

1. Enable StackWise Virtual:
```
stackwise-virtual
```

2. Configure SVL:
```
interface range TenGigabitEthernet1/0/1-2
 stackwise-virtual link 1
```

```ad-warning
title: Configuration Caution
collapse: closed
icon: exclamation-triangle

Always save your configuration and schedule a maintenance window when implementing these technologies. The process often requires a reboot and can cause temporary network disruption.
```

## Best Practices

1. Use redundant VSL/SVL links to prevent single points of failure
2. Implement Multichassis EtherChannel (MEC) for load balancing and redundancy
3. Keep software versions consistent across all members
4. Regularly backup configurations of all stack members

```ad-tip
title: Upgrade Strategy
collapse: closed
icon: level-up-alt

When upgrading software on stacked switches, use the In-Service Software Upgrade (ISSU) feature when available to minimize downtime.
```

## Troubleshooting

Common commands for troubleshooting:

1. VSS:
   - `show switch virtual`
   - `show switch virtual link`

2. StackWise:
   - `show switch`
   - `show platform stack manager all`

3. StackWise Virtual:
   - `show stackwise-virtual`
   - `show stackwise-virtual neighbors`

```ad-info
title: Logging Best Practice
collapse: closed
icon: book

Enable logging on all stack members and consider using a centralized syslog server to facilitate troubleshooting in complex stacking scenarios.
```

## Cisco Documentation and Whitepapers

1. [Virtual Switching Systems (VSS) White Paper](https://www.cisco.com/c/en/us/products/collateral/switches/catalyst-6500-virtual-switching-system-1440/prod_white_paper0900aecd806ed95c.html)
   - Comprehensive overview of VSS technology, its benefits, and implementation considerations.

2. [Cisco StackWise and StackWise Plus Technology White Paper](https://www.cisco.com/c/en/us/products/collateral/switches/catalyst-3750-series-switches/prod_white_paper09186a00801b096a.html)
   - Detailed explanation of StackWise technology, its evolution, and advantages in network design.

3. [Cisco StackWise Virtual White Paper](https://www.cisco.com/c/en/us/products/collateral/switches/catalyst-9000/white-paper-c11-739988.html)
   - In-depth look at StackWise Virtual, its architecture, and how it enhances network resiliency.

4. [Cisco Catalyst 9000 Switches StackWise Virtual Deployment Guide](https://www.cisco.com/c/en/us/products/collateral/switches/catalyst-9000/guide-c07-743901.html)
   - Practical guide for deploying StackWise Virtual in Catalyst 9000 series switches.

5. [High Availability: Cisco VSS, Cisco StackWise and StackWise Virtual Technologies Design Guide](https://www.cisco.com/c/en/us/td/docs/solutions/Enterprise/Campus/HA_campus_DG/hacampusdg.html)
   - Design guide focusing on high availability implementations using VSS, StackWise, and StackWise Virtual.

```ad-tip
title: Additional Resources
collapse: closed
icon: book-reader

Cisco's documentation is regularly updated. Always check the latest version of these documents for the most current information and best practices.
```

---
# Reference