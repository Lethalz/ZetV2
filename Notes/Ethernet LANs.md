2209261433
	Status: #Exam
		Tags: [[CCNA 200-301]] [[Networking]]

# Ethernet LANs

<img src = "https://i.gyazo.com/19e858642453c0854a4fd30fcaccd9ab.png">

**

MAC address: OU:IO:UI:VE:ND:OR

OUI – Organisationally Unique Identifier – ID assigned to a particular manufacturer

VENDOR – managed and assigned by the manufacturer

  

CSMA/CD (Carrier sense multiple access with collision detection) – if the sender detects a collision, it sends a jamming signal. All nodes cease transmitting and resume it after a random time.
Collisions can happen, but the algorithm defines how the computers should notice
a collision and how to recover
**


Cables used in **10BASE-T and 100BASE-T**: 1,2,3,6. Crossover cable: 1→3, 2→6, 3→1, 6→2

Cables used in 1000BASE-T: 1-8.

Ethernet NIC transmitters use the pair connected to **pins 1 and 2**; the NIC receivers
use a pair of wires at pin positions **3 and 6**. LAN switches, knowing those facts about what
Ethernet NICs do, **do the opposite**.

PC, ROUTER, APS - > 1,2
SWITCH, HUBS  -> 3,4
**
## Ethernet Frame 

<img src = "https://i.gyazo.com/adb9c0c9d342a2b620d81b4c6494b73d.png">


Multicast MAC addresses: 01:00:5E:00:00:00-01:00:5E:7F:FF:FF

The last 23 bits of a multicast MAC address are used to map the relevant multicast IP address. Since multicast addresses have 28 variable bits, this is a one-to-many mapping, i.e. one MAC address is used for several (32, to be precise) IP addresses.

802.3 Standards (Learn w/ spaced repitition)
	Throw fiber standards in that  `bitch

**Gigabit Ethernet Interface Converter (GBIC):** The original form factor for a removable
transceiver for Gigabit interfaces; larger than SFPs
**Small Form Pluggable (SFP):** The replacement for GBICs, used on Gigabit interfaces, with
a smaller size, taking less space on the side of the networking card or switch.
**Small Form Pluggable Plus (SFP+)**: Same size as the SFP, but used on 10-Gbps interfaces.
(The Plus refers to the increase in speed compared to SFPs.)

Ethernet shared mediaI refers to hubs causing connected devices to share bandwidth because of half duplex restrictions.

![[532a0dccacb7b24852419b582fb94dab.png]]

### Fiber

<img src ="https://i.gyazo.com/6640cb66f5606f3803b19c0e87de4c59.png">

The optical transmitter, shines a light into the core.

light reflects off the cladding back into the core


![[cb16997e8a23fc2fec73c40579fc338b.png]]


single-mode fiber uses a smaller-diameter core and a laser

![[b193c95217d51acf5c06b12f589f4a0d.png]]


Multimode improves the maximum distances over UTP  and it uses less expensive transmitters as compared with single-mode.

Single-mode allows distances into the tens of kilometers, but with slightly more expensive SFP/SFP+ hardware.



## Key Terms

**Frame Check Sequence**—A field in many data-link trailers used as part of the error-detection process.

**Tranceiver**—A term formed from the words *transmitter* and *receiver*. The hardware used to both send (transmit) energy over some communications medium (e.g., wires in a cable), and to process received energy signals to interpret as a series of 1s and 0s.

**10BASE-T**---The 10-Mbps baseband Ethernet specification using two pairs of twisted-pair
cabling (Categories 3, 4, or 5): one pair transmits data and the other receives data. 

**10BASE-T**---which is part of the IEEE 802.3 specification, has a distance limit of approximately 100 m (328 feet) per segment.

**100BASE-T**---A name for the IEEE Fast Ethernet standard that uses two-pair copper cabling, a
speed of 100 Mbps, and a maximum cable length of 100 meters.

**1000BASE-T**---A name for the IEEE Gigabit Ethernet standard that uses four-pair copper
cabling, a speed of 1000 Mbps (1 Gbps), and a maximum cable length of 100 meters.
2-way state In OSPF, a neighbor state that implies that the router has exchanged Hello


 
 

---
# Reference