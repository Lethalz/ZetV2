2209291618
	Status: #Exam
		Tags: [[CCNA 200-301]] [[Networking]]

# Using the Cisco CLI

### Basic Configuration
**enable**

Logs you into enable mode, which is also known as user exec mode or privileged mode

**configure terminal**

Logs you into configuration mode

**interface fastethernet/number**

Enters interface configuration mode for the specified fast ethernet interface

**reload**

An exec mode command that **reboots** a Cisco switch or router

**hostname name**

Sets a host name to the current Cisco network device

**copy from-location to-location**   i.e. copy run start

An enable mode command that copies files from one file location to another

**copy running-config startup-config**  copy run start

An enable mode command that saves the active config, replacing the startup config when a Cisco network device initializes

**copy startup-config running-config**

An enable mode command that merges the startup config with the currently active config in RAM

**write erase / erase startup-config**

An enable mode command that deletes the startup config

**ip address ip-address mask**

Assigns an IP address and a subnet mask

**shutdown / no shutdown**

Used in interface configuration mode. “Shutdown” shuts down the interface, while “no shutdown” brings up the interface.

**ip default-gateway ip_address**

Sets the default gateway on a Cisco device

**show running-config**

An enable mode command that displays the current configuration

**description name-string**

A config interface command to describe or name an interface

**show running-config interface interface slot/number**

An enable mode command to display the running configuration for a specific interface

`**show ip interface [type number]**`

Displays the usability status of interfaces that are configured for IP

**ip name-server serverip-1 serverip-2**

A configure mode command that sets the IP addresses of DNS servers

**Copy run tftp:
Copy start tftp**
**Copy run flash**:<config-name>

Should be used to back up your config elsewhere in case of epic failure on network device. 


hostname>
User Exec mode

hostname#
Privileged Exec mode (‘Enable’)

hostname(config)#
Global Configuration mode (‘Configure Terminal’)

hostname(config-if)#
Interface Configuration mode (‘Interface x’)

‘Exit’ drops back down a level.

‘End’ drops back to Privileged Exec mode from any level.

**terminal length (0-50)**

default terminal length is 24 
will see --more--

---
# Reference