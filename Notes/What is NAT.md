2305161407
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# What is NAT

**NAT (Network Address Translation)** is a process of changing the source and destination IP addresses and ports. Address translation reduces the need for IPv4 public addresses and hides private network address ranges. This process is usually done by routers or firewalls.

An example will help you understand the concept:

[![NAT process explained](https://study-ccna.com/wp-content/uploads/2016/01/nat_process_explained.jpg)](https://study-ccna.com/wp-content/uploads/2016/01/nat_process_explained.jpg)

Host A request a web page from an Internet server. Because Host A uses private IP addressing, the source address of the request has to be changed by the router because private IP addresses are not routable on the Internet. Router R1 receives the request, changes the source IP address to its public IP address and sends the packet to server S1. Server S1 receives the packet and replies to router R1. Router R1 receives the packet, changes the destination IP addresses to the private IP address of Host A and sends the packet to Host A.

There are three types of address translation:

1.  **Static NAT** – translates one private IP address to a public one. The public IP address is always the same.
2.  **Dynamic NAT** – private IP addresses are mapped to the pool of public IP addresses.
3.  **Port Address Translation (PAT)** – one public IP address is used for all internal devices, but a different port is assigned to each private IP address. Also known as **NAT Overload**.


![[9854a6f9447f89f721cac89232d6f3d3.png]]




<img src = 'https://i.gyazo.com/6b11d0039f1796672b65945c96473e31.png'>









---
# Reference