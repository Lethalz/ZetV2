2304212037
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Administrative Distance

1. **Common Administrative Distances**:
    
    - Directly connected: 0
    - Static route: 1
    - EIGRP summary route: 5
    - External BGP: 20
    - Internal EIGRP: 90
    - IGRP: 100
    - OSPF: 110
    - IS-IS: 115
    - RIP: 120
    - EIGRP external route: 170
    - Internal BGP: 200

--- 


Remember, the key is not just to memorize these charts but to understand the concepts behind them. The CCNA exam tests understanding and application, not just rote memorization. However, having these charts at your fingertips can save valuable time during the exam and boost your confidence.

If paths to the same destination are received from different routing protocols, their metrics cannot be compared

The Router needs a different method to choose when routes to the same destination are received from diffreent routing protocols, this is where *AD - administrative distance* comes in

Just like 'Metric' , the lowest value wins

| Route source        | default AD |
| ------------------- | ---------- |
| Connected Interface | 0          |
| Static Route        | 1          |
| External BGP        | 20         |
| EIRGP               | 90         |
| OSPF                | 110        |
| IS-IS               | 115        |
| RIP                 | 120        |            

AD is used to choose btw multiple paths learned via different routing protocols
Metric is used to choose btw multiple paths learned via the same protocol


### Floating Static Routes

If the best path to a destination is lost ( if a link went down) it would be removed and replaced with the next best route (dynamically)

However, what if we would like to to configure a static route as a backup for the route learned via a routing protocol.

Static routes have a AD of 1 (As seen in the table above) so how could we do that?

We can change the AD of a static route to make it act as the backup :

If we're using OSPF (AD 110)
then we'd add the following route to the ip table:
`R4 (config) #ip route 10.0.1.0 255.255.255.0 10.1.3.2 115`

It's a static route but we are changing it to a higher AD so that it does not overide the chosen routing protocol.

```
Gateway of last resort is not set

      10.0.0.0/8 is variably subnetted, 3 subnets, 2 masks
C        10.1.1.0/24 is directly connected, GigabitEthernet0/0
L        10.1.1.1/32 is directly connected, GigabitEthernet0/0
C        10.2.2.0/24 is directly connected, GigabitEthernet0/1
L        10.2.2.1/32 is directly connected, GigabitEthernet0/1
S        10.3.3.0/24 [1/0] via 10.2.2.2
```

Example \[1/0] is AD/Metric





---
# Reference