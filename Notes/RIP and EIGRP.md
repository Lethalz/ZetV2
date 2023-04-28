2304281223
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# RIP and EIGRP

# RIP
RIPv1 is legacy
RIPv2 supports authentication
Can  Equal Cost up to 4 routes

Configuration
```
	R1(config)#router rip
	R1(config-router)#version 2
	R1(config-router)#network 10.0.0.0

```
> [!info]
The 'network' command should reference a classful network. No subnet mask is specified.


Rip auto-summarizes routes to the classful boundary by default

For example 123.168.10.1/30 will be advertised as a 192.168.10.0/24

Modern networks are  NOT built like this anymore 


## Manual Summarization
``` R2(config-router)#interface f1/0
	R2(config-if)#ip summary-address rip 10.0.0.0 255.255.0.0
```
Neighbors will only learn the summary route
Configured on the **interface** level
Only used in really small networks or lab networks
Send traffic for 10.0.0.0/16 here 



### show run | section rip

```
R1#sh run | section rip
router rip
	version 2
	network 10.0.0.0
	no auto-summary

```

Check routes that are not showing in the routing table


### default route injection

final outbound router gets configured instead of every single router

```
R4(config)#ip route 0.0.0.0 0.0.0.0 203.0.113.2
R4(config)#router rip
R3(config-router)#default-information originate
```

# EIGRP


Enhanced interiror gateway routing protocol
- supports large network
- very fast convergence times
- bounded updats where network topology change updates are only sent to routes affected by teh change
- multicast instead of broadcast

- will automatically perform equal cost load balancing on up to 4 paths by default
- can be congiufred to perform unequal cost load balancing
- up to 16 paths


## configuration

```
R1(config)#router eigrp 100
```

'100' is the Autonomous System (AS) meaning an independent administrative domain. 

- EIGRP routers need to have the same *AS* number to peer with each other (configuration-wise)

`R1(config-router)#network 10.0.0.0 0.0.255.255`

`network` command uses wildcard masks (inverse of a subnet mask)
>[!info] subtract each octet in the subnet mask from 255 to calculate the wildcard mask

A subnet mask of 255.255.0.0 equals a wildcard of **0.0.255.255**
A subnet mask of 255.255.255.252 equals (255-252) = 3 so **0.0.0.3**

- However if you dont enter a wildcard te command defaults to using the classful boundary absed on the ip

The network command means: 

Hey look for interfaces with a IP address with falls within this range 0 = match 255 = any
then enable EIGRP on those interfaces - send out and listen for EIRGP hello messages and peer with adjacent EIGRP routers
ALSO, ADVERTISE the network and mask WHICH is configured on the router through those interfaces.

`R1(config-router)#network 10.0.0.0 0.0.255.255
the network statement is NOT advertise it is ONLY used as a range to find valid Networks.

10.0.0.0/16 is *NOT* advertised just used to find valid networks
## EIGRP Router ID

How the EIGRP routers identify themselves (in the form of an IP address)
Will default to being the highest IP address of any loopback interfaces configured on the router or the highes othe IP address if a loopback does not exist

Loopback interfaces never fo down so the Router ID wont change

Can configure manually
- Use a loopback or configure manually
```
R1(config)#router eigrp 100
R1(config-router)#eigrp router-id x.x.x.x
```


show ip eigrp neighbors















# Reference