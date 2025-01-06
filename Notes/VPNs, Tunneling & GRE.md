2501061253
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]  [[CCNP SVPN]] [[VPN]]
# VPNs, Tunneling & GRE


What is a VPN? and what is it's purpose?

VPN stands for Virtual Private network, It's used to provide a secure channel for data over the Internet.

What does a VPN rely on and how does it work?
VPN's rely on tunnels, these tunnels are created by encapsulating data within special packets

In VPN (answer above), what are the three main protocols involved in the process and how do they work together? (Create excalidraw example)

The three main protocol's are carrier, encapsulator and passenger. 


What are the two MAIN types of VPNs? And what are they used for?

Remote access - Used for a single host to connect to a network. For example a user trying to connect to a work network.

What are two Examples of secure VPN Implementations and when are they used?

IPsec - Used in L2L (Site to Site) and Remote access
SSL/TLS - Used in remote Access mostly over a browser 


What are two Examples  insecure VPN Implementations?
GRE - general routing encapsulation and it supports multicast which is good for certain routing protocols. Becuase it's insecure is normally used along side other protocols such as ipsec.

DMVPN 



What is the Significance of (Insecure Encapsulation protocol) supporting Multicast?

It supports multicast which is good for protocols such as OSPF EIGRP that use multicast to send information to multple devices at once









---
# Reference

[[VPN Tunnel ELI5]]

[GRE RFC 2784](https://www.rfc-editor.org/info/rfc2784)