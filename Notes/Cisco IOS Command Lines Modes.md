2209291451
	Status: #Exam
		Tags: [[CCNA 200-301]] [[Networking]]

# Cisco IOS Command Lines Modes

### User Mode "User EXEC" `>` 
User Mode is the first mode a user has access to after logging into the router. 
The user mode can be identified by the `>` prompt following the router name. 
	This mode allows the user to execute only the basic commands, such as those that show the system's status. The router cannot be configured or restarted from this mode.

- Limited number of commands
- view-only mode
### Privileged/Enable mode (Privileged EXEC Mode) `#`

Privileged mode allows users to **view the system configuration**, restart the system, and enter router configuration mode. 

*Commands such as `reload` would not work in User EXEC mode because users are not allowed to restart the system.*

 ```ad-note
  Privileged mode also allows all the commands that are available in user mode.
```

Enable mode gets its name from the `enable` command, which moves the user from user mode to enable mode.

Privileged mode can be identified by the **`#`** prompt following the router name. 
 a user can change to privileged mode, by running the `enable` command. 
 Also, we can keep an enable password or enable secret to restrict access to privileged mode. 
enable secret password uses encryption, so it is recommended to use.

`disable` to return to User EXEC mode


```ad-note Note
The commands that can be used in either user EXEC or enable mode are called EXEC commands
``` 


### Global Configuration mode

Global Configuration mode is where we can enter configurations which affects the
device as a whole (as opposed to configuring a particular interface for example).

**Not one of the commands in user or privileged mode changes the switch’s configuration.**

Global Configuration mode allows users to modify the running system configuration. 

From the Privileged mode, a user can *move to configuration mode* by running the `configure terminal` or `conf t`  command from privileged mode.

To exit configuration mode, the user can enter `end` command or press Ctrl-Z [key combination](https://www.omnisecu.com/cisco-certified-network-associate-ccna/important-key-combinations-of-cisco-ios-command-line-interface.php)

``` ad-note Note
Use `do` to bypass not being able to use priv exec commands
The `end` command drops back down to Privilege Exec mode from any level. You
can also achieve this by entering ‘Ctrl-C
```

The Global Configuration mode can be identified as shown below.

`Router(config)#`

Change things like: 
Hostname
motd

# Sub Modes
Global Configuration mode has various sub-modes, starting with global configuration mode, which can be identified by the (config)# prompt following the router name. 

You Enter these Sub Modes Based on the Context of your configuration command.
i.e. If i use `interface FastEthernet 0/1` 
If i then type `?` i will get help in configuring Ethernet Interfaces.
``` ad-note Note
**Use `exit` to move from a submode back to global conf mode w/o using another Context-Specific subcommand.**
``` 

The Following are the important Global Configuration sub modes.

**•** **Interface mode** (Router physical interface configuration mode)
- Ip address
- enable/disable interface

`Router(config-if)#`

**•** **Sub-interface mode** (Router sub-interface configuration mode)

`Router(config-subif)#`

**•** **Console Line mode** (Router line configuration mode - console, vty etc.)
line console 0

`Router(config-line)#`

**•** **Router configuration mode** (Routing protocols configuration mode.)
OSPF , RIP , EIGRP
router rip
`Router(config-router)#`

#### Moving between modes with Context commands.
![[ca7621e78e0cf30bc3a684f46c6ad599.png]]

---
# Reference


![[4378dcf32e4ebef5bba85b1c9f5ce546.png]]