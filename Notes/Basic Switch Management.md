
2212271340
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Basic Switch Managment


The Work performed by a Networking Device can be split up into three categories:

1. Data Plane: The work the Device does to forward or filter data
2. Control Plane: the configuration and processess that control and change the choices made by the switch's data plane
3. Managment Plane: Deals with Managing the device itself.



### Securing the switch

`line con 0` console mode for the console
`line vty 0 15` vty line config for Telnet Pass



`password <value>` Defines the actual password used on the console or vty

`login` Tells IOS to enable the use of a simple shared password with no username on this line (console or vty)

<img src = "https://i.gyazo.com/753e9078def39d912c9ad58a390e7fff.png">

 The command to configure the enable password is a **global configuration command**: **enable secret** *password-value*

Command to configure the enablepassword;;**enable secret** *password-value*
<!--SR:!2023-01-02,1,230-->

Password Configuration checklist
	Step 1. Configure the enable password with the **enable secret** password-value command.
	Step 2. Configure the console password:
	A. Use the **line con 0** command to enter console configuration mode.
	B. Use the **password** password-value subcommand to set the value of the
	console password.
	C. Use the **login** subcommand to enable console password security using a
	simple password.
	S
	
	
	tep 3. Configure the Telnet (vty) password:
	A. Use the **line vty 0 15** command to enter vty configuration mode for all 16
	vty lines (numbered 0 through 15).
	B. Use the **password** password-value subcommand to set the value of the
	console password.
	C. Use the **login** subcommand to enable console password security using a
	simple password.   


## Local Usernames and Passwords For USER Mode

<img src = "https://i.gyazo.com/685fc751c6ee01d46c24e308355fd9fc.png">



Enable the User/Pass security with **login local** line which means use the local list of usernames for login.

Configure local username login checklist
	Step 1.
	Use the **username** name secret password global configuration command to
	add one or more username/password pairs on the local switch.
	Step 2.
	Configure the console to use locally configured username/password pairs:
	A. Use the **line con 0** command to enter console configuration mode.
	B. Use the **login local** subcommand to enable the console to prompt for both
	username and password, checked versus the list of local usernames/pass-
	words.
	C. (Optional) Use the **no password** subcommand to remove any existing sim-
	ple shared passwords, just for good housekeeping of the configuration file.
	Step 3.
	Configure Telnet (vty) to use locally configured username/password pairs.
	A. Use the **line vty 0 15** command to enter vty configuration mode for all 16
	vty lines (numbered 0 through 15).
	B. Use the **login local** subcommand to enable the switch to prompt for both
	username and password for all inbound Telnet users, checked versus the list
	of local usernames/passwords.
	C. (Optional) Use the **
 
 ** subcommand to remove any existing sim-
	ple shared passwords, just for good housekeeping of the configuration file.      

## SSH
To control which protocols a switch supports on its vty lines, use the **transport input** {all |
none | telnet | ssh} vty subcommand in vty mode, with the following options:

transport input all or transport input telnet ssh: Support both Telnet and SSH
transport input none: Support neither
transport input telnet: Support only Telnet
transport input ssh: Support only SSH*


SSH configuration checklist
	Step 1.
	Configure the switch to generate a matched public and private key pair to use
	for encryption:
	A. If not already configured, use the **hostname** name in global configuration
	mode to configure a hostname for this switch.
	B. If not already configured, use the **ip domain-name** name in global configu-
	ration mode to configure a domain name for the switch, completing the
	switch’s FQDN.
	C. Use the crypto key generate rsa command in global configuration mode
	(or the crypto key generate rsa modulus modulus-value command to
	avoid being prompted for the key modulus) to generate the keys. (Use at
	least a 768-bit key to support SSH version 2.)
	Step 2.
	(Optional) Use the **ip ssh version 2** command in global configuration mode to
	override the default of supporting both versions 1 and 2, so that only SSHv2
	connections are allowed.
	Step 3.
	(Optional) If not already configured with the setting you want, configure the
	vty lines to accept SSH and whether to also allow Telnet:
	A. Use the **transport input ssh** command in vty line configuration mode to
	allow SSH only.
	B. Use the **transport input all** command (default) or transport input telnet ssh
	command in vty line configuration mode to allow both SSH and Telnet.
	Step 4.
	Use various commands in vty line configuration mode to configure local user-
	name login authentication as discussed earlier in this chapter.

command lists status information about the SSH server itself;;show ip ssh
<!--SR:!2023-01-04,3,250-->

## Enabling IPv4 on the switch

The IP for the switch has nothing to do with actual switching, it's to support overhead managment traffic/

The switch then uses a NIC-like concept called a **switched virtual interface** (SVI),
or more commonly, a VLAN interface, that acts like the switch’s own NIC. 


<img src = "https://i.gyazo.com/43de3c857b12dfb6e4e9d71630826f0a.png">

 the management IP address does not have to be configured on the VLAN 1 interface like in the picture.

```ad-note
You should not try to use a VLAN interface for which there are no physical ports
assigned to the same VLAN. If you do, the VLAN interface will not reach an up/up state, and the switch will not have the physical ability to communicate outside the switch.
```

Ipv4 on a switch Checklist
	Step 1.
	Use the **interface vlan 1** command in global configuration mode to enter inter-
	face VLAN 1 configuration mode.
	Step 2.
	Use the **ip address** *ip-address* *mask* command in interface configuration mode
	to assign an IP address and mask.
	Step 3.
	Use the **no shutdown** command in interface configuration mode to enable the
	VLAN 1 interface if it is not already enabled.
	Step 4.
	Add the **ip default-gateway** *ip-address* command in global configuration mode
	to configure the default gateway.
	Step 5.
	(Optional) Add the **ip name-server** *ip-address1 ip-address2* … command in
	global configuration mode to configure the switch to use Domain Name System
	(DNS) to resolve names into their matching IP address.

**reminder** Change this into a flashcard marcus
To administratively enable an interface on a switch, use the **no shutdown** interface subcommand; to disable an interface, use the **shutdown** interface subcommand. 

To use DHCP for getting an IP use **ip address dhcp**


### Verifying IPv4

`show dhcp lease`

`show interfaces vlan 1`

`show ip default-gateway`





















---
# Reference