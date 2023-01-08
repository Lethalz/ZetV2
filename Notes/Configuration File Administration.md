2212241615
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Configuration File Administration


## Storing Config Files

- RAM/DRAM : Volatile Storage, used for the running-config (active)
- Flash Memory: Either a chip or a removable memory card, default location of CISCO IOS at Boot, Can be used to store any other files
- ROM : Read-Only Memory, stores boothelper(bootstrap) program that finds the Cisco IOS and manages the process of loading the IOS into RAM.
- NVRAM: Nonvolatile RAM , stores the intial or startup conf file taht is used when the switch is powered on.

When you use Configuration mode you only change the running-config

`copy running-config startup-config`

Backs up RAM to NVRAM

write erase
erase startup-config
erase nvram:



---
# Reference