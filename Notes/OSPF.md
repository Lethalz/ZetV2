2304301201
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# OSPF

# OSPF Routing Protocol Overview

**OSPF (Open Shortest Path First)** is an Interior Gateway Protocol (IGP). It is a link-state routing protocol that uses the Shortest Path First (SPF) algorithm to calculate the best route. OSPF routing protocol is an open standard, so various network vendors implement it.

Here are the most important features of OSPF:

-   A classless routing protocol
-   Supports VLSM, CIDR, manual route summarization, equal cost load balancing
-   Incremental updates are supported
-   Uses only one parameter as the metric – the interface cost.
-   The administrative distance of OSPF routes is, by default, 110.
-   Uses multicast addresses 224.0.0.5 and 224.0.0.6 for routing updates.

Routers running OSPF protocol have to establish neighbor relationships before exchanging routes. Because OSPF is a link-state routing protocol, neighbors don’t exchange routing tables. Instead, they exchange information about network topology. Each OSPF router then runs SPF or Dijkstra algorithm to calculate the best routes and adds those to the routing table. Because each router knows the entire topology of a network, the chance for a routing loop to occur is minimal.

Each OSPF router stores routing and topology information in three tables:

-   **Neighbor table** – stores information about OSPF neighbors
-   **Topology table** – stores the topology structure of a network
-   **Routing table** –  stores the best routes

## OSPF Neighbors

OSPF routers need to establish a neighbor relationship before exchanging routing updates. OSPF neighbors are dynamically discovered by sending Hello packets from each OSPF-enabled interface on a router. Hello packets are sent to the multicast IP address of 224.0.0.5.

The process is explained in the following figure:

[![ospf routing protocol](https://study-ccna.com/wp-content/images/ospf_hellos.jpg "ospf hellos")](https://study-ccna.com/wp-content/images/ospf_hellos.jpg)

Routers R1 and R2 are directly connected. After OSPF is enabled, both routers send Hellos to establish a neighbor relationship. You can verify that the neighbor relationship has been established by typing the **‘show ip ospf neighbors’** command.

R1#show ip ospf neighbor 
Neighbor ID Pri State Dead Time Address Interface
2.2.2.2 1 FULL/DR 00:00:30 192.168.0.2 FastEthernet0/0

In the example above, you can see that the router-id of R2 is  2.2.2.2. Each OSPF router is assigned a router ID. A router ID is determined by using one of the following:

1.    Using the router-id command under the OSPF process.  
2.    Using the highest IP address of the router’s loopback interfaces.  
3.    Using the highest IP address of the router’s physical interfaces.

The following fields in the Hello packets must be the same on both routers in order for routers to become neighbors:

-   subnet
-   area id
-   hello and dead interval timers
-   authentication
-   area stub flag
-   MTU

By default, OSPF sends hello packets every 10 seconds on an Ethernet network (Hello interval). A dead timer is four times the value of the hello interval, so if a router on an Ethernet network doesn’t receive at least one Hello packet from an OSPF neighbor for 40 seconds, the router declares that neighbor to be down.

## OSPF Neighbor States

Before establishing a neighbor relationship, OSPF routers need to go through several state changes. These states are explained below:

**1. Init state** – a router has received a Hello message from the other OSPF router  
**2. 2-way state** – the neighbor has received the Hello message and replied with a Hello message of his own  
**3. Exstart state** – beginning of the Link State Database (LSDB) exchange between both routers. Routers are starting to exchange link state information.  
**4. Exchange state** – DBD (Database Descriptor) packets are exchanged. DBDs contain LSAs headers. Routers will use this information to see what LSAs need to be exchanged.  
**5. Loading state** – one neighbor sends LSRs (Link State Requests) for every network it doesn’t know about. The other neighbor replies with the LSUs (Link State Updates), which contain information about requested networks. After all the requested information have been received, other neighbor goes through the same process  
**6. Full state** – both routers have the synchronized database and are fully adjacent to each other.!
> [!NOTE]
> Depending on the network, OSPF can elect a **Designated Router (DR)** and a **Backup Designated Router (BDR)**. DR and BDR serve as the central point for exchanging OSPF routing information.
## Exchange

![[1d41a79437359608101b5dc1ffaf41a3.png]]

## Loading

![[829960768a9ca1859e7130adf6d4ffe9.png]]

There is anothe state calld 'full' where each router sends a LSAck

## OSPF Routing Protocol Areas

OSPF uses the concept of areas. An area is a logical grouping of contiguous networks and routers. All routers in the same area have the same topology table, but they don’t know about routers in the other areas. The main benefits of creating areas are that the size of the topology and the routing table on a router is reduced, less time is required to run the SPF algorithm, and routing updates are also reduced.

Each area in the OSPF network has to connect to the backbone area (area 0). All routers inside an area must have the same area ID to become OSPF neighbors. A router with interfaces in more than one area (area 0 and area 1, for example) is called **Area Border Router (ABR)**. A router that connects an OSPF network to other routing domains (EIGRP network, for example) is called **Autonomous System Boundary Router (ASBR)**.

>[!NOTE]
>In OSPF, manual route summarization is possible only on ABRs and ASBRs.

In OSPF, manual route summarization is possible only on ABRs and ASBRs.

To better understand the concept of OSPF areas, consider the following example.

[![ospf areas](https://study-ccna.com/wp-content/images/ospf_areas.jpg "ospf areas")](https://study-ccna.com/wp-content/images/ospf_areas.jpg)

All routers are running OSPF. Routers R1 and R2 are inside the backbone area (area 0). Router R3 is an ABR because it has interfaces in two areas, namely Area 0 and Area 1. Routers R4 and R5 are inside Area 1. Router R6 is an ASBR because it connects the OSPF network to another routing domain (an EIGRP domain in this case). If the R1’s directly connected subnet fails, router R1 sends the routing update only to R2 and R3 because all routing updates are localized inside the area.

> [!note] 
> The role of an ABR is to advertise address summaries to neighboring areas. The role of an ASBR is to connect an OSPF routing domain to another external network (e.g. Internet, EIGRP network…).

## Reference Bandwidth

Bandwidth default is 100Mbps this is the command to change that

`R1(config)# router ospf 1
`R1(config-router)#auto-cost reference-bandwidth 10000`

If its 1000 Gbps would be 1 (1000/1000) that would mean you aren't expecting faster speeds don't make the same mistake the old-time engineers that created ospf did. Set that hoe to 10000 (10000/1000) cost 100

![[bac827d6c4ce8a45156cbad5515eaa49.png]]


## OSPF Metric (Cost) Change on Interface

- A manually congifured OSPF cost overrides the value automatically derived from the bandwidth
`R1(config)#interface FastEthernet 0/0`
`R1(config-if)#ip ospf cost 50`


## Show OSPF Interface information

![[3d0d8217a4dd58d23839566b73595e55 1.png]]


## OSPF Packet Types

*Hello* - A router will send out and listen for hello packets when OSPF is enabled on an interface, and form adjacencies with other OSPF routers on the link unless it is a passive interface
-Multicast (224.0.0.5)
-Sent every 10 seconds by default
-Out every interface that OSPF is enable (except passive-interfaces)
![[2a304b1c75f0462817d49633313df40b.png]]
(cont)
![[8b940fd1e250a8170367acd256a67e31.png]]
These settings much match for a pair of OSPF routers to form an adjacency with each other
1. Must be in each other's Neighbor list
2. Hello and Dead intervals
3. Area ID
4. Ip Subnet
5. Authentication Flag
6. Stub Area Flag

DBD DataBase Description:* Adjacent routers will tell each other the networks they know about with the DBD  packet

*LSR Link State Request:* If a router is missing information about any of the networks in the received DBD, it will send the neighbour an LSR
*LSA Link State Advertisement:* A routing update
*LSU Link State Update* Contains a list of LSA's which should be udpated used during flooding
*LSAck* : recieveing routers acknowledge LSAs



### LSA, LSU, and LSR

OSPF routers use the LSAs (Link-State Advertisements) to exchange topology information. Each LSA contains routing and topology information to describe a part of an OSPF network. When two neighbors decide to exchange routes, they send each other a list of all LSAs in their respective topology databases. Each router then checks its topology database and sends a Link State Request (LSR) message requesting all LSAs not found in its topology table. The other router responds with the Link State Update (LSU) containing all LSAs the other neighbor requested.

The concept is explained in the following example:

[![ospf lsa lsr lsu](https://study-ccna.com/wp-content/images/ospf_lsa_lsr_lsu.jpg "ospf lsa lsr lsu")](https://study-ccna.com/wp-content/images/ospf_lsa_lsr_lsu.jpg)

 After configuring OSPF on both routers, routers exchange LSAs to describe their topology database. Router R1 sends an LSA header for its directly connected network 10.0.1.0/24. Router R2 checks its topology database and determines that it doesn’t have information about that network. Router R2 then sends a Link State Request message requesting further information about that network. Router R1 responds with Link State Update, which contains information about subnet 10.0.1.0/24, such as next hop address, cost, etc. 



## MTU mismatch issue


If there is an MTU  setting mismatch then OSPF routers can become neighbors but they will not exchange routes with each other 
MTU is congifures at the interface level![[74d9f623de6f1e7b06760d133bef1d1b.png]]

There are two types of MTU 
1 IP
2 Interface

## DR and BDR

- HIGHEST router ID picks the Designated Router that hold most the information everyone else summarizes 
- SECOND highes is the back up DR
- Routers elect the DR and BDR at the 2-Way stage
- no election on point to point links

The DR and BDR establish FULL neighbor state with all routers on the network segment
the other routers stay in a 2-way state not directly sending DBD to each other

If any of the routers has a link state change it send a multicast message just to the DR's 
and then the DR multicasts the updates to everyone else.


### Setting OSPF Priority



![[367ee39b98be009e2e4b6e23dab92f8f 1.png]]

The router with the highest priority becomes the DR and the router with the second highest priority becomes the BDR.

## Summary Routes


Summarize routes going across different areas to take up less space in router memory

```
R2(config)#router ospf 1
R2(config-router)#area 0 range 10.1.0.0 255.255.0.0
R2(config-router)#area 1 range 10.0.0.0 255.255.0.0
```

>[!Notice] 
>Summary routes do not use wildcards because they specify the acutal network 
>


---




# Reference