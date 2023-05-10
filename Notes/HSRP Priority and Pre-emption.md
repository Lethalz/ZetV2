2305101045
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# HSRP Priority and Pre-emption


- You can choose which router will be the active by setting priority on the routers
- the router with the **higher** priority will be preferred (default is 100) 
- In the even of a tie the highest IP address wins
- If pre-emption is also enabled, when a igher priority router comes back online after a failure it will transition back to active
- If pre-emption is not enabled(default) , the lower priority router will remain active when the failed router comes back online
- This can be more stable if a higher priority router is flapping (coming up going down)
- If pre-emption is enable when this 'flapping' happens you will have intermittent outages everytime the 'flapping' router goes up and down


## Configuration

`R1(config)#interface g0/2`
`R1(config-if)#ip address 10.10.10.2 255.255.255.0`
`R1(config-if)#no shutdown`
`R1(config-if)#standby 1 ip 10.10.10.1`
`R1(config-if)#standby 1 priority 110`
`R1(config-if)#standby 1 preempt`


`R2(config)#interface g0/1`
`R2(config-if)#ip address 10.10.10.3 255.255.255.0`
`R2(config-if)#no shutdown`
`R2(config-if)#standby 1 ip 10.10.10.1`
`R2(config-if)#standby 1 priority 90`



## Verification
w
`show standby`


<img src = 'https://i.gyazo.com/147d46ba1fa613450367157ac950b006.png'>

## Active/Active

The only way to get an active/active configuration is by setting up two different standby groups and giving them two differnt IP addresses and also making R1 the priority on `standby 1` but making R2 the priority on `standby 2`

Then we confiure 50% of our PCs to use one default gateway or stand by and the other half to use standby 2 's gateway.'

<img src ='https://i.gyazo.com/df62e708a7b455314bd42d3103cd5b1f.png'>

##### Option 2

Another way to get loadbalancing
If we got multiple subnets going through the same pair of routers we can have one subnet going through one router and the other subnets going through the other

Notice in this example we are using two different interfaces in which instead of it being segmented by deafult gatways its segmented by which interface the subnets are going into.


<img src = 'https://i.gyazo.com/a747c5da7e2a36071e99cc0cc60b097e.png'>





















---
# Reference