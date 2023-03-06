
2303051033
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Subnetting cheet sheet

Base Instruction:

1. Use Given CIDR/mask to find column on Cheat Sheet
	a. CIDR/mask map to each other
	b. Locate Group Size
	c. Start at ".0" in relevant octet
	d. Increase by Group size until you PASS target IP
2. Number BEFORE target IP is **Network ID**
3. Number AFTER target IP is the **Next Network**
4. IP address BEFORE Next Network is **Broadcast**
5. IP address AFTER network ID is ** First Host**
6. IP address BEFORE Broadcast IP is **Last Host**
7. 2^(32-CIDR) number of IPs (usable is -2)





## Cheet Sheet

| Group Size | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|------|-----|----|----|----|---|---|---|---|
| Subnet Mask | 128 | 192 | 224 | 240 | 248 | 252 | 254 | 255 |
| CIDR | /25 | /26 | /27 | /28 | /29 | /30 | /31 | /32 | 
| 3rd Octet | /17 | /18 | /19 | /20 | /21 | /22 | /23 | /24 |
| 2nd octet | /9  | /10 |  /11 | /12 | /13 | /14 | /15| /16 |
| 1st Octet | /1 | /2 | /3 | /4 | /5 | /6 | /7 | /8 | /9 |




## Third Octet

10.4.211  .66 /18
         .0 .0
         .64 .0
         .128 .0
         .192 .0
     .***4***   ~~.256~~ .0
     .**5** .  0 .0

## First and second Octet

<img src = 'https://i.gyazo.com/186b5466bbd1ca2fa3c20a5a49d58331.png'>


If it goes past 256 on the first octet theres no other networks to go to

<img src = 'https://i.gyazo.com/b4ecc9072ebf451a2b793b13146e7dc3.png'>


# Speed Tips

### #1 
You can multiply the group size to get to the target more quickly

#### Example :  10.1.1.85 /29
You can just multiple 8 by 10 to get to 80 quickly

### #2

Each group size is a multiple of 128 so if your target is past 128 you can just start at 128.

10.3.3.147 /28

.128
.144
.160

### #3 Every group size lands on the subnet value of the same column and every column to the LEFT (on the subnet cheet chart)

10.3.3.197 /30 
                      x                        x
subnet : 128 192 224 240 248 252 254 255
                                              /30

SO we can start at .192

### # 4

You can start higher then subtract
---
# Reference

https://www.youtube.com/watch?v=5-wlfAdcmFQ&t=182s