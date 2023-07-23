2303081752
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Fixed-Length Subnet Mask(FLSM)


![[Pasted image 20230308175441.png]]
---
If we start at /0 and ask how many /4 are in a /0 you would get 16 as the answer
This applies at any starting point not just /0 
For example: /18

<img src = 'https://i.gyazo.com/6ba6684be07dea410fa9f62c88a8650a.png'>


Types of questions:

<img src = 'https://i.gyazo.com/4b3d5e1aa2481c1beff464016e98a519.png'>

we got to 26 from out cheet sheet table   a /26 has a group size of 64 hence /26 being the goal here. SO 32 is the answer. and this can be from anywhere. If asked from /23 then the answer is 8 sub-networks.




Can use the power of 2 table to solve quickly

| 2^1 |  = 2   |
|----:|-----:|
| 2^2 |  = 4   |
| 2^3 |  = 8   |
| 2^4 |  = 16 |
| 2^5 |  = 32 |
| 2^6 |  = 64 |
| 2^7 |  = 128 |
| 2^8 |  = 256 |
| 2^9 |  = 512 |

Example : 

If you start with a /10 how many subnetworks could you create that were each a /16

/16 - /10 = 6
2^6 =64 so the answer is 64

If you start with a /22, how many sub-networks could you create that could contain 50 IP address (/26 has 64)

/26 - 22 = 4  , 2^4=16


If you start with a /15 what size subnetwork would you need to create 500 sub network

2^9 =512

/15 + 9  = 24   so the answer is 24

# Reference

https://www.youtube.com/watch?v=F05sDLXOFh8&list=PLIFyRwBY_4bQUE4IB5c4VPRyDoLgOdExE&index=8