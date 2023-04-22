2304211827
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# IGP and EGP

Interior gateway protocol is for routing within an organization 

Exterior gateway protocol is for routingbetween organizations over the internet

Avoid Using Differing Types in One Network

### Distance Vector Protocols 

The router only advertises its own direct neighbors and their direct routes, they have no knowledge of the full network topology.

*Often called Routing by rumor*


### Link State ROuting Protocols

Each router describes itself and its interfaces to its directly connected neighbours.

Every Router learns the full picture of the network including every router its interfaces and what they connect to.

``` ad-note Careful
Just like Distance vector Protocols, the router only talks to it's direct neighbor. However, Distance vector sees the routing information in the POV of it's neighbor while Link state the routing information is unchange and you see the POV of the router that originally sent that information
```

Puts more load on the router


| Protocol | Type            | IGP or EGP |
| -------- | --------------- | ---------- |
| RIP      | Distance Vector | IGP        |
| EIRGP    | Distance Vector | IGP        |
| OSPF     | Link-State      | IGP        |
| IS-IS    | Link-State      | IGP        |
| BGP      | Path Vector     | EGP           |


*EIRGP* - Enhanced Interiror Gateway routing protocol
*IS-IS* - Intermediate System - Intermediate System



---
# Reference