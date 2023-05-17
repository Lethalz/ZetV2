2305161413
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Static NAT

With static NAT, routers or firewalls translate one private IP address to a single public IP address. Each private IP address is mapped to a single public IP address. Static NAT is not often used because it requires one public IP address for each private IP address.


Here is an example.

[![static nat example](https://study-ccna.com/wp-content/images/static_nat_example.jpg "static nat example")](https://study-ccna.com/wp-content/images/static_nat_example.jpg)

Computer A requests a web resource from S1. Computer A uses its private IP address when sending the request to router R1. Router R1 receives the request, changes the private IP address to the public one, and sends the request to S1. S1 responds to R1. R1 receives the response, looks it up in its NAT  table, and changes the destination IP address to the private IP address of Computer A.

## Configuration

```
R1(config)#ip nat inside source static 10.0.0.2 59.50.50.1
R1(config)#interface fastEthernet 0/0
R1(config-if)#ip nat inside
R1(config-if)#interface fastEthernet 0/1
R1(config-if)#ip nat outside
```

# Verification


```
R1#show ip nat translations
Pro Inside global Inside local Outside local Outside global
icmp 59.50.50.1:9 10.0.0.2:9 59.50.50.2:9 59.50.50.2:9 
--- 59.50.50.1 10.0.0.2 --- ---
```



## NAT Definitions

Inside local: Inside local is how our devices are configured and recognized within our own network. It's like their "local identity" that other devices within our network can use to communicate with them.

Inside global: Inside global is how the outside world sees our internal devices. It's like their "global identity" that devices outside our network use to communicate with them.

Outside local: Outside local is how an external device appears to our internal devices. It's like the "local identity" of an outside device as seen from within our network.

Outside global: Outside global is how the outside world perceives an external device. It's like the "global identity" of an outside device, known from within our network but aware that it exists outside.

#
---
# Reference