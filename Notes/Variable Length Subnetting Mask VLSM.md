2307171738
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Variable Length Subnetting Mask VLSM

![[df29b84ba8f681651a091e3adbb6c8b2.png]]
Number of IP addresses per network


1. Start a VLSM problem by listing out the /n that you would need for the number of hosts like this: 

![[b0b3279afee124d8edcc314076366e8c.png]]


2. Then allocate sub-networks to each starting with the "biggest" (most hosts)
	1. In this case it would be 31 (note we gave 31 the /26 because 27 is too small 32-2= 30 usable)

3. Dont forget to give the networks inbetween routers a subnet to if its router to router (point to point) then it's /30 
---
# Reference