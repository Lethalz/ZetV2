2301021502
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Implementing VLANs



Usable VLAN IDs: 
- 1-1001 (standard), 
- 1006-4094 (extended). Extended range is enabled only on newer Cisco devices.

Creating VLAN and assigning interfaces:

-   (config)# **vlan** *n* – Create a VLAN with ID n and enter its configuration context
    
-   (config-vlan)# **name**  name – Assign a human readable name to a give VLAN
    
-   (config-if)# **switchport access vlan** *n* – associate the port with VLAN n
    
-   (config-if)# **switchport mode access** – force the port to access mode (i.e. do not autonegotiate and do not accept trunking)

- (config-if)# **interface range** fastethernet 0/13 - 14 - Selects multiple Interfaces at once for mass configuration. 

Show VLAN config:

-   # **show vlan brief** – show all enabled VLANs and a list of interfaces assigned to each
    
-   # **show vlan id** *n* – as above + brief information on spanning tree protocols
    
-  # **show running-config** - If this does not list any VLANs you may have VTP on.

Disable VLAN:

-   (config-vlan)# **shutdown** – disable VLAN OR
    
-   (config)# **shutdown vlan** *n*
    

### Trunking
    

There are two trunking protocols: 
- 802.1Q (IEEE standard) 
- ISL (Inter-Switch Link, Cisco proprietary and deprecated). 

One can set the protocol with:
-   (config-if)# **switchport trunk encapsulation** {dot1q | isl | negotiate}
    

Controlling whether a port is trunking:

-   (config-if)# **switchport mode access** – never trunk
    
-   (config-if)# **switchport mode trunk** – force trunking
    
-   (config-if)# **switchport mode dynamic auto** – trunk if the other side is set to trunk or to dynamic desirable, access otherwise
    
-   (config-if)# **switchport mode dynamic desirable** – initiate trunking with the other side, trunk if the other side is set to dynamic auto, dynamic desirable or trunk, access otherwise
- (config-if)#**switchport nonegotiate** - Disables DTP
    

Dynamic trunk negotiation is done using **Dynamic Trunking Protocol** (DTP). 
DTP frames travel over *native VLAN* (i.e. untagged), and native VLAN settings must be **identical** on both devices. 

Link will fail if one interface is set to trunk and the other to access. 

One caveat: if VTP is enabled (even in transparent mode), the VTP domain on both switches must match for DTP to work.

Set allowed VLANs:

-   (config-if)# **switchport trunk allowed** *vlan range* (can be specified multiple times)

![[158a04e3bd4be61699218c4c353004c8.png]]

>[!Note] 
>Daisy-chained Phones, the interface that phone is using needs to be configured as a Truck port because it is going to be transmitting data from multiple vlans namely the phone and the accompanying PC connected to the back of it . VMs are VLAN aware and can switch between VLANs whenever they want so the interface they are plugged into also needs to be trunked
>

For the IP phones they aren't going to be configured as a trunk port but as an 'access' port with trunk qualities

![[19994a377601b0a218f06e47fca7fbbb.png]]

Access would be data
Voice would be Phone

## Native VLAN

<img src = 'https://i.gyazo.com/6fd454c0983abe77bfda831483a2f024.png'>


## Allowed VLANs Config

Lets say you have a switch that has vlan 10, 30, 40 on it. but you have another switch that only has 10, 30. Allowing 40 traffic to go to the switch is a waste of time and bandwidth here is how you change the allowed VLANs on a switch


![[dfa30cd5e504dabd742053b09857c4d7.png]]

### Review config

-   # **show interfaces** ifname **switchport** – show settings of a given port
    
-   # **show interfaces trunk** – show all trunking ports, including information on VLANs allowed on a given port and VLANs pruned by STP
    

Cisco IP phones contain a small switch that de facto trunks towards the rest of the network and provides an access port for a PC. The voice VLAN can be set with:

-   (config-if)# switchport voice vlan n
    
	 
	 
### VLAN Trunking Protocol
    

**VTP (VLAN Trunking Protocol)** – allows a device to advertise VLAN info (IDs enabled and names) and others to receive it and update their configuration accordingly. OCG recommends disabling it, as VTP can mess up VLAN config in the whole network if misconfigured:

-   (config)# vtp mode transparent OR
    
-   (config)# vtp mode off
    

However, VTP configuration does appear on the exam, so best to describe the protocol and its configuration. There are 3, mutually incompatible VTP versions: VTPv1, VTPv2, VTPv3. VTPv3, in particular, addresses many of the protocol’s shortcomings and makes it much less dangerous to use. VTP works on trunk links only.

VTP can operate in three modes:

-   Server (default)– creates, modifies and deletes VLANs, stores VLAN information locally in NVRAM, originates and forwards VTP advertisements and synchronises VTP information
    
-   Client – Listens for VTP advertisements and forwards them. A client’s VLAN database is completely dependent on VTP – a client cannot add, modify or delete VLANs locally – and is not stored in NVRAM.
    
-   Transparent – Does not participate in VTP, i.e. does not originate VTP advertisements nor does it use them to populate its VLAN database, but it will forward VTP advertisements. In VTPv1, a transparent switch will only forward VTPv1 advertisements in its own domain or if its own domain is empty. In VTPv2, a transparent switch will forward VTP advertisements regardless of domain. A transparent switch maintains its own VLAN database and stores it in NVRAM.
    
<img src = 'https://i.gyazo.com/9d14f72fa489346bd90eb0fce92deb84.png'>

To set mode:

-   (config)# vtp mode {server | client | transparent | off}
    

To set domain:

-   (config)# vtp domain vtp_domain

<img src = 'https://i.gyazo.com/f33cad8cb91b1738d59a151786723bf7.png'>


To set version:

(config)# vtp version n


Check VTP status:

-   # show vtp status
    

<img src = 'https://i.gyazo.com/3e9531cc74045d4e5196686459b395cd.png'>

If there are several VTP servers on the network, the one with the highest configuration revision will originate VTP advertisements. In theory, this allows decentralised configuration: switch A makes changes, ups the configuration revision and propagates new configuration to other switches. Switch B can then do the same and propagate its changes, with incremented configuration revision to other switches, including switch A. In practice, however, this may lead to a VTP bomb – if a switch with configuration revision higher than others (e.g. an old switch being repurposed) is attached to a network, it will overwrite VLAN configuration on all switches, And That’s Terrible.

VTPv3 solves that by making one VTP server primary. Primary VTP server announces its status to others, which precludes them from making configuration changes. In effect, non-primary VTP servers act as VTP clients for all intents and purposes, with the only difference between VTP non-primary servers and VTP clients being that VTP clients are explicitly precluded from becoming primary. Primary mode can be password protected – if another switch wants to become primary, it will have to input the password, if set.

-   # vtp primary – note this is in EXEC mode
    
-   (config)# vtp password password [hidden] – specify VTP password. Encrypt password if hidden argument is specified.
    

Additionally, VTPv3 supports extended VLANs (1006-4094), while VTPv1 and VTPv2 support only standard VLANs. Furthermore, VTPv3 propagates Multiple Spanning Tree instance information, which is a very interesting topic well explained in the following Reddit post, on which the whole subchapter is based: [https://www.reddit.com/r/ccna/comments/6ohnqo/the_forgotten_a_vtp_mst_post/](https://www.reddit.com/r/ccna/comments/6ohnqo/the_forgotten_a_vtp_mst_post/)




# IP Telephony

We call it daisy chaining on the field.

![[90f69e6608faa3b2f94d966f71f6384c.png]]


The Phone has a little LAN switch in the back that directs traffic and splits the PC and phone traffic into two.

The PC here comes in on the access port and would be part of its own VLAN

The phone would come in on the same port configured to also accept voice on a **different** VLAN.

Heres how:

![[Pasted image 20230103165125.png]]

```ad-note

CDP must be enabled on an interface for a voice access port to work with Cisco IP phones.

```

Use **show vlan brief** for a quick overview
Use **show interfaces** *type* n  to see Access mode VLAN and Voice VLAN settings
Use **show interfaces interface switchport** for verification
Use **show interfaces** F0/4 **trunk** Tp get some more info

However, using **show interfaces trunk** wont show the IP telephony switchport because it does not consider it a truck.

## VLAN Troubleshooting

- Confirm that all VLANs are both defined and active
- Check the allowed VLAN lists on both ends of each trunk to ensure that all VLANs intended to be used are included.
- Check for incorrect trunk congiuration settings that result in one switch operating as a trunk, with the neighboring switch not operating as a trunk.
- Check the native VLAN settings on both ends of the trunk to ensure the settings match.

**show vlan brief**



---
# Reference