2304212228
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Loopback interfaces

-   A **loopback interface** is a virtual interface in a router or switch that is not connected to any physical interface.
-   Loopback interfaces are identified by a unique **IP address** and **subnet mask**, and can be used as the source or destination address for testing connectivity or routing.
-   Loopback interfaces are always **up and running**, making them a reliable source for diagnostic and troubleshooting purposes.
-   Loopback interfaces can be used to **simulate a physical interface**, which is useful for testing and configuring network protocols and services.
-   Loopback interfaces are often used to provide a **stable IP address** for services, such as DNS, that need to be accessible even if a physical interface fails or is reconfigured.
-   Loopback interfaces are typically configured with a **/32 subnet mask**, which means that the interface is the only address in its network and can communicate only with directly connected devices or devices that have a route to the loopback interface subnet.
-   Loopback interfaces can also be used for **OSPF and EIGRP router IDs**, which are used for routing protocol calculations.
---
# Reference