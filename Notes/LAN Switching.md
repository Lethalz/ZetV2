2212261344
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# LAN Switching


A modern Ethernet LAN connects user devices as well as servers into some switches with the switches then connecting to each other.


## How a switch chooses to forward a ethernet frame

The LAN switch has one primary job: to forward frames to the correct destination (MAC) address.
Switches perform three actions:
1. Deciding when to forward a frame or when to filter (not forward) a frame, based on
the destination MAC address
2. Preparing to forward frames by learning MAC addresses by examining the source
MAC address of each frame received by the switch on a specific interface.
3. Preparing to forward only one copy of the frame to the destination by creating a
(Layer 2) loop-free environment with other switches by using Spanning Tree Protocol
(STP)

### Forwarding known frames

Uses a dynamically built table that lists MAC addresses

```ad-note 
A switch’s MAC address table is also called the switching table, or bridging table,
or even the Content-Addressable Memory (CAM) table, in reference to the type of physi-
cal memory used to store the table.
```

The switch uses this Table to understand where to send the frame.
If the Frame destination is known it will be on the Table
Each switch has its own table based on its interfaces (ports)

## Learning MAC adresses

Switches build the address table by listening to incoming frames and examining the source
MAC address in the frame. 

If a frame enters the switch and the source MAC address is not
in the MAC address table, the switch creates an entry in the table.


## What to do with unknown unicast and broadcast frames


When there is no matching entry in the table, switches forward the frame out all interfaces (except the incoming inter-face) using a process called ***flooding.***


### Loop Prevention

Spanning Tree Protocol(STP)

To prevent looping frames, STP blocks some ports from forwarding frames so that only one active path exists between any pair of LAN segments.


<img src = "https://i.gyazo.com/bfe5a2da48eceb99284fe6fb27d0aec7.png">

There should only be one way to get from larry to archie


## Mac Learning

To see a switch's MAC address table;;show mac address-table

Can be DYNAMIC or STATIC

Check the status of switch interfaces;;show interfaces status
<!--SR:!2023-01-04,3,250-->

Lists stats about incoming and outgoing frames on the interfaces;;show interfaces counters
<!--SR:!2023-01-02,1,230-->

Need to find a specific address on the mac table using the address;;show mac address-table address
<!--SR:!2023-01-02,1,230-->

Cmd to find addresses on a specific interface on the mac table;; show mac address-table interface \<interface>


##  Managing Mac Address Tables

The switch will remove the entries **due to age, due to the table filling,** and
you can remove entries using a command.

Switches remove entries that have not been used for a defined number of seconds (default of **300 seconds** on many switches)

Cmd to change mac table aging time;;mac address-table aging-timetime-in-seconds

Remove dynamic entries from the MAC address table;;clear mac address-table dynamic
<!--SR:!2023-01-02,1,230-->

`show` commands are user and enable level but `clear` is a enable level command


**Mutliple mac addresses can be on the same interface**











--- 
# Reference