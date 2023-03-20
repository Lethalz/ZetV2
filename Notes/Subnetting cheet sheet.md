
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
what i mean by this
	Based on the information you provided, it seems that you are referring to the calculation of the network address for the IP range 10.1.1.85/29.
	
In this case, the /29 subnet mask means that the first 29 bits of the IP address are used to identify the network portion of the address, and the remaining 3 bits are used to identify the host portion of the address. In other words, the subnet mask is 255.255.255.248 in decimal format, which can be derived from the binary representation of /29, which is 11111111.11111111.11111111.11111000.
	To calculate the network address for this range, you need to set all the host bits to 0. In this case, the last 3 bits of the IP address are the host bits, so you need to set them to 0:

10.1.1.85 -> 00001010.00000001.00000001.01010101 ^^^

The result is:

10.1.1.80 -> 00001010.00000001.00000001.01010000 ^^^

Therefore, the network address for the IP range 10.1.1.85/29 is 10.1.1.80.

It seems that the statement "You can just multiple 8 by 10 to get to 80 quickly" may be a reference to the fact that the 4th octet of the network address is 80, which is 8 multiplied by 10. This may be a mnemonic device to help remember the network address for this range.

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