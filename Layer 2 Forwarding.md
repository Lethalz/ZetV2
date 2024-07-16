2407121006
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# Layer 2 Forwarding

# Layer 2 Forwarding Fundamentals

## My Understanding of Layer 2 Forwarding

The switch understands the flow of data at level 2, The main function of a switch is Learn Flood forward. A switch learns by receive a frame on an interface, it looks at the source MAC address and updates the MAC table. It then uses that MAC table to forward frames to the destination. Unlike Routing the MAC table works on an exact match.  When a destination MAC isn't known the frame is flooded out all ports except the one it was received on. 

---

## Fundamentals of Layer 2 Forwarding

### 1. MAC Address Table
- Also known as CAM (Content Addressable Memory) table
- Stores MAC addresses and associated ports
- Used for making forwarding decisions

### 2. Learning Process
- Switch learns MAC addresses from incoming frames
- Associates source MAC with the port it arrived on

### 3. Forwarding Decision
- Destination MAC lookup in the MAC address table
- If found, forward to specific port
- If not found, flood to all ports except the source

### 4. Flooding
- Occurs when destination MAC is unknown
- Helps in discovering new devices on the network

### 5. Aging
- MAC entries have a timeout period
- Removes stale entries to accommodate network changes

### 6. Types of MAC Addresses
- Unicast: Single destination
- Multicast: Group of destinations
- Broadcast: All devices on the network

### 7. VLAN Awareness
- Switches can maintain separate MAC tables per VLAN
- Ensures traffic separation between VLANs

---

## Feynman Method Explanation

Imagine you're a postal worker in a small town. Your job is to deliver letters to houses:

1. You have a big book (MAC address table) that lists every house and its address.

2. When you get a letter, you look at who it's from and write down which street they live on (learning process).

3. To deliver the letter, you look up the recipient's address in your book (forwarding decision).

4. If you can't find the address, you ask every house in town if they know the person (flooding).

5. You update your book regularly, removing old addresses (aging).

6. Sometimes you deliver to one house, sometimes to a group, and sometimes to everyone (unicast, multicast, broadcast).

7. The town has different neighborhoods (VLANs), and you keep separate address books for each.

This is essentially how a switch works at Layer 2. It learns addresses, looks them up to make decisions, and delivers frames to the right destinations, just like you deliver letters in the town.

---
# Reference