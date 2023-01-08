2212292343
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Switch Interfaces
**duplex** {auto | full | half} and **speed** {auto | 10 | 100 | 1000}
**description** text interface subcommand lets you add a text description to the interface


![[93fe8071cad5e02b8c64b3681d761faf.png]]


show interfaces status :
Lists the details we just put in about the duplex, speed etc..

To Edit Multiple interfaces at once use this command;;**interface range FastEthernet 0/11 - 20** 
<!--SR:!2023-01-02,1,230-->


Brings down the interface;;shutdown
<!--SR:!2023-01-04,3,250-->

Brings up the interface;;no shutdown
<!--SR:!2023-01-02,1,230-->


Using the no command before set commands such as **duplex speed** resets it to default



Configuring both the speed and duplex on a Cisco Catalyst switch interface **dis-
ables** autonegotiation.


Autonegotiation is **disabled** if both speed and duplex settings are set manually.

If the other side has autonegotiation disabled, IEEE standard requires using the slowest supported speed and, if the speed is 10 or 100, half-duplex (full duplex otherwise). Since the slowest supported speed will almost (?) always be 10, the result is 10Mbits half-duplex. Cisco, instead, senses speed and uses full duplex at 1000 and higher.

| Line status               | Protocol Status (layer 2) | show interfaces status | description                                                                                                |
| ------------------------- | ------------------------- | ---------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Administratively down** | down                      | disables               | Interface configured with **shutdown**                                                                     |
| down                      | down                      | notcommect             | cable not commected or faulty                                                                              |
| down                      | down(err-disabled)        | err-disabled           | Port security, DHCP snooping, Dynamic AR{ Ispection or other security mechanism has disabled the interface |
| up                          |up                           |connected                        |Interface is working                                                                                                            |


in the show interfaces command output has counters here are some important ones


Ethernet input errors:

-   Runts – frames smaller than 64 bytes, can be caused by collisions
    
-   Giants – frames larger than the maximum frame size, i.e. 1518 bytes. Note: in some situations (802.1Q-in-802.1Q, MLPS) the frame can be larger than 1518 bytes but smaller than 1600 – these are valid frames and are called baby giants. Additionally, some installations deliberately use larger maximum frame size, up to 9000 bytes, these are called jumbo frames.
    
-   CRC – Frames that did not pass FCS, can be caused by collisions.
    

Ethernet output errors:

-   Collisions – all collisions that happened when transmitting a frame
    Late collisions – collisions that happened after 64th byte of a frame – sign of duplex mismatch (in half-duplex mode, collisions should be detected before the 64th byte.)**





---
# Reference