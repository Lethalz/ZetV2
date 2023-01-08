2209261430
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# TCPIP networking
<img src = "https://i.gyazo.com/7728793a5a2154aed71c5294e3821609.png">
RFC 1122, which defines a four-layer TCP/IP model, conflates physical and data-link layers into a single link layer, but it makes a lot of sense to separate the two. E.g. Ethernet can run on many types of physical medium, network layer interacts with Ethernet but does not need to know if there is copper or fibre underneath. Most authors use a five-layer TCP/IP model.
Each layer includes protocols and standards that relate to that category of functions.
    
What is a Networking Model?
	It is a network blueprint consisting of documents that explain one small function of computer networks, but as a whole the documents explain the process of computer networking.

The TCP/IP Model is the de facto model for networking today. However, OSI terminology is still used to describe certain aspects of networking.

What are RFC's?
	RFC (Requests for comments)
	Defines protocols for computer networking.

#### PDU's 

Each layer has its own PDU, once you get past layer 4 the PDU is just data

Layer 4 PDU;;Segment 
<!--SR:!2023-01-04,3,250-->
Layer 3 PDU;;Packet
Layer 2 PDU;;frame
<!--SR:!2023-01-05,4,270-->
Layer 1 PDU;;Bit
<!--SR:!2023-01-04,3,250-->

#### Encapsulation & De-encapsulation

Encapsulation
Is the adding of a Header and a trailer so the computer on the recieving end can know what to do with the information.

De-encapsulation
Then removes the header and trailer after using needed info for each layer until the destination device can read the data.

### Same layer interaction & Adjacent layer interaction

Same-layer interaction on different computers happens when two computers interact, i.e. when they send information from one computer to another. 

Adjacent-layer interaction happens on the **same** computer when the data is passed from the one layer to the other layer in the network stack.





# Reference
https://www.google.com/search?q=rfc+1122&rlz=1C1ONGR_enUS999US999&oq=RFC+1122&aqs=chrome.0.0i512l2j0i22i30l5j0i390l2.572j0j4&sourceid=chrome&ie=UTF-8`
---
 
# FlashCards

 happens on the **same** computer when the data is passed from the one layer to the other layer in the network stack.;;Adjacent-layer interaction



Is the adding of a Header and a trailer so the computer on the recieving end can know what to do with the information.;;Encapsulation

