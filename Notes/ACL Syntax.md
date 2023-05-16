2305151617
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# ACL Syntax


# A Particular Application

Use TCP or UDP if you want the ACE to apply to traffic for a particular application between a source and destination address

<img src = 'https://i.gyazo.com/a0e6157032545f17f2276510a2452fb5.png'>


# Between two addresses
Use IP if you want the ACE to apply to all traffic between a source and a destination address

<img src = 'https://i.gyazo.com/b10fc6bc33a87eae029f689c2573a614.png'>


# Source IP Value
For the Source IP you can specify multiple things, the source address, if it's any, or a single host.

<img src = 'https://i.gyazo.com/3460eafd9193f3b21c72be7ed96b03a8.png'>
**Any** and **host** are 'wildcards'

# Wildcards

Wildcards save you typing out the wildcard mask, these example mean the same thing.

<img src = 'https://i.gyazo.com/512cd3f9a8a885ccab9ed767eb8dc0b0.png'>


# Source port number

<img src = 'https://i.gyazo.com/d3c8c2c34ffc86d49ff60174999876a9.png'>

- Optional, defaults to ***any*** port.
- Any as in the wildcard `any`


# Destination Address

The destination address uses the same format as the source address
<img src = 'https://i.gyazo.com/1c88e313b00f62e976977a2d2e003092.png'>


# Final Options

<img src = 'https://i.gyazo.com/d9b377383a75771868bea74eaa0cf111.png'>



# Verification

`show access-list 100`

Tells you if there are addresses that are 'matching' the rule, Great for troubleshooting



















---
# Reference