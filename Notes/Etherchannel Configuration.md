2305131337
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Etherchannel Configuration



>[!Important] 
>EACH PORT CHANNEL GROUP NEEDS ITS OWN NUMBER IF A SWITCH IS GOING TO HAVE 2 PORT-CHANNELS THATS 2 SETS OF INTERFACES. YOU NEED TO USE PORT-CHANNEL 1 AND PORT-CHANNEL 2
>

### LACP Configuration

![[Pasted image 20230513132726.png]]


This creates interface port-channel 1
`(config)# interface range f0/23 - 24`
`(config-if-range)#channel-group 1 mode active`

Configure the interface settings on the port channels
`(config)#interface port-channel 1`
`(config-if)#switchport mode trunk`
`switchport truck native vlan 199`
- if you are plannign to change native-vlan

Configre matching settins on the other switch on the other side of the links:

Same commands as above on the second switch'

## PAgP Configuration


![[495b4e1c49423b0e9699430dc60821b9.png]]


`(config)#interface range f0/23 - 24`
`(config-if-range)#channel-group 1 mode desirable`

``(config)#interface port-channel 1`
`(config-if)#switchport mode trunk
`switchport truck native vlan 199`
- if you are plannign to change native-vlan

Configure matching settings on the other switch.

Same commands as above on the second switch'
`
# Static Config


`(config)#interface range f0/23 - 24`
`(config-if-range)#channel-group 1 mode on`

``(config)#interface port-channel 1`
`(config-if)#switchport mode trunk
`switchport truck native vlan 199`
- if you are plannign to change native-vlan

Configure matching settings on the other switch.

Same commands as above on the second switch


# Layer 3 etherchannel

![[Pasted image 20230513142616.png]]


---

# Verification

![[1c9ea42e4bfb15646c45d8f651f3444c.png]]



## Before


<img src = 'https://i.gyazo.com/9bef1862b408e8a3265dbdb5c56a3059.png'>

## After


<img src = 'https://i.gyazo.com/f2c7f6221b011b504786dc602da13a9f.png'>





Notice before F0/24 Was just block and not being used but after we configured Port Channel in the next `show spanning-tree vlan 1` we see that it is Po1 (Port-channel 1) which is what we created. And now we arent just wasting that whole link.



























---
# Reference