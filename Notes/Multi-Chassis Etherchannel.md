2305131414
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Multi-Chassis Etherchannel


![[76b7d8e29306dd1424a6d9b779a7da9b.png]]

As you can see from the figure above, Acc4 has ether channel enabled on its ports however STP is still blocking one logic![[450d9e33802424f3a94ddd7ad649ac0e.png]]

-Spanning tree is still enabled but it treats it has one interface
- So if it gets a broadcast from any of the links it wont send it back through any of those ports hence no loop
- Supports full load balancing and redundancy

![[Pasted image 20230513141847.png]]