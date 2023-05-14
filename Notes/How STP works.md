2305111310
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]] [[STP]]

# How STP works


All switches come with **STP enabled.**
When a switch is **powered on** and plugged in it sends out **BDPU** packets
**Bridge Data Protocol Unit**
- This contains the switch's **Bridge ID** (Unique Identifier on LAN)
- Comprised of the switch's unique MAC and a admin defined Bridge Priority Value
- Can be from 0-65535 (32768 is default)

Using this information the switches(Bridges) in the LAN choose a **Root** bridge based on the **lowest** switch Priority value (3234 would be root over 52343)

In the case of a tie the switch with the lowest MAC address will be selected.
The switches then build a loop free fowarding path tree that leads back to the **root** bridge

The other (non-root) Bridges(switches) will detect their **lowest cost path** to the **root** bridge and set those interfaces to a forwarding state.

this 'Cost' is preffered via **bandwidth**

Each switches exit interface on the lowest cost path to the root bridge is selected as the **root port**


>[!note] 
>STP does not do load balancing if there is a tie it will select the neighbor switch with the lowest Bridge ID or MAC Address. If there are multiple links to the same bridge (switch) it uses the port with the lowest Port ID.

![[2c816c7314929dc93ee015d7f99b1937.png]]



## Desginated ports

Ports on the neighbor switch opposite the root port are **Designated ports**

**Root** Ports point **towards** the root bridge
**Designated** ports point **away** from the root bridge
**All** Ports on the Root Bridge are **Designated** because they are all pointing away from the Root


**Root** ports and **Designated** ports always transition to a **forwarding** state




![[f73c78c4034e368d4f6f7e6569e6ff81.png]]

- For point two the lowest bridge ID (Mac if equal) is used for the designated port origine
Purple = Designated
Yellow = Root
Red = Blocked

![[3f2aa7b0c5f685a4b7131830ea937310.png]]

- Spanning tree only blocks ports on one side of the blocked link 
- BPDUs continue to be sent over the link but the other traffic is dropped

The easy way to fiure out which ports are root, designated and blocking
1. determine the root bridge first
2. all ports on the root bride are designated ports
3. determine the root ports on the other switches (lowest cost to root bridge)
4. the ports on the other side of those lines are designated
5. on the links which are left one port will be blocking
6. Determine the blocking port (highest cost path to root bridge or highest bridge ID)
7. The ports on the other side of those links are 'Designated Ports'













---
# Reference