2305081256
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Inter-VLAN routing



# Router with Seperate Interfaces

![[4c4714fdcb6a82192fc33d25433a0b6b.png]]

<img src = 'https://i.gyazo.com/0f7778b3f85fe831813a80886d7e478d.png'>



## Disadvantages

1. You need a separate physical interface for every  VLAN - you are liable to run out of interfaces
2. Traffic being routed within the campus has to go up and down physical ethernet  cables to the router

# Router on a Stick



![[5495a5f1603b39c7239d0239ed720c24.png]]

Uses Subinterfaces
The One interface is configured as a Trunk port
When Vlan Traffic goes over the Trunk it is encap with 801.Q header
That is how the router knows what subinterface it is going to.


<img src = 'https://i.gyazo.com/db448e7c18b3b2690bb2ab6b44e8004a.png'>



## Considerations

Less likely to run out of physical interfaces for every vlan
Traffic being routed within th ecampus has to go up and down the same physical ethernet cable to the router - there is more contention for bandwidth than when using separate interfaces.


## Layer 3 switch

![[4f84f6e3f12e33ec17ae4da3cdc51916.png]]

![[d246326a29be627b772dd6b23d44b4e2.png]]

![[746c40c5bcb99cc565e47cc58ca2e477.png]]
---

This second slide is configuring the interface linking the Switch and the router. 
It needs to not be a switchport in order to 'route' not switch traffic to the router.
The config needs to be mirrored on the router as well as the route to the internet
The router needs a route to the 10.10.100.0/24 network because its seeing the switch as a router



## Considerations 

1. Traffic being routed within the campus is routed across the switch backpalne, it does not need to travel over physical cables to an external router
2. You may still need an external router for WAN connnectivity and services
# Reference