

2309281030
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Solicited node multicast address

# IPv6 Solicited Node Multicast Addresses

## Overview

IPv6 Solicited Node Multicast Addresses are specialized multicast addresses used in Neighbor Discovery Protocol (NDP). They are designed to make ARP-like neighbor resolution more efficient by limiting the scope of who receives the request.

### Format

The Solicited Node Multicast Address is generally in this format:

**FF02::1:FF00:0/104**

The **FF02::1:FF00:0/104** part is fixed, and the last 24 bits (last 6 hexadecimal digits) are variable and are taken from the Interface ID of the corresponding unicast address.

## How to Create

### Step 1: Take the Last 6 Hex Digits of Unicast Address

Let's say you have a unicast address like this: **2001:db8::1:2a1:fc23**

The last 6 hex digits would be **a1:fc23**.

### Step 2: Append to Fixed Part

Append the last 6 hex digits to **FF02::1:FF**, which results in the Solicited Node Multicast Address.

**FF02::1:FFa1:fc23**

### Step 3: Verification

Verify if this address matches the intended network devices.

## Summary

To form a Solicited Node Multicast Address:

1. **Isolate the last 6 hexadecimal digits** from the IPv6 unicast address.
2. **Append** these 6 hex digits to the fixed part **FF02::1:FF**.
3. **Verify** the newly formed address.

**Note**: The 'FF02::1:FF00:0/104' part is not changed; only the last 24 bits are variable, based on the unicast address

# Neighbor Discovery Protocol (NDP) in CCNA Context

## Overview

Neighbor Discovery Protocol (NDP) is a fundamental protocol within the IPv6 suite, responsible for various essential functions that make IPv6 networking work smoothly. In the context of CCNA studies, understanding NDP is vital for mastering IPv6 operations, including address resolution, duplicate address detection, and router discovery.

### Functions of NDP

1. **Router Discovery**: Determines available routers on the network.
2. **Prefix Discovery**: Finds out which address prefixes can be used for autoconfiguration.
3. **Parameter Discovery**: Learns the link's MTU (Maximum Transmission Unit) and hop limits.
4. **Address Resolution**: Resolves network layer addresses to link-layer addresses.
5. **Neighbor Unreachability Detection**: Detects whether a neighbor is reachable.

## Relationship with IPv6 Solicited Node Multicast Addresses

NDP often utilizes IPv6 Solicited Node Multicast Addresses for its operation, specifically for the function of Address Resolution. When a node wants to resolve a target IPv6 address to a MAC address, it sends a Neighbor Solicitation (NS) message. This message is sent to the Solicited Node Multicast Address corresponding to the target IPv6 address.

**Example**:

1. Node A wants to find the MAC address of Node B with the IPv6 address **2001:db8::1:2a1:fc23**.
2. Node A sends a Neighbor Solicitation message to the Solicited Node Multicast Address **FF02::1:FFa1:fc23**.
3. Node B listens to this multicast address and responds with its MAC address in a Neighbor Advertisement (NA) message.

## How NDP Works

### Step 1: Router Solicitation (RS)

When an IPv6-enabled device boots up, it sends an RS to inquire about available routers.

### Step 2: Router Advertisement (RA)

Routers respond to RS with an RA, which contains necessary parameters like prefix information.

### Step 3: Neighbor Solicitation (NS)

If a device needs to discover the link-layer address of another device, it sends an NS to the device's Solicited Node Multicast Address.

### Step 4: Neighbor Advertisement (NA)

The target node responds with an NA message containing its link-layer address.

### Step 5: Data Exchange

Once the link-layer address is known, data packets can be exchanged directly.

## Summary

NDP performs multiple functions that maintain IPv6 network health and facilitate communication. It often uses Solicited Node Multicast Addresses for efficient address resolution. Understanding both NDP and Solicited Node Multicast Addresses is crucial for mastering IPv6 topics in CCNA studies.

## Router Solicitation (RS)

### When Used:

1. **Device Boot-up**: When an IPv6-enabled device starts up, it sends out RS messages to discover available routers.
2. **Manual Trigger**: An administrator can manually request a router advertisement by sending an RS.
3. **Network Reconfiguration**: Upon network changes, devices may send RS messages to ensure they have the latest router information.

## Router Advertisement (RA)

### When Used:

1. **In Response to RS**: When a router receives an RS, it replies with an RA to provide network configuration information.
2. **Periodic Broadcast**: Routers send RA messages at regular intervals to keep devices updated about network configurations.
3. **Network Change**: When a router’s configuration changes, it will often broadcast an RA to update connected devices.

## Neighbor Solicitation (NS)

### When Used:

1. **Address Resolution**: To find the MAC address corresponding to a known IPv6 address, a device will send an NS message.
2. **Duplicate Address Detection (DAD)**: NS is used to verify the uniqueness of a tentative address before it's fully assigned to an interface.
3. **Neighbor Unreachability Detection**: NS messages can be used to check if a previously reachable neighbor is still reachable.

## Neighbor Advertisement (NA)

### When Used:

1. **Responding to NS**: After receiving an NS for address resolution, the target device sends an NA message back with its MAC address.
2. **Confirming Address**: If a device passes DAD, it may send an unsolicited NA to announce its presence.
3. **Topology Changes**: If there is a change in link-layer address or other significant parameters, a device may send an NA to update its neighbors.

## Summary

1. **RS** is generally used to discover routers when a device boots up or when the network configuration changes.
2. **RA** is used by routers to broadcast network configuration information either periodically or in response to RS messages.
3. **NS** is used mainly for address resolution, DAD, and verifying the reachability of a neighbor.
4. **NA** is used to respond to NS messages, to announce the success of DAD, or to inform neighbors about changes in configuration.
---
# Reference