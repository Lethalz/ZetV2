2301041625
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Spanning Tree Protocol Concepts


## Chapter 9 – Spanning Tree Protocol Concepts
    

```ad-note
“switch” and “bridge” used interchangeably
```

### Classic STP

**STP** (and its descendants), standardised as 802.1D, now included in 802.1Q. Allows switches to exchange information on network physical topology and agree which links to disable to ensure there are no loops. If topology changes (e.g. a cable is disconnected), the switches converge on a new set of links to use.

Port can be in two **permanent states:**

-   **Forwarding** 
-   **Blocking** (Discarding in RSTP) – do not send or receive any frames (apart from BPDUs?) on this interface.

There are also two **transient states**:

- **Listening** (not in RSTP) – **Do not forward frames**, listen to incoming frames to remove stale        MAC entries that might cause loops
- **Learning** – **Do not forward frames**, listen to incoming frames to learn MAC addresses**

```ad-note
Ports that are administratively disabled or that are failed are said to be in a disabled state.
``` 

STP/RSTP uses three criteria to choose whether to put an interface in forwarding state:
■ STP/RSTP elects a root switch. STP puts all working interfaces on the root switch in forwarding state.
■ Each nonroot switch considers one of its ports to have the least administrative cost
between itself and the root switch. The cost is called that switch’s root cost. STP/RSTP places its port that is part of the least root cost path, called that switch’s root port (RP),
in forwarding state.
■ Many switches can attach to the same Ethernet segment, but due to the fact that links
connect two devices, a link would have at most two switches. With two switches on a
link, the switch with the lowest root cost, as compared with the other switches attached
to the same link, is placed in forwarding state. That switch is the designated switch, and
that switch’s interface, attached to that segment, is called the designated port (DP).

![[b9a18f81f45ce19617d57d7e98879a80.png]]


![[29ced4717855ffde4c077e123a8110ab.png]]

Take bridge 11 for example, It gets a hello from **bridge 21 DP** and **Bridge 5 DP**.. It's says "Hmm, bridge 21 is closer to the root switch so i can block my other link port."

--- 

## Electing the root switch

Each switch has an **8-byte Bridge ID (BID)**, consisting of a 2-byte priority field and 6-byte System ID **(Unique)**, based on the switch's MAC address.

BPDU (**bridge protocol data units**) or configuration BDPUs 
-most common: **Hello** BPDU
-Include Root Bridge ID, Sender Bridge ID, Senders root cost, Timer values on the root switch
Each bridge/switch sends a **Hello** BPDU (bridge protocol data unit) with
	-   Root bridge ID – ID of a bridge the sender believes to be root
    
	-   Sender bridge ID – ID of the sender
    
	-   Sender root cost – the cost of path from sender to root
    
	-   Timer values – set by root bridge, adopted and forwarded by other bridges
    

	-   Hello – intervals between hello message, defaults to 2 seconds
    
	-   MaxAge – How long a switch should wait when not receiving Hellos BPDUs before trying to change topology, defaults to 10 times Hello (20 seconds)
    
	-   Forwarding delay – When changing topology, how long a switch should stay in each transient state: listening and learning, in that sequence. Defaults to 15 seconds for each state.


**Root bridge selection:** *lowest* priority wins.  Lowest number in BID.
If there is a draw, the lowest MAC address wins.

At the beginning, all switches send BPDUs with their **BIDs as root**. When they see a better BID, they start announcing it as the new root BID. Over time, every bridge will **converge** on the best root BID.

**Convergence** – *the process by which switches react to changes in topology and agree on how to change how frames are forwarded.* Happens when a switch stops receiving Hello BPDUs on its root port for a period determined by MaxAge timer or when the link on the root port fails

When convergence happens, switches **decide new port roles**, which then determine port state.

## Choosing the Root Port

***Root cost** is the sum of all port costs on the way from the root bridge to the port in question*. Port costs are determined by the **actual link speed** by default, but this can be tweaked.

***All ports*** on the **root** bridge are set to a *forwarding state*. 
On non-root bridges, **ports with lowest root cost** (closest to root switch, in a way) are set to a **forwarding state**.

```ad-note   
title: Tiebreaker
- Choose based on the lowest neighbor BID
- Choose based on the lowest neighbor port priority
- Choose based on the lowest neighbor internal port number
```



## Designated Ports

There are also designated ports: on a given Ethernet segment (collision domain) the one with **lowest root cost** (lowest BID as a tiebreaker) is set to a forwarding state. 
Others are blocked. In practice, since hubs are no longer used, **every port facing “away” from the root switch is a designated port.**

In short, frames will successfully go via a link that has a designated port on the side closer to the root switch and a root port on the other. If hubs are not used – and they are not used any more – the port closer to the root switch is always the designated port, it is the other side that determines whether a link is active or not.

## Changing infterface states

When a forwarding port goes to another state, either RP or DP it can imeediately move.
However, to go from a blocked state to a forwarding state it happens diffrently to stop any looping problems.
STP moves an interface from blocking to listening, then to learning, and then to forwarding state. 

![[02dfa1b373f2d0cfb4c237143e225f49.png]]





****




### RSTP
    

**Rapid Spanning Tree Protocol** – introduced in 1998, standardised in 2001 as 802.1w amendment to 802.1D, revised in 2004, now included in 802.1Q.

Similarities with classic STP:
	-   Election of root switch
	-   Selection of root port  
	-   Election of designated port
	-   Forwarding and blocking (discarding in RSTP) states
    

Differences:
	-   **Alternate port** can quickly replace a root port without waiting for the port to enter a forwarding state
	-   **Backup port** can quickly replace a designated port without waiting for the port to enter a forwarding state
	-   Shortened timers – MaxAge set as 3 times Hello (6 seconds)
	-   Mechanism to ask a neighbouring switch about a possible link failure instead of waiting for MaxAge to expire
	-   Hello BPDUs are generated by each switch – this means each switch needs to have the same timer settings
	-   STP **blocking and disabled states** are *lumped together* into a *discarding state*
	-   Even when a state transition requires waiting, RSTP does not use a listening state and jumps right into the learning state.
    

An **alternate port** is the one with the **second-lowest** root cost, right after the root port. When a switch stops receiving Hello BPDUs on its root port, it quickly (either after MaxAge, i.e. 6 seconds, or after determining the link has failed):

1.  informs the switch on the other side of its alternate port that a topology change has occurred and ask it to flush relevant entries in MAC table to avoid loops
    
2.  flushes relevant entries in its own MAC table to avoid loop
    
3.  designates its alternate port the new root port and moves it into forwarding state
    
4.  moves the old root port into a discarding state
    
5.  selects a new alternate port
    

This process bypasses the listening and learning states.

![[19657d7b0534cd6e0ca54037d6e0365e.png]]

RSTP port/link types:

-   **point-to-point** – full-duplex link between two switches. Default if PortFast is disabled. Convergence on these links requires entering the learning state.
    
-   **point-to-point** edge – full-duplex link between a switch and a single edge device (e.g. a PC). Since the switch doesn’t know what is on the other side, this link type is set when PortFast is set on a port. Ports on these links bypass the learning state when converging.
    
-   **shared** – half-duplex links are assumed to be connected to a hub, necessitating slower convergence (both a hub and an endpoint is connected) Not likely anymore.
    



## Other STP Features

**EtherChannel** – prevents STP convergence from being needed when only a single port or cable faulure occurs. Bundles up to 8 L2 or L3 links together into a single link. Provides load-balancing and quick failover. More on that to follow.

**BPDU Guard** – If enabled on a port, disable the port if it receives a BPDU. This prevents rogue switch attacks (i.e. attacker becoming a root switch to listen to traffic) and incidents (a non-STP/RSTP aware switch plugged into the network causing loops). **Should be enabled on all access ports**:

-   (config)# **spanning-tree bpduguard default** – enable BPDU Guard on all access links by default
    
-   (config)# **no spanning-tree bpduguard default** – disable BDPU Guard on all access links by default
    
-   (config-if)# **spanning-tree bpduguard enable** – enable BPDU Guard on the specified interface
    
-   (config-if)# **spanning-tree bpduguard disable** – disable BDPU Guard on the specified interface
    

BDPU Guard disables the interface if it receives a BPDU. To manually restore it:

-   (config-if)# **shutdown**
    
-   (config-if)# **no shutdown**
    

To enable automatic recovery:

-   (config)# **errdisable recovery cause bpduguard**
    
-   (config)# **errdisable recovery interval seconds** – Set interval before automatic recovery. NOTE: This applies to automatic recovery from all types of errors.
    

**PortFast** allows the interface to *transition directly from blocking to forwarding state* **without** going through listening and learning states.
It should be enabled **only on ports** connected to **end devices**, not other switches. Additionally, PortFast-enabled ports *should also be configured* with **BPDU Guard**.

-   (config)# **spanning-tree portfast default** – enable PortFast on all access links by default
    
-   (config)# **no spanning-tree portfast default** – disable PortFast on all access links by default

-   (config-if)# **spanning-tree portfast** – enable PortFast on a specific interface (must be access port)
    
-   (config-if)# **spanning-tree portfast network** – force-enable PortFast on a specific interface
    
-   (config-if)# **spanning-tree portfast disable** – disable PortFast on a specific interface
    

**RootGuard** is used to *prevent a device* connected to a given port f*rom becoming the root switch*. This is most often **used when adding new switches to the network**. **LoopGuard** is used to prevent loops that might arise from connectivity failures. **Incompatible with RootGuard**, will be automatically disabled if RootGuard is enabled on a port.

-   (config-if)# **spanning-tree guard root** – Enable RootGuard on a port
    
-   (config-if)# **spanning-tree guard loop** – Enable LoopGuard on a port
    
-   (config-if)# **spanning-tree guard none** – Disable RootGuard and LoopGuard on a port
    
-   (config)# **spanning-tree loopguard default** – Enable LoopGuard on all interfaces by default.
    


****

---
# Reference