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

**


Cables used in **10BASE-T and 100BASE-T**: 1,2,3,6. Crossover cable: 1→3, 2→6, 3→1, 6→2

Cables used in 1000BASE-T: 1-8.

**
## Ethernet Frame 

<img src = "https://i.gyazo.com/adb9c0c9d342a2b620d81b4c6494b73d.png">


Multicast MAC addresses: 01:00:5E:00:00:00-01:00:5E:7F:FF:FF

The last 23 bits of a multicast MAC address are used to map the relevant multicast IP address. Since multicast addresses have 28 variable bits, this is a one-to-many mapping, i.e. one MAC address is used for several (32, to be precise) IP addresses.


---
# Reference