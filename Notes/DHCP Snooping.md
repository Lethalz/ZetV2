2305151205
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# DHCP Snooping

# What is DHCP Snooping? - Explanation and Configuration 


---

**DHCP Snooping** is a security technology on a Layer 2 network switch that can prevent unauthorized DHCP servers from accessing your network. It is a protection from the untrusted hosts that want to become DHCP servers. DHCP Snooping works as a protection from man-in-the-middle attacks. DHCP itself operates on Layer 3 of the OSI layer while DHCP snooping operates on Layer 2 devices to filter the traffic that is coming from DHCP clients.

## Why Do We Need DHCP Snooping?

Dynamic Host Configuration Protocol (DHCP) server is a vital role in every organization’s network as most end-user devices like PC and laptops are using DHCP to learn the IP addresses automatically. The host is making an IP address lease to the DHCP server.

To protect the host within the organization’s network to establish a connection from unauthorized rogue DHCP servers, we need to configure DHCP snooping on the Layer 2 switch where the unauthorized hosts are connected.

## DHCP Snooping Trusted and Untrusted Ports

In Cisco switches, DHCP snooping is enabled manually. Trusted ports should be manually configured and the rest unconfigured ports are considered untrusted ports. Most devices connected to trusted ports are routers, switches, and servers. DHCP clients like PC and laptops are commonly connected to an untrusted port.

How it works is that it will allow DHCP server messages like DHCPOFFER and DHCPACK that are coming from a trusted source. If the DHCP server messages are coming from untrusted ports, it will discard the DHCP traffic. The switch creates a table called the DHCP Snooping Binding Database. The DHCP snooping database registers the source MAC address and IP address of the hosts that are connected to an untrusted port.

  >[!note]
DHCP clients connected to an untrusted port are expected to transmit these DHCP messages: **DHCP DISCOVER** and **DHCP REQUEST**. If it transmits DHCPOFFER and DHCPACK, then the switch discards the DHCP packets. **DHCPOFFER** and **DHCPACK** are expected to be received on the trusted ports of the switch.


## Dynamic Host Configuration Protocol Snooping Configuration

For our configuration example, we will use the network topology below. There is a rouge DHCP Server trying to connect to our network through a man-in-a-middle attack.

[![DHCP Snooping](https://study-ccna.com/wp-content/uploads/DHCP-Snooping.jpg)](https://study-ccna.com/wp-content/uploads/DHCP-Snooping.jpg)

1. To enable DHCP snooping on the switch, we use the following command:

     SW(config)#ip dhcp snooping

2. After enabling DHCP snooping, configure FastEthernet 0/1 and FastEthernet 0/2 as a trusted port.

     SW(config)#interface range FastEthernet 0/1 - FastEthernet 0/2
     SW(config-if-range)#ip dhcp snooping trust
     SW(config-if-range)#no shutdown
     SW(config-if-range)#exit

3. Assign IP DHCP Snooping to the VLAN that is currently using the following command.

     SW(config)#ip dhcp snooping vlan 1

4. Assign an IP address to the gateway router’s interface gigabitEthernet 0/0.

     Router(config)#interface gigabitEthernet 0/0
     Router(config-if)#ip address 192.168.1.1 255.255.255.0
     Router(config-if)#no shutdown

5. On the legitimate DHCP server, select the **_Services_** tab and click on **_DHCP_**. Enable the service, and assigned the IP details, subnet mask, and DNS server IP. The name **_serverPool_** cannot be changed as it is existing already.

[![DHCP Snooping Configuration - Server](https://study-ccna.com/wp-content/uploads/DHCP-Snooping-Configuration-Server.jpg)](https://study-ccna.com/wp-content/uploads/DHCP-Snooping-Configuration-Server.jpg)

6. Enable DHCP on PC0 and PC1 and will get the IP address from the legitimate DHCP server.

[![DHCP Snooping Configuration - PC](https://study-ccna.com/wp-content/uploads/DHCP-Snooping-Configuration-PC.jpg)](https://study-ccna.com/wp-content/uploads/DHCP-Snooping-Configuration-PC.jpg)

7. Disconnect the legitimate DHCP server and observe that PC0 and PC1 are not getting any IP. The below snippet shows PC0 is getting an APIPA address. The PCs will not be able to get connected to the rogue DHCP server.

[![DHCP Snooping Configuration - APIPA](https://study-ccna.com/wp-content/uploads/DHCP-Snooping-Configuration-APIPA.webp)](https://study-ccna.com/wp-content/uploads/DHCP-Snooping-Configuration-APIPA.webp)

## DHCP Snooping Verification Commands

The following are the show commands that we can use on the switch to verify if DHCP snooping works as expected.

     Switch#show ip dhcp snooping
     Switch#show ip dhcp snooping bindinga
---
# Reference