2407211247
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# SDM Switching Database Manager

# Switching Database Manager (SDM)

## My Understanding
[Space for your own notes and understanding of the topic]

## Fundamentals

Switching Database Manager (SDM) is a feature in Cisco switches that optimizes the use of hardware resources, specifically TCAM (Ternary Content Addressable Memory). SDM templates allocate TCAM for different features such as IP routing, Layer 2 switching, and security.

Key Components:
1. TCAM: High-speed memory used for rapid table lookups in switches.
2. SDM Templates: Predefined resource allocation profiles.
3. Hardware Resources: Various switch features that utilize TCAM.

Types of SDM Templates:
1. Default Template: Balances resources across all features.
2. Access Template: Optimizes resources for Layer 2 switching.
3. Routing Template: Allocates more resources to Layer 3 routing.
4. VLAN Template: Optimizes resources for VLAN configurations.

```ad-info
title: Template Selection
collapse: closed
icon: info-circle

The choice of SDM template depends on the switch's role in the network and the primary functions it needs to perform.
```

## Feynman Method Explanation

Imagine you're organizing a toolbox for different jobs. You have a limited number of compartments (TCAM) and various tools (network features). SDM templates are like different organizer inserts for your toolbox. 

The "Default" insert gives equal space to all tools. The "Access" insert makes more room for screwdrivers (Layer 2 switching). The "Routing" insert allocates more space for wrenches (Layer 3 routing). The "VLAN" insert creates many small compartments for lots of different small tools (VLAN configurations).

By choosing the right insert (SDM template), you optimize your toolbox (switch) for the specific job (network role) you're doing, ensuring you have enough space for the tools you use most often.

## Relevant Commands

Configure SDM Template:
```
sdm prefer {default | access | routing | vlan}
```

Verify Active SDM Template:
```
show sdm prefer
```

Apply New SDM Template:
```
reload
```

```ad-warning
title: Reload Required
collapse: closed
icon: exclamation-triangle

After changing the SDM template, a switch reload is required for the changes to take effect. This will cause a brief network interruption.
```

## Related RFCs

There are no specific RFCs for SDM as it's a Cisco proprietary feature. However, understanding related RFCs can be beneficial:

1. RFC 1213 - Management Information Base for Network Management of TCP/IP-based internets: MIB-II
2. RFC 2233 - The Interfaces Group MIB using SMIv2

## Cisco Documentation and Whitepapers

1. [Configuring SDM Templates](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst3750x_3560x/software/release/12-2_55_se/configuration/guide/3750xscg/swsdm.html)
   - Comprehensive guide on SDM template configuration and usage.

2. [Understanding and Configuring Switching Database Manager on Catalyst Switches](https://www.cisco.com/c/en/us/support/docs/switches/catalyst-3750-series-switches/44921-swdatabase-3750-44921.html)
   - Detailed explanation of SDM concepts and configuration examples.

3. [Cisco Catalyst 3750 Series Switches Data Sheet](https://www.cisco.com/c/en/us/products/collateral/switches/catalyst-3750-series-switches/product_data_sheet0900aecd80371991.html)
   - Includes information on supported SDM templates for specific switch models.

4. [Campus LAN and Wireless LAN Design Guide](https://www.cisco.com/c/en/us/td/docs/solutions/CVD/Campus/cisco-campus-lan-wlan-design-guide.html)
   - Provides context on how SDM templates fit into overall network design.

```ad-tip
title: Best Practices
collapse: closed
icon: lightbulb

When selecting an SDM template, consider not only current network requirements but also future scalability needs. Regularly review and adjust templates as network demands change.
```

## Conclusion

SDM templates are crucial for optimizing switch performance by appropriately allocating TCAM resources. The choice of template depends on the switch's role in the network and the primary features required. Proper configuration and regular review of SDM templates can significantly enhance network efficiency and prepare for future scalability.

---
# Reference