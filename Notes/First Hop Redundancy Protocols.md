2305100953
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# First Hop Redundancy Protocols

<img src = 'https://i.gyazo.com/5257881d230062f87a6cfb1b36d4f581.png'>

FHRP 

R1 and R2 both run the FHRP and they agree on what their virtual IP and mac address will be to allow for automated gateway failover

The hosts use the 1 VIP as thier default gateway address

If one of the gateway gails another gateway will take its place



FIrst Hop Redundancy protocols

HSRP : Cisco Proprietary, depolyed in active/standby pair
Virtual Router redundancy protocol (VRRP): open standard deployed in active/standby pair very simliar to HSRP
Gatway load balancing protocol (GLBP): Cisco proprietary supports active/active load balancing across multiple routers



Hot standby router Protocol

<img src = 'https://i.gyazo.com/cc6fad205167c8d1c4adb251dd0e7481.png'>

Uses a virtual IP and mac address to allow for automated gateway failover.
In this diagram both R1 and R2 used HSRP to agree upon an IP address and mac address so now their virtual ip is '10.10.10.1'

However one will become active and one will become standby
they send 'keep alive' packets to each other if one goes down the other kicks into gear
This failover happens automattically


<img src = 'https://i.gyazo.com/32d264e15ea291c73c30eaedfebe98ff.png'>

If the standby router stops recieving Hello


## HSRP Configuration

`R1(config)#interface g0/1`
`R1(config-if)#ip address 10.10.10.2 255.255.255.0`
`R1(config-if)#no shutdown`
`R1(config-if)#standby 1 ip 10.10.10.1`

`R2(config)#interface g0/1`
`R2(config-if)#ip address 10.10.10.3 255.255.255.0`
`R2(config-if)#no shutdown`
`R2(config-if)#standby 1 ip 10.10.10.1`




Everything looks like standard interface configuration but we are using `standby` command for HSRP

### Verification

`show standby`


















---
# Reference