2305111518
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Manipulating Root bridge

You can elect the root bride by setting the brige pritotiy which you should make lower than the default
32768

<img src = 'https://i.gyazo.com/24a2cae0ae32284dc4e5c2bdeff8a7ef.png'>

`(config)# spanning-tree vlan 1 root primary`

Sets a secondary root bridge just incase the primary goes down
`(config)# spanning-tree vlan 1 root secondary`

![[0e4e310f0441305bd42356e0d6ef9fb7.png]]

---
# Reference