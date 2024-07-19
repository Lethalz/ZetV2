2407191339
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# SSO Stateful Switchover

# SSO, NSF, and GR

## My Understanding

SSO provides seemless transfer from active to backup for control-plane processors or RSPs. 
## Overview

SSO (Stateful Switchover), NSF (Non-Stop Forwarding), and GR (Graceful Restart) are technologies designed to maintain network availability during planned or unplanned control plane disruptions.

## Stateful Switchover (SSO)

SSO provides redundancy for the control plane, allowing a backup Route Processor (RP) to take over if the primary RP fails.

Key features:
1. Maintains Layer 2 protocol states
2. Syncs configuration and protocol state information between active and standby RPs
3. Enables sub-second failover for supported protocols
4. SSO fully boots and initializes the Standby RP
5. Incremental synchronization is used to sync any changes from Active to Standby (Checkpointing)
6. Layer 2 protocols are initialized (stp lacp pagp vtp port security) Layer 2 is maintained
7. Layer 3 Protocol states are not synced (routes are cleared from routing table)



```ad-info
title: SSO Support
collapse: closed
icon: info-circle

SSO is supported on various Cisco platforms, including Catalyst switches and high-end routers. Check your specific model's documentation for SSO capabilities.
```

## Non-Stop Forwarding (NSF)

NSF works in conjunction with SSO to maintain packet forwarding during a switchover. Allows Line cards to forward packets at L3 while the RP fails over.

Key features:
1. Continues forwarding packets based on existing CEF (Cisco Express Forwarding) information
2. Works with routing protocols to rebuild routing information after a switchover
3. Minimizes packet loss during failover
4. NSF can't be configured.

```ad-tip
title: NSF and Routing Protocols
collapse: closed
icon: lightbulb

For NSF to work effectively, neighboring routers must be NSF-aware or NSF-capable. Ensure your network design considers NSF support across all devices.
```

## Graceful Restart (GR)

GR is a protocol-independent feature that allows a router to continue packet forwarding during a restart of its control plane.

Key features:
1. Supported by various routing protocols (BGP, OSPF, IS-IS)
2. Allows neighbors to assist in the restart process
3. Reduces the impact of routing flaps caused by restarts

```ad-example
title: GR in BGP
collapse: closed
icon: network-wired

In BGP, a router undergoing GR (the restarting router) informs its peers that it's restarting. The peers then maintain their routing information for the restarting router, allowing it to rebuild its BGP table without causing route flaps.
```

## Comparison

| Feature     | SSO                      | NSF                          | GR                         |
| ----------- | ------------------------ | ---------------------------- | -------------------------- |
| Focus       | Control Plane Redundancy | Continuous Packet Forwarding | Protocol-level Restart     |
| Scope       | Device-level             | Network-level                | Protocol-level             |
| Key Benefit | Fast Failover            | Minimal Packet Loss          | Reduced Routing Disruption |

## Configuration Examples

### SSO Configuration (Cisco IOS)

```
redundancy
 mode sso
```

### NSF Configuration (for OSPF)

```
router ospf 1
 nsf
```

### GR Configuration (for BGP)

```
router bgp 65000
 bgp graceful-restart
```

```ad-warning
title: Configuration Impact
collapse: closed
icon: exclamation-triangle

Enabling these features can impact CPU usage and memory consumption. Test thoroughly in a non-production environment before deployment.
```

## Best Practices

1. Use SSO and NSF together for optimal high availability
2. Ensure all devices in the failure domain support the required features
3. Regularly test failover scenarios to ensure proper operation
4. Monitor system resources, as these features can increase CPU and memory usage

```ad-tip
title: Design Consideration
collapse: closed
icon: drafting-compass

When designing for high availability, consider using these features in conjunction with redundant hardware and diverse network paths.
```

## Troubleshooting

Common commands for verifying SSO, NSF, and GR:

1. SSO:
   - `show redundancy states`
   - `show redundancy`

2. NSF:
   - `show ip protocols`
   - `show ip ospf nsf`

3. GR:
   - `show ip bgp neighbors`
   - `show ip ospf neighbor`

```ad-info
title: Logging Best Practice
collapse: closed
icon: book

Enable logging for SSO, NSF, and GR events to facilitate troubleshooting and to verify proper operation during switchovers.
```

## Cisco Documentation and Whitepapers

1. [Configuring Stateful Switchover](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ha/configuration/xe-16/ha-xe-16-book/ha-config-stateful-switchover.html)
   - Detailed guide on SSO configuration and operation.

2. [Configuring Cisco Nonstop Forwarding](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ha/configuration/xe-16/ha-xe-16-book/ha-config-nsf.html)
   - Comprehensive overview of NSF implementation in Cisco IOS.

3. [BGP Graceful Restart](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/iproute_bgp/configuration/xe-16/irg-xe-16-book/bgp-graceful-restart.html)
   - In-depth look at GR in BGP, including configuration and verification.

4. [NSF/SSO and Graceful Restart for MP-BGP IPv4/IPv6](https://www.cisco.com/c/en/us/products/collateral/ios-nx-os-software/border-gateway-protocol-bgp/white_paper_c11-492271.html)
   - Whitepaper discussing the integration of NSF, SSO, and GR in BGP environments.

5. [High Availability Configuration Guide, Cisco IOS XE Gibraltar 16.12.x](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ha/configuration/xe-16-12/ha-xe-16-12-book.html)
   - Comprehensive guide covering various high availability features including SSO, NSF, and GR.

```ad-tip
title: Additional Resources
collapse: closed
icon: book-reader

Cisco regularly updates its documentation. Always refer to the latest version for the most current information and best practices.
```

## Conclusion

SSO, NSF, and GR are crucial technologies for maintaining network availability and minimizing disruptions during control plane events. When properly implemented, they significantly enhance network resilience and reduce downtime.

```ad-warning
title: Implementation Complexity
collapse: closed
icon: cogs

While these technologies offer significant benefits, they also introduce complexity to network operations. Ensure your team is properly trained and has the necessary expertise to implement and manage these features effectively.
```

---
# Reference