2305131300
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]] [[STP]]

# EtherChannel 101



 Normally, Spanning Tree provides redundancy but not load balancing.
 Which sucks because we looks half of out bandwidth (a necessary evil)
 Instead of trying to load balance stp will select the port with the lowest port ID


<img src = 'https://i.gyazo.com/3a8a2d7982df942705d15c40e49c4683.png'>

- Traffic is load balanced across all the links in the EtherChannel
- And if an interface goes down its traffic will fail over to the remaining links


## NIC Teaming

This combines multiple physical network cards into a single logical inter face
Another why to bundle multiple physical network cards into a single logical interface




# As known AS


#### EtherChannel
- A port channel 
- LAG Link Aggregation
- A link bundle

#### NIC Teaming is alos known as
- Bonding
- NIC balancing 
- Link aggregation

---


# EtherChannel Load Balancing


![[Pasted image 20230513131822.png]]



![[19dced4d18da69c94dcf1ce1f240e730.png]]

>[!note] 
>It doesn't just pick a random interface every time once it picks one the next packet it sends goes over the same link


In this way each flow recieve the maximum amount of bandwidth of a single link in the port

<img src = 'https://i.gyazo.com/e03e2765d71bc5d95949e6051520e61d.png'>


# EtherChannel Protocols 


LACP Link Aggregation Control Protocol
- Open standard 
- Switch on both sides negotiate the port channel creation and maintenance
- Preffered

PAgP Port Aggregation Protocol
- Cisco Proprietary
- Switches on both sides negotiate the port channel creation and maint.

Static Etherchannel: 
-The switches do not negotiate creation and maintenance but the settings must still amtch on both sides for the port chell to come up
- Use if LACP is not supported on both sides.

All protocols are congifured with the `channel-group` command

## Etherchannel Parameters


- The switches on both sides must have a matching configuration
- the member interfaces must have the same settings on both sides
- speed and duplex
- Access or trunk mode
- Native VLAN and allowed VLANs on trunks
- Access  VLAN on access ports







---
# Reference