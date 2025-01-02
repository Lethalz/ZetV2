2412271537
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# The Hierarchical Network Model



Why do we need the hierarchical LAN Design Model?

For one it divides the network architecture into modular layers, modular meaning each layer implements a different function and can be added or removed at will.

This modularity allows the network to be scaled more easily and provides fault isolation which makes network troubleshooting much easier.


How do we achieve this Modularity?

In order to achieve this, we break the network into three separate layers:

- Access - This layer is where endpoint access the network (Network Edge)
- Distribution - Boundary between layer 2 and Layer 3, Serves as a aggregation point for the access layer and a Services boundary between core and access.
- Core - Provides connectivity between distribution blocks


![[Pasted image 20250102131123.png]]



The number of layers that are required are based on the network characteristics, for example a single building may not need a dedicated distribution layer.

Which in turn would result in a **2 Tier** architecture also known as a collapsed core.

And as the network grows it doesn't grow vertically but horizontally as more blocks are added to increase the capacity of the layer as opposed to scale up would be to upgrade the individual box vertically.


## Access Layer

This layer is known as the Network edge, this is where end user devices are attached to the network.

The access layer provides high bandwidth access to both wired and wireless end users and is the first hop for QOS and where the network gets segmented by VLANs.

Don't get this confused with SVI's (Switch Virtual Interfaces) which deal with the routing between VLANs

As you can see by the image above the access layer switches are not connected and need to go through the distribution blocks in order to communicate with one another this is by design to keep the network scalable. 



## Distribution Layer 

Aggregates access layer switches for one building, floor or campus. Because it will ultimately be the layer pushing traffic north to the core you wont need uplinks from each switch so this reduces the amount of cable runs.

It provides a boundary between layer 2 and layer 3 by keeping stp down to the access layer and stopping loops and layer 3 routing can be simplified up to the core layer by route summarization.

This layer should be deployed in 2's for redundancy, link redundancy and node reducnancy between the switches. this would be where we would see [[SSO Stateful Switchover |SSO]] supported in chassis based switches as well as at the core. 

## Core Layer

Core layer is the backbone and aggregation point for multiple networks, this provides high-speed layer 3 connectivity between distribution blocks and the wan, internet, data center, network services (authentication, load balancing) . 

Because this layer is focused on being fast, we don't want to skimp on hardware or bandwidth here and avoid any complex policies at the core so it can focus on routing to all the different networks.




## Enterprise Network Design Options

![[Pasted image 20250102154124.png]]






## Layer 2 Access


![[Pasted image 20250102155541.png]]



As you can see by the image above Layer two starts south bound of the distribution blocks and layer 3 starts above.

So the links going up to the Core aren't trunks but are layer 3 links which would need to run OSPF or EIGRP. 
But going down to the switches the links would be trunks in order to receive traffic from multiple VLANs.

This is why the distribution layer is the boundary between Layer 2 and layer 3.


## Layer 3 Access 

![[Pasted image 20250102160027.png]]

In Layer 3 access the routed edge moves down from the distribution blocks to the access blocks, so the links going up from the access switches to the distribution blocks are no longer trunks but layer 3 routed links. 

Access Layer switches would need to run routing protocols such as OSPF and EIGRP like the distribution blocks in the layer 2 access model.

Access Layer switches would be the default gateways for the end hosts which would remove the need for first hop redundancy protocols which allow load balancing to happen per flow and not per host. 

Removes the need for STP, there are no more blocked links from access layer to distribution layer and this would in turn increase the bandwidth and lead to easier troubleshooting now that STP is removed. 

There would now be a faster convergence of the network now that STP doesn't need to go through all of its states and it would be a function of OSPF and EIGRP.

A limitation of this would be no spanning VLAN's between multiple access switches.


## Simplified Campus Design 

This uses switch clustering techniques such as virtual switching System[[VSS, StackWise, and StackWise Virtual |(VSS) ]] or [[VSS, StackWise, and StackWise Virtual#StackWise |StackWise]]
where multiple switches act as one. This removes the requirement for First Hop Redundancy Protocols and reduces the need for spanning-tree protocol because the access layer uses Port-channels (No unused Links) to connect to distribution layer and STP is still used as a fallback in the case of system failure.

![[Pasted image 20250102163256.png]]


Traffic will be balanced per-flow from access layer to distribution layer based on port-channel load balancing protocols and reduces the convergence time because port channels offer sub second reconvergence on the failure of a member interface.

Distributed vlans can span between multiple access switches without blocked links (limitation of layer 3 access model) and the cluster of stacked switches can be managed as a single switch. 





---
# Reference