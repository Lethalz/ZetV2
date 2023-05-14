2301271213
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# RSTP and EtherChannel Configuration

### Per-VLAN spanning tree 

Original STP and RSTP did not take VLANs into account. Without any extensions to the protocol, the BDPUs would travel in a native VLAN and there would be just one spanning tree (CST, common spanning tree) for all VLANs. Per-VLAN spanning trees allow for better load balancing.

There are three multiple spanning tree protocols available:

-   PVST+ - Per-VLAN Spanning Tree, a Cisco-proprietary extension to classic STP. One spanning tree for each enabled VLAN.
    
-   RPVST+ - Rapid Per-VLAN Spanning Tree, a Cisco-proprietary extension to RSTP. One spanning tree for each enabled VLAN.
    
-   MSTP – Multiple Spanning Tree Protocol, IEEE standard, can define an arbitrary number of spanning trees, defined in 802.1Q amendment 802.1s.
    

All three protocols embed the VLAN number in the priority part of Bridge ID. 2 bytes originally reserved for priority are divided into 4-bits of priority and 12 bits System ID Extension. As a result:

1.  newpriority = floor(oldpriority/4096)
    
2.  System ID Extension = oldpriority%4096
    

They also VLAN-tag the BPDUs, whereas the bare STP/RSTP sends them in native VLAN.

Selecting the protocol in use:

-   (config)# spanning-tree mode mst – use MSTP
    
-   (config)# spanning-tree mode rapid-pvst – use RPVST+
    
-   (config)# spanning-tree mode pvst – use PVST+
    

Set priority:

-   (config)# spanning-tree vlan n priority m – where m is 0 or a multiple of 4096
    
-   (config)# spanning-tree vlan n root primary – set priority to 24576 or to a value 4096 less than the current lowest priority setting in the network.
    
-   (config)# spanning-tree vlan n root secondary – set priority to 28672, which in ordinary circumstances would be higher than root but lower than other switches.
    

Set port cost:

-   (config-if) spanning-tree [vlan n] cost x – manually set port cost for a given port. vlan parameter is optional. If given, set the cost only for a particular VLAN’s spanning tree, if not, for all spanning trees.
    

--- 

### Configuring L2 EtherChannel
    

An EtherChannel is a bundle of physical links that, for all intents and purposes, act as a single link from the point of view of STP/RSTP. It also provides redundancy – should one of the bundled physical links fail, the EtherChannel as a whole will continue functioning.

Manual configuration:

-   (config-if)# channel-group *n* mode *on* – assign a port to the EtherChannel with ID n
    

Show EtherChannel status:

-   # show etherchannel n summary – show summary status – state, ports bundled – of the EtherChannel with ID n
    
-   # show etherchannel n port-channel – show detailed info – including autonegotiation – on the EtherChannel with ID n
    

EtherChannel virtual interfaces are named Port-channels (usually shortened to Pon), where n is the ID, eg. Po1 for ID 1.

Autonegotiation can be achieved with two protocols: Cisco-proprietary PAgP (Port Aggregation Protocol) and IEEE standard LACP (Link Aggregation Control Protocol). They are mostly analogous. At least one side of the link must be set to initiate autonegotiation, the other can be set to wait for the other to begin. This is done with:

-   (config-if)# channel-group n mode active – Use LACP, initiate autonegotiation
    
-   (config-if)# channel-group n mode passive – Use LACP, wait for the other side to initiate autonegotiation
    
-   (config-if)# channel-group n mode desirable – Use PAgP, initiate autonegotiation
    
-   (config-if)# channel-group n mode auto – Use PAgP, wait for the other side to initiate autonegotiation
    

Manual configuration (mode on) disables EtherChannel autonegotiation and cannot be used with autonegotiation enabled on the other side of the link. Active-active or desirable-desirable will work, passive-passive and auto-auto will not.

Troubleshooting EtherChannel:

Regardless whether autonegotiation was used or not, the following parameters must match across all bundled ports:

-   Speed
    
-   Duplex setting
    
-   VLAN mode: all must be trunk or all must be access
    
-   Access VLAN, if port set as an access port
    
-   Allowed VLANs and native VLAN, if port set as trunk port
    
-   STP settings (port cost)
    

If there is a mismatch, the PortChannel virtual interface will be put in an err-disabled state. To recover, fix the underlying mismatch and then do:

-   (config-if)# shutdown
    
-   (config-if)# no shutdown
    

Sidenote: shutdown and no shutdown command automatically apply to physical interfaces bundled in a given PortChannel

Load distribution: EtherChannel can distribute its load between all links based on a number of criteria. This is set by:

-   (config)# port-channel load-balance method – where method is one of the following (what is the default???):
    

-   src-mac
    
-   dst-mac
    
-   src-dst-mac
    
-   src-ip
    
-   dst-ip
    
-   src-dst-ip
    
-   src-port
    
-   dst-port
    
-   src-dst-port
    

-   # show etherchannel load-balance – shows the enabled method
    
-   # test etherchannel load-balance interface PoN pol {mac|ip|port} src dst – simulate which link would be used to carry traffic between given source and destination
---
# Reference