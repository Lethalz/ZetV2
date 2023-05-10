2305091956
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Cisco Router DHCP Client
Routers are typically manually congiured with static IP addresses however an exception is when an office is connected to the internet but does not have a static public ip, they would still need a public ip address to allow internal hosts outbound connectivity to the internet through NAT


In this case the router will receive the public IP address on its outside interface from the ISP via DHCP

On the outward facing interface (facing the ISP)
`R1(config)#interface f0/0
`R1(config-if)#ip address dhcp`
`R1 (config-if)#no shutdown`

Instead of configuring an actual ip add, we specify 'dhcp'

## verification

`show dhcp lease`


---
# Reference