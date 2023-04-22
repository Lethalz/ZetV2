2304212230
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Adjacencies and Passive Interfaces

-   A **neighbor adjacency** is a logical relationship between two neighboring devices in a network. It is established when the two devices exchange information about their routing tables and network topology.
-   Adjacencies are important for the correct functioning of routing protocols, as they allow the devices to exchange routing information and update their routing tables.
-   Adjacencies are established and maintained through a series of **protocol-specific messages** exchanged between the neighboring devices, such as hello messages in OSPF and EIGRP.
-   A **passive interface** is an interface that is not advertised to other devices using a routing protocol. This means that the router will not send routing updates out of this interface, but will still listen for updates from other devices.
-   Passive interfaces are useful for preventing routing loops and conserving bandwidth, as they prevent unnecessary updates from being sent out of interfaces that do not need them.
-   Passive interfaces can be configured on a per-interface basis, and can be used to selectively enable or disable routing updates on specific interfaces.
-   In OSPF, the passive interface command can be used to configure a specific interface as passive, while in EIGRP, the interface can be configured as passive using the passive-interface command.
---
# Reference