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
## VSL/VSS initialization

- When a switch boots, the config is parsed for VVSL configurations then the VSL interfaces are then enabled
- **VSLP** (Virtual Switch Link Protocol) is used to establish and maintain the VSL/VSS
- **VSLP** has two components 1. LMP and 2. RRP
- **LMP** (Link Management Protocol) performs the following functions:
	  1. Verifies link integrity by establishing bidirectional traffic forwarding
	  2. Exchanges switch IDs (Set one switch as "1" and the other as "2")
	  3. Exchanges other required information
**RRP**(Role Resolution Protocol) performs the following functions:
1. Determines if the hardware and the software versions of the switches are compatible.
2. Determines the active switch and the standby switch

Depending on the compatibility checks, the stack will come up in one of two modes: 
1. **RPR**( Route-Processor Redundancy) mode
2. **NSF/SSO**(Nonstop Forwarding/Stateful Switchover) mode

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

## Stackwise Initialization
When all switches in the stack are powered on, **SDP** (Stack Discovery Protocol) uses broadcast messages (via the stack connections ) to discover the stakc topology

After all switches in the stack have been discovered switch numbers are determined
	- Switches must have a unique number (1 to 8) 
	- Automatically determined, but can be manually changed.
After Discovery, and *Active* switch is elected
	- Switches that boot up within a 2-minute election window participate
		- Highest priority (default 1, highest 15), lowest MAC are taken into account (int that order).
2 minutes after the *Active* election, a *Standby* switch is elected.
	- Same parameters as above.
Other switches will be *members.*
	- Active in forwarding, but not ready to immediately take over for a failed active switch.\

Switches added **after the 2-minute** time window will become members, because the election happened and another is not triggered.

```ad-question
collapse: yes
title:What happens if you connect a switch after the election


When you connect a new switch to an existing StackWise stack after the initial election process, here's what typically happens:

1. Discovery:
    - The existing stack detects the new switch.
    - The new switch goes through a discovery process to learn about the stack.
2. Software Version Check:
    - The stack checks the software version of the new switch.
    - If it doesn't match the stack's version, the new switch may be put into a version mismatch state.
3. Configuration Sync:
    - If the software versions are compatible, the active switch in the stack will push its configuration to the new switch.
4. Stack Membership:
    - The new switch is assigned the next available switch number in the stack.
5. No Re-election:
    - The active and standby switches do not change. The new switch joins as a member switch.
6. Potential Reboot:
    - If there's a software version mismatch, the new switch may need to be manually updated and rebooted to join the stack.
7. Role Negotiation:
    - While it doesn't trigger a re-election, the new switch participates in role negotiation for future elections.
8. Stack Ring Reconfiguration:
    - The stack ring is reconfigured to include the new switch in the data path.
9. Feature Compatibility Check:
    - The stack checks if all features running on existing switches are supported on the new switch.

Key Points:

- The process is generally non-disruptive to the existing stack operation.
- No immediate change in active/standby roles occurs.
- Ensure software compatibility for smooth integration.
```
## StackWise Virtual

StackWise Virtual combines elements of VSS and StackWise, designed for newer switch models.

Key features:
1. Supports Catalyst 3850, 9000 series, and some Nexus switches
2. Uses StackWise Virtual Link (SVL) for inter-switch communication
3. Provides active/active supervisor redundancy
4. SVL  frames are encapsulated with a 64-byte StackWise Virtual Header


## SVL Initialization

When a switch boots, the config is parsed for SVL congiurations then enabled

Two protocols are used to iniitale the SVL and the stack: LMP and SDP 

LMP: (Same as [VSS/VSL])  performs the following functions: 
1. Verifies link integrity by establishing bidirectional traffic forwarding 
2. sends periodic 'hello' messages to maintain the SVL.
3. Exchanges other required information. 

SDP (StackWise Discovery Protocol) performs the following fuctions:
1. Determines if the hardware and software versions of the switches are compatible
2. Determines the active switch and standby switch.

## Comparison

| Feature            | VSS            | StackWise   | StackWise Virtual |     |
| ------------------ | -------------- | ----------- | ----------------- | --- |
| Max Switches       | 2              | Up to 9     | 2                 |     |
| Switch Types       | Chassis        | Fixed       | Both              |     |
| Redundancy         | Active/Standby | N+1         | Active/Active     |     |
| Link Type          | VSL            | Stack Cable | SVL               |     |
| Distance/Range     | Long/KM        | Short/M     | Long/KM           |     |
| Relevant Protocols | VSLP,LMP,RRP   | SDP         | LMP,SDP           |     |

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

1. [Virtual Switching Systems (VSS) White Paper](https://www.cisco.com/c/dam/en/us/products/collateral/interfaces-modules/network-modules/white_paper_c11_429338.pdf)
   - Comprehensive overview of VSS technology, its benefits, and implementation considerations.

2. [Cisco StackWise and StackWise Plus Technology White Paper](https://www.cisco.com/c/en/us/products/collateral/switches/catalyst-3750-series-switches/prod_white_paper09186a00801b096a.html)
   - Detailed explanation of StackWise technology, its evolution, and advantages in network design.

3. [Cisco StackWise Virtual White Paper](https://www.cisco.com/c/dam/en/us/products/collateral/switches/catalyst-3850-series-switches/q-and-a-c67-738577.pdf)
   - StackWise Virtual FAQ

4. [Cisco Catalyst 9000 Switches StackWise Virtual Deployment Guide](https://www.cisco.com/c/en/us/products/collateral/switches/catalyst-9000/nb-06-cat-9k-stack-wp-cte-en.html)
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
![[Pasted image 20240719121958.png]]


![[Pasted image 20240719122035.png]]

![[Pasted image 20240719130849.png]]

# Other Links
## [StackWise Virtual Tips and Tricks](https://community.cisco.com/t5/networking-knowledge-base/stackwise-virtual-tips-and-tricks/ta-p/4922633)
