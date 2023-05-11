## Open Standards(in order of release)
802.1D Spanning tree protocol (STP) 50 sec convergence
802.1w Rapid spanning tree- improved converges but no load balancing Uses one spanning tree for all vlans in the lan
802.1s Multple Spanning Tree Protocol (MSTP) - enables grouping and mapping VLANS into dfferent spanning tree instances for load balancing


![[2a04033fd1b1e39bad440bc1da52b665.png]]


## Cisco Proprietary Versions

<img src = 'https://i.gyazo.com/9ed4ecb490139c504d88985200616a91.png'>

## Cisco Load Balancing 

<img src = 'https://i.gyazo.com/256cfa582a466fc6d832095c763f5cd0.png'>


## PVST+ Port Roles

Same as STP but Blocking ports are called 'Alternate' Ports




### VERIFICATION

	`show spanning tree vlan 1`

if you dont specify vlan it will show for all vlans on switch

`enabled protocol ieee` means its pvst+


`show mac address-table`

use this to match Mac addresses to the correct outgoing interfaces
Can use it to map your STP


