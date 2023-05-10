

2305091900
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]] [[dhcp]]

# External DHCP server Config


The DHCP Discover packet is a 'Broadcast address' so If the DHCP server is in a different subnet the router will by default drop the packet.


We would need to make our router a DHCP relay in order to forward this request.

This is configured on the interface of the client.

`R1(config)#interface f0/1`
`R1 (config-if)#ip helper-address 10.10.20.10`

here 10.10.20.10 would be the DNS server on a different subnet
















---
# Reference