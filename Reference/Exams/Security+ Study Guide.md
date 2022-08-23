2208031833
	Status: #Exam
		Tags: [[Security+]] [[CyberSecurity]]

# Security+ Study Guide

# 1.0 Threats, Attacks, and Vulnerabilities

## 1.1 Compare and contrast different **types of social engineering techniques.**
- Social Engineering—an attempt by an attacker to convince someone to provide info (like a password) or perform an action they wouldn't normally perform (such as clicking on a malicious link)
- Social engineers often try to gain access to the *IT infrastructure* or the **Physical facility**.
- <u><em>Social engineering</em> is a big part of cybersecurity.</u> It often involves impersonation of some sort, attackers often use *impersonation* tactics, which are not easily countered via technology. It is important to understand that the best defense against this is user awareness and education. "Hacking People"
- Phishing—commonly used to try to trick users into "giving up personal information" *such as accounts and passwords*, click a malicious link, or open a malicious attachment.
- **Phishing** combines technical deceit with the elements of traditional social engineering. Be sure to know the variants of phishing attacks. 
- **Know the differences between the different types of phishing attacks.**

#### Eliciting Information

- Strategic use of casual conversation to extract information without the arousing suspicion of the target
- Techniques include: flattery, false statements, artificial ignorance, bracketing (vague statement in hopes of recieving a specific response).


#### Tailgating
- Simple Yet Effective
- Following closely behind someone who has authorized physical access in an environment.
- Playing on human emotions and desire to be polite.
```ad-note 
title: Solutions
- Mantraps (airlock like mechanisms that allow only one person to pass at a time)

```

#### Shoulder Surfing

- Shoulder surfing involves looking over someone's shoulder to obtain information illicitly.
- Watching someone put in their card pin at an ATM.
- Someone with binoculars peering through a window.

> [!note] Solutions
> - ATM's now include mirrors, so users can see who might be behind them and better-designed keypads to help conceal keypad entry.
> - Privacy screens are another deterrent to shoulder surfing.


#### Phishing and Related Attacks

- An attempt to acquire sensitive information by masquerading as a trustworthy entity via electronic communication, usually by email. 
- A mix of technical deceit and social engineering practices. The attacker must persuade the victim to intentionally perform a series of actions that provides access to confidential information.
- Spam: Is unsolicited emails sent to you by advertisers, attackers , or false actors.

>[!note] Solutions
> - There are proper security technologies and techniques at the client side, the server side and the enterprise level.
> - **Many organizations now prepend to the subject line some sort of notification if the email is external; this practice is known as prepending.**
> - Prepending can also be used in a malicious sense, like adding the word "SAFE" to a malicious file or suggesting topics via social engineering to uncover information of interest.

>[!note] Related:
>- Spearphishing – This type of phishing goes for a specific individual.
>- WhalePhishing (Whaling)—This is a targeted version of phishing, except for the size of the fish. Going after the CEO of a company instead of helpdesk.
>- Vishing - fake caller ID to appear as a trusted organization or vendor.
>-  Pharming - Redirects a user from a legitimate website to a fake one, usually done with DNS cache poisoning.
>- Smishing - SMS phishing. Phishing done over text.
>- SPIM (Spam over Internet Messaging) - The delivery of spam through the use of IM.


#### Reconnaissance

A common technique that comes in multiple forms:

##### Passive discovery
Techniques that do not send packets to the ttarget, like google hacking phone calls DNS and WHOIS lookups

##### Semi-passive discovery
Touches the target with packets in a non-aggressive fashion to avoid raising alarms of the target

##### Active discovery 
More aggressive techniques likely to be noticed by the target, including port scanning, and tools like nmap and metaploit.








>[!attention]+ Misc.
> - Credential harvesting is a common goal of phishing campaigns that involves capturing usernames and passwords.
> - E.g In the form of a bogus email bank's website. From there, the attacker's goal would be to get you to input and submit your username and password.
> - Countermeasures: email defense, anti-malware, EDR/XDR \* solutions that will check  URLs and block the scripts often used to execute the attack







#### Watering hole Attacks

- This attack is like spearphishing, but instead of using email, the attacker attacks a site that the target frequently visits. The goal is to compromise the larger environment—for example, the company the target works for or if they're targeting a company, a sandwich shop down the block that they know employees frequent.
- Just like a lion that waits at the community waterhole to capture its next victim, so too, do attackers wait for opportunities to compromise any of these victims.
- Commonly used in conjunction with a **zero-day exploit.**

> [!note] Solutions 
> - Set up a good baseline defense for your systems so it doesnt matter what they do.
> - Anti-virus/Malware








                         
 #### Typo squatting
- Also known as URL hijacking is a simple method used frequently for benign purposes, but it is also easily used for more malicious attacks. 
- Redirecting a user to a fictitious website based on a misspelling of the URL. 
- E.G www.gooogle.com 

>[!attention]+
> Always check that the website you are visting is secure.


#### Hoaxes and Influence Campaigns

- Hoaxes are not a threat in and of itself, it however takes place in the response people have to said hoax.
- Influence campaigns are coordinated actions that seek to affect the development, actions, and behavior of the targeted population. 
- Heavily enabled through social media.
- Cyberwarfare has recently become common among nations. 


#### Principles of Influence a.k.a Social Engineering Principles

- **Authority**: Job titles, uniforms, symbols, badges, and even specific expertise are all elements we often equate with authority. With such proclaimed and believed authority, *we naturally feel an obligation to comply.* 
- **Intimidation**: Authority plays to our sense of duty, and people with authority or power above us are in a position to abuse that power. There will be bad things if you don't comply.
- **Consensus/Social Proof:** Because people tend to trust like-minded people such as friends and family members, they frequently believe what others around them believe. "general agreement"
- **Scarcity and urgency**: Scarcity is commonly used as a marketing ploy. We tend to value something more if we believe it is *less available*. We are likely to be more impulsive if we believe something is the last one. 
- **Familiarity/liking**: People tend to comply with request from those whom they like or have common ground with. Liking regularly leads to trust. A social engineer might use humor or try to connect with more personally to open their victim up.
- **Trust**: Trust plays a part in all of these principles. We trust those with assigned authority. "Do unto others as you would have them do unto you." The reciprocation that occurs and the equity that is established helps build trust.









## 1.2  Given a scenario, analyze potential indicators to determine the **type of attack.**

#### Malware

- *Malicious software* is a serious problem in today's network environment. This software is intended to harm a user's computer or data.   
- The target is not only the information stored on the local computer, but also the other resources and other computers on the network.
- The most serious malware typically takes advantage of system vulnerabilities, which makes the malware more dangerous and enables it to spread more effectively.

To determine whether a system has been infected, examine the following critical areas.

- Memory, Registries, Macros.

#### Viruses

- A virus is a program or a piece of code that runs on a computer, often without the user's knowledge and without their consent.
- A virus is made to replicate when it executes and launches, attaching to other files and adds its code to other application's code.
- Viruses can replicate over networks, and even bypass some security systems.
- A Virus maker's goal is to increase infection and decrease detection.
- A **fileless malware** is more insidious. These viruses "live off the land" and use legitimate tools that are usually part of the operating system or IT based tools to do their bidding. Such as Windows PowerShell and such.
	 - Does a good job of avoiding anti-virus.  
	 - Operated in memory but never in a file or app.


>[!alert] Viruses are executed by some type of action, such as a running a program.
 
There are different types of viruses based on how a virus lives in a system:

- Resident Virus: Resides in memory, which means it is loaded each time the system starts and can infect other areas based on different actions. This method allows a virus to remain active even after any host program terminates. *Have to be called up from some type of storage.*
- Nonresident virus: Once executed, this type of virus looks for targets locally and also across the network. The virus then infects those areas and exits. Unlike a resident virus, it does not remain active.
- Boot sector virus: This type of virus is placed into the first sector of the hard drive so that when the computer boots, the virus loads into memory.
- Macro virus: This type of virus is inserted into a Microsoft Office document and emailed to unsuspecting users.

>[!note] Viruses exhibit several potential characteristics that further define their classifications.
- Program- and file-infecting virus: Most common viruses are this type, The virus infects EXE program files and becomes active in memory. Seeks out other files to infect. 
- Polymorphic virus: A polymorphic virus can change form or signature each time it is executed to avoid detection. Instead of looking for a specific signature heuristic-based scanning examines the instructions running within a program.
- Armored virus: Aim is to make detection as difficult as possible. They make it difficult to analyze functions, creating a metaphorical layer of armor around the virus. 
- Stealth Virus: Tries and avoids detection, for example, a stealth virus removes itself from an infected file and places a copy of itself in a different location.
- Multipartite virus: A multipartite virus infects EXE files and also attacks the master boot record of the system. 

#### Worms

- Worms are similar to viruses, but worms are *self-replicating* and **do not need a host file.** 
- A worm is built to take advantage of a security hole in and existing application or OS, then find other systems running the same software, and then automatically replicate itself to the new host.

#### Trojan
 - programs disguised as useful applications, think of the trojan horse that they used to get into the castle undiscovered.
 - Trojans are often classified by their payload or function.
 - Common: **backdoor, downloader, infostealer, and keylogger.**
	- **Backdoor Trojans:** Open a less obvious entry into a system for later access.
	- **Downloader Trojans:** download addition often malicious software onto infected systems.
	- **Info stealer Trojans**: attempt to steal information from the infected machine.
	- **Keylogger Trojans:** Monitor and send keystrokes typed from the infected machine to a remote attacker.
- A *backdoor Trojan* is also known as a **remote
access Trojan (RAT).** 

> [!note]+ Solution
>- Only allow software from trusted sources.
>- Keep control of user downloads
#### Rootkits
- A piece of software that can be installed and hidden on a computer mainly to fuck the system up and gain escalated privileges.
- Enables the attacker to gain root access to the victim's computer, which can compromise other machines on your network.
- Rootkits can be included as part of software packages, can be installed through an unpatched vulnerability, or downloaded.
- Many rootkits run in the background, you can usually spot one by looking in the memory processes, and checking programs.
- Kernel rootkits modify the kernel component of an operating system. Can intercept system calls passed to the kernel and can use encryption to protect outbound communications.
- Will piggyback on commonly used ports to communicate without interrupting other applications to stay hidden from administrators and detection tools.
- You can avoid a rootkit by **not having root privileges in the first place.**
- Keep security patches up-to-date!
- Anti-malware software , EDR/XDR




#### Logic Bombs 
- A virus or Trojan designed to execute malicious actions when a certain event occurs or after a certain period of time.
- A logic bomb is also referred to as slag code. The malicious code is usually planted by a disgruntled employee.

#### Bots

 - An automated computer program that needs no user iteration. 
 - Bots are systems that outside sources can control.
 - Many of these bots are unprotected home pcs
 - A botnet is a large number of these bots, and they are used for attacking other systems. Also known as a zombie army.
 - Can be created through a port that has been left open or a unpatched vulnerability.
 - Normally used for DDoS attacks.



#### Crypto-Malware

- Is a specifically designed tool to find valuable data on a victim's pc and uses cryptography to encrypt the data to prevent access.
- Ransomware is just that, butt the attacker attempts to hold the victim's information for ransom. 
- To *Extort Money*
- Known for heavy CPU use.
- E.G Wannacry



#### Potentially Unwanted Programs (PUPs)

- It is a program that is most likely unwanted, sometimes even with the user's consent.
- Includes: spyware, adware, dialers, and these programs are often downloaded in conjunction with programs that users actually want.

##### Spyware 
Undesirable code that behaves as advertising, collection of personal data and change a PC's configuration without consent. It sends your information across the internet to some unknown entity.

Symptoms Include: 
- The system is slow, especially on the Internet
- Desktop is slow in coming up
- Clicking a link does nothing or takes you to an unexpected page
- Browser home pages changes without user input

Spyware monitors user activity on the system, possible including key strokes typed. The information is then sent to the originator of the spyware.

##### Adware

It is a form of spyware that gives advertisers an online way to make a sale. Companies offer to place ads in their web properties. A portion of the revenue from banner sales goes to the company placing the ad.

##### Crypto-mining software

Attackers will put this software on your computer so that they can use your resources to "mine" more bitcoin or any cryptocurrency for that matter.




### Physical Attacks

Skimming is and attack type that has gained more widespead attention. It involves copying data from a credit or debit card by using a specialized terminal.
The card can subsequently be cloned, in a process known as card cloning.

### ADVERSARIAL ARTIFICIAL INTELLIGENCE (AI)

Artificial intelligence (AI) involves the applicationof various techniques to solve a variety of problems and challenges. Just as information security has benefited from
machine learning, the technology can also be used for nefarious purposes by an adversary.


Attackers are not only using machine learning for their gain but are perpetrating attacks against ML algorithms.

### Password Attacks
Because passwords are the most common from of authentication and user access control is a password. So you can imagine that it is one of the first places attackers look to exploit.

Different types of Password attacks:
- Dictionary attack: Are the most succesful on simple passwords because the attack just tries each word from the supplied list. 
- **Brute force attack**: Relies on cryptoanalysis or hashing algoriths that are capable of performing exhaustive key searches. Can crack short passwords more quickly than can dictionary attacks. **Account lockouts** are a way to mitigate these attacks. Although there are ways to brute-force offline. 
- ***Password spraying*** is a slow approach, it's using a single password attempt over multiple accounts.
- ***Rainbow table*** is a very large set of precomputed hash values for every possible combination of characters that is able to reverse a cryptography has function. 
- **Birthday attack** is a cryptographic method of attack against a secure hash. Finds collisions within hash functions and so is a more efficient method of brute-forcing one-way hashing. **Commonly targets digital signatures.**
    - if 23 people are in a room, the probability that two of those people
have the same birthday is 50%
                 


## 1.3 Given a scenario, analyze potential indicators associated with **application attacks.**

#### Privilege escalation

- This allows the attacker to gain **higher-level access** to their target's system, this usually is done by exploiting a vulnerability, a bug or a Zero-day exploit.
- With the newly gained access, the attacker has more capabilities or in other words, he expands his attack surface.
- Of course, these types of vulnerabilities are of the highest concern and have to be dealt with quickly.
- *Horizontal privilege escalation* is not gaining a higher privilege, but the privilege of another user.

> [!note] Solutions/Mitigations
> - Patch Quickly
> - Update anti-virus/anti-malware
> - Data execution prevention
> - Address space layout randomization 


#### Cross-site scripting

XSS or cross site scripting is one of the *most common web app development errors.*
It takes advantage of the trust a user has for a site and its complex and varied.
By placing a malicious client-side script on a website, an attacker can cause an unknowing browser user to conduct unauthorized access activities. 
Occurs when web apps contain 'reflected input'.
*Can be boiled down to a **javascript injection** between websites*

* Non-Persistant (reflected) XSS attack

	* Website allows scrips to run in user input, search box is a common source. The attacker emails a link that takes advantage of this vulnerability.
	* The script embedded in the URL executes in the victim's browser as if it came from the server.
	* The attacker uses credentials/ session IDs / and cookies to steal victim's information without their knowledge.

* Persistent (stored) XSS attack


	* Attacker posts a message to a social network which includes the malicious payload. It is now “persistent” because it is based in the webpage and not the link.
	* No specific target, usually it allows anyone to visit the page, however this type of attack is very dangerous especially for social networking. Everyone who views the message can post it themselves and have the malicious payload propagated even further.

> [!note]+ Solutions
>  - Never click an untrusted link
>  - Consider disabling certain javascript features
>  - Keep your software and applications updated
>  -  Validate input to input fields (developer)

#### Code injections

- Is done by adding your own information into a data stream, usually enabled because of *bad programming*.

###### SQL injection

- Structured Query Language- the most common relational database management system language.
This type of injection is normally done by modifying SQL requests..
Prevented through good code practices on the DEV side.

##### XML injection and LDAP injection

- XML—Extensible Markup Language : A set of rules for data transfer and storage.
This type of injection is done by modifying XML requests just like SQL
- LDAP—Lightweight Directory Access Protocol
 This type of injection modifies LDAP requests to manipulate application results.

##### DLL Injection

- Dynamic-Link Library: A Windows library containing code and data, many applications use this library.
 Attackers can inject a DLL and have an application run a program and it runs as part of the target process.


#### Buffer Overflow

A **buffer** is a place where data is stored. Buffers have a *fixed size*. A program must be very careful to not put more data into the buffer than its size allows, or else the buffer will "overflow" and damage the data in surrounding memory. It would be like if your toilet overflowed and water spilled onto your floor, damaging your flooring and drywall.

If a malicious hacker has control over the data that is put into a buffer, sometimes **they can control what data overflows out of the buffer as well**. This allows them to replace _other_ data in memory, with the data they chose. This can change the behavior of the program, allowing the hacker to manipulate it to his/her will.

An **integer overflow** is another type of overflow that is specific to whole numbers, known as integers. For example, 12 is an integer, but 12.1 is not. When programs do not carefully account for integer overflows, undesirable behaviors and
consequences can result.

#### Replay Attack

A **replay attack** is when a third party intercepts and “replays” a secure data transmission, allowing the third party to *interact with the receiver* as though they were the original sender. It’s a relatively common and surprisingly simple form of cyberattack.
Hackers can eavesdrop on data exchanges being sent through networks—this type of eavesdropping is known as **packet sniffing**. Once data is intercepted it is replayed in the same form—usually a session ID, an email, or a message. Replay attacks are often used to steal *usernames and passwords*, or trick users into sending funds to the hacker.

> [!note] Solutions
> - **To prevent this, passwords are often “[hashed and salted](https://www.expressvpn.com/blog/internet-security-technical-glossary/).”**
> - Encryption : Use a session ID with the password hash to create a unique authentication hash each time.
> - Data/Time stamps


##### Cookies and Session IDs

- Cookies are information stored on your computer by the browser, they are used for tracking, personalization, session management and security.
- Could be considered a privacy risk because of all the personal data those cookies contain about you.
- *Session IDs* are typically stored in the cookie in order to maintain sessions across multiple browser sessions. ***Pass the hash*** - A type of replay attack in which the attacker provides the hashed password to an accepting authentication scheme.
	- Session Hijacking : When an Attacker gets a hold of your session ID and pretends to be you.
	- Solutions : Encrypt end-to-end
		- They can't capture your session ID if they can't see it


#### Request forgeries

##### Cross-site requests
- Common and legitimate
- Website pages consist of client-side code and server-side code.
	- Client side : Renders the page on the screen , HTML , JavaScript.
	- Server side: Performs requests from the client, HTML, PHP , any requests from client.
- **Cross-site request forgery**
- takes advantage of inherent trust that a web application has for the user
	- requests are made without your consent and knowledge
	- the Attacker posts a Facebook status on your account.

> [!note] Solutions
> - DEV oversight
> -  The app should have anti-forgery techniques added 
> -  Usually a cryptographic token to prevent a forgery
> - Same-origin policy

EXAMPLE: 
<img src="https://i.gyazo.com/98e60293f7db7a11e139882e8b751c38.png"> 

[Reference](https://www.youtube.com/watch?v=fmtqMzP7aXI&list=PLG49S3nxzAnkL2ulFS3132mOVKuzzBxA8&index=31) @ 4:25


##### Server-side request forgery (SSRF)

- Attacker finds a vulnerable web application and sends malicious requests tto the web server then the web server would then perform the request on behalf of the attacker.
- Cause by bad programming or bad DEV oversight. Server should validate the input and the responses, these are rare but critical.

EXAMPLE :
<img src = "https://i.gyazo.com/a94a6da99e1b45a1232963ee056a935a.png">
[Reference](https://www.youtube.com/watch?v=fmtqMzP7aXI&list=PLG49S3nxzAnkL2ulFS3132mOVKuzzBxA8&index=31) @ 5:26

##### Driver Manipulation

**Drivers** are the interation between the hardware of your computaer and your OS, which makes them a perfect medium for attack.

- Shimming : Filling the space between two objects. A middleman.
	 - Windows includes its own shim via backwards compatibility with previous windows versions.
	- Malware authors write their own shims to get around security.
- Refactoring: Metamorphic malware, a different program each time it's downloaded. Used to dodge antivirus and anti-malware because they stop malware by signatures.
	- Can intelligently redesign itself.


##### SSL stripping / HTTP downgrade

SSL stripping attacks (also known as SSL downgrade or HTTP downgrade attacks) are a type of cyberattack in which hackers downgrade a web connection from the more secure HTTPS to the less secure HTTP. This makes all communications unencrypted and sets the stage for a [man-in-the-middle attack](https://www.keyfactor.com/blog/what-is-a-man-in-the-middle-attack/), in which the hacker sits in the middle of a conversation listening or intercepting information.

- Combines an on-path attack with a downgrade attack, It's difficult to implement, but big returns for the attack/
- For this attack to work the attack must sit in the middle of the conversation, they need to modify data between the victim and web server.
- Done by Proxy server, ARP spoofing rouge wifi hotspot
- Victim doesn't see any difference except that the S is missing for HTTPS
- Works on client and server *SSL And TLS*


<img src ="https://i.gyazo.com/bf9426db51515dad970a13f63d668851.png">


##### Race Condition

A **race condition** is an undesirable situation that occurs when a device or system attempts to perform **two or more operations at the same time**. 

Because of the nature of the device or system, the operations must be done in the proper sequence to be done correctly.

- Time-of-check to time-of-use attack (TOCTOU)
 it is an asynchronous attack that exploits timing. TOCTOU takes advantage of
the time delay between the checking of something and the usage of something.

EXAMPLE: A simple example of a race condition is a light switch. In some homes, there are multiple light switches connected to a common ceiling light. When these types of [circuits](https://www.techtarget.com/whatis/definition/circuit) are used, the switch position becomes irrelevant. If the light is on, moving either switch from its current position turns the light off. Similarly, if the light is off, then moving either switch from its current position turns the light on.


##### Memory vulnerabilities

Memory leak: Unused memory not properly released, so it begins to slowly grow in size it eventually uses all available memory and the system crashes.
 - **NULL pointer**/object deference 
	 - Dereferencing means taking away the reference and giving you what it was actually referring to.
	 - Technique that references a empty portion of memory, application crashes, debug information displayed also a denial of service. 

##### Directory Traversal / Path traversal 
Read files from a web server that are outside the website file directory.

Web server software vulnerability and web app code vulnerability.

Able to view files you aren't supposed to read.

##### Improper error handling
- Make sure that your error messages aren't showing too much information such as network info memory dump stack traces database dumps, etc.
- easy to fix and find

##### Improper input handling
All input should be considered malicious, check everything, trust no one.
Allowing invalid input can be devastation, SQL injections, overflows, etc.

##### API attacks
Application Programming Interface

Attackers look for vulnerabilities in this new communication path, exposing sensitive data , dos , intercepted communication, privileged access, etc.

<img src = "https://i.gyazo.com/a849eef129b1c8d5fa6c1905c2ebe2a1.png">


##### Resource exhaustion

A specialized DoS attack, using up all your resources if possible.

I.E zip bomb: compressed file that will slowly fill up your storage space to capacity if opened , DHCP starvation : Attacker floods a network with IP addess requests.




## 1.4 Given a scenario, analyze potential indicators associated with **network attacks**

#### Rouge access point and Evil Twins

##### Rouge Access Points

An unauthorized wireless access point, may be added by an employee doesn't necessarily have to be an attack, but it is still a problem to your network. It's becoming very easy to plug in a wireless AP or enable wireless sharing on your phone or OS. It's always a good idea to schedule a periodic survey and be aware of your surroundings.

NAC (Network Access Control) 802.1X is a good deterrent. 
A NAC system can deny network access to noncompliant devices, place them in a quarantined area, or give them only restricted access to computing resources, thus keeping insecure nodes from infecting the network.


##### Evil Twins

An evil twin attack is **a spoofing cyberattack that works by tricking users into connecting to a fake Wi-Fi access point that mimics a legitimate network**. 
The most dangerous evil twin attacks work by tricking victims into thinking that they are connecting to a reliable public Wi-Fi network. To make the attack as believable as possible, hackers will choose a location with free Wi-Fi and set up an AP, then name it something that a victim thinks is the right Wi-Fi.


#### Bluejacking and Bluesnarfing

##### Bluejacking
Sending of unsolicited messages to another device, via Bluetooth. The typical functional distance of Bluetooth is about 10 meters, depending on antenna and interference.
However, Bluejacking **does not involve device hijacking**, despite what the name implies. The bluejacker may send only unsolicited messages. Hijacking does not actually occur because the attacker never has control of the victim’s device. At worst, bluejacking is an annoyance.

**Bluesnarfing and bluebugging,** however, are actual attacks that may result in a user losing control of his device. Although bluejacking, bluesnarfing and bluebugging use Bluetooth as the point of entry, bluesnarfing and bluebugging are far more harmful.

#### Wireless Disassociation Attacks 

A type of DoS attack in which the attacker breaks the wireless connection between the victim device and the access point. The method is based on the use of a special disassociation frame specified under IEEE 802.11. Transferring such a frame to the target device breaks the connection, and the Wi-Fi protocol does not require any encryption for it. For a successful attack, the cybercriminal needs to know only the victim’s MAC address or Wi-Fi address.


#### Wireless Jamming

##### Radio frequency (RF) jamming
Denial of Service
A jamming attack is **the transmission of radio signals that disrupt communications by decreasing the Signal-to-Inference-plus-Noise ratio (SINR)**

Counteracting a jamming attack is both simple and complicated. It is simple because most jamming attacks require physical proximity.

Many enterprise-grade devices provide power levels that can be configured and have the capability to identify and locate rogue devices that are causing interference.

#### RFID (Radio-frequency identification)

An RFID tag works by [transmitting and receiving information](http://electronics.howstuffworks.com/gadgets/high-tech-gadgets/rfid1.htm) via an antenna and a microchip — also sometimes called an integrated circuit or IC. The microchip on an RFID reader is written with whatever information the user wants.
There are two main [types of RFID tags](http://blog.atlasrfidstore.com/active-rfid-vs-passive-rfid): **battery-operated and passive.** As the name suggests, battery-operated RFID tags contain an onboard battery as a power supply, whereas a passive RFID tag does not, instead working by using electromagnetic energy transmitted from an RFID reader. Battery-operated RFID tags might also be called active RFID tags.

<img src = "https://butlertechnologies.com/wp-content/uploads/rfid-tag.jpg">

Types of Attacks :

- Data captures : View communication , Replay attack
- Spoof the reader : write your own data to the tag
- Denial of service : signal jamming
- Decrypt communication 


#### NFC (Near field communication)

-  Two way wireless communicationon
- Payment systems use this option
- Bootstrap for other wireless
- Access token or, Identity card.


Security concerns:
- Remote capture 10 meters for active devices
- Frequency jamming
- Relay / Replay attack  "On-Path attack"
- Loss of RFC device control 


#### Cryptographic nonce "Salt"

- Arbitrary number : Used once, "for the nonce" - for the time being.
- A random or pseudo-random number, something that cant be reasonably guessed.
- Use a nonce during the login process, Salting your password makes it more secure.

#### On-path network attack (MITM)

An on-path attack is an attacker that *sits in the middle* between two stations and is able to *intercept,* and in some cases, *change that information that’s being sent* interactively across the network. This is a type of attack that can occur without *anyone knowing* that anyone is sitting in the middle of the conversation.
The attacker redirects your traffic then passes it on to the destination, so you never know your traffic was redirected.
Normally done with ARP poisoning because ARP has no security.

####  MAC Flooding and Cloning

In networking, the term MAC address refers to the **Media Access Control** address of a network card. We often refer to this MAC address as the physical address of the card because *every single* adapter card has a different MAC address.

- 48 bits/ 6 bytes long; Hexidecimal 

<img src = "https://i.gyazo.com/fbc216a1334258cd348d0ae82cd6d61d.png">


##### Lan Switching

**LAN switching** is a form of packet switching in which the data packets are transferred from one computer to another over a network. Switching technologies are vital to network design, as these technologies **permit the traffic to be sent only where it is required; in most of the cases,** making use of fast, hardware-based methods. LAN switching technology helps to *improve the overall efficiency* of local area networks and *address the existing bandwidth issues*

##### Mac Flooding

The MAC Flooding is an attacking method intended to compromise the security of the network switches. Usually, the switches maintain a table structure called MAC Table. This MAC Table consists of individual MAC addresses of the host computers on the network which are connected to ports of the switch. This table allows the switches to direct the data out of the ports where the recipient is located.

The attacker knows the MAC table is only  so big, so the attacker starts sending traffic wiht different source MAC  addresses to force out the legitimate MAC addresses, the table fills up and the switch begins flooding traffic to all interfaces.
This effectively turns the switch into a hub , because all traffic is transmitted to all interfaces. This is a great time for the attacker to start collecting information from the network because broadcast messages are normally sent in-the-clear.

##### MAC Cloning
The attacker changes their MAC  adress to match the MAC address of an existing device. They will use this to circumvent filters like MAC FILTERS so they can create a Dos or disrupt communication on the network. Many switches will look for mac address spoofing or cloning so that these problems dont happen.


#### DNS posioning


DNS poisoning, also known as DNS cache poisoning or DNS spoofing, is **a highly deceptive cyber attack in which hackers redirect web traffic toward fake web servers and phishing websites**.

Usually done by either modifing the client host file or sending a fake response to a DNS request (MITM/On-Path)

##### Domain hijacking

The attacker gets access to the domain registration has control on where the traffic flows.
Done by social engineering, or brute forcing.

##### URL hijacking
URl looks like the real site.
Used for malicious softaware installation or sold back to the company that it's close to.

TYPES: 
- Typosquatting/brandjacking
- Outright misspelling
- A typing error
- Different TLD .com , .org, etc..

#### Denial of Service

- Force a server/ service to fail
- takes advantage of a design failure 
- cause a system to be unavailable
- smokescreen for other attack 
- Doesnt have to be complicated.

- DDoS : Launch a army of computers normally with a botnet to take down a system.
- DDoS Amplification : Uses Protocols with little authentication like NTP DNS ICMP
- Command and Control is the center of a botnet attack
- Disgruntled or malicious internal users may use DDoS attacks todisrupt services without any outside influence.

![[Pasted image 20220817135806.png]]
##### Application DoS
Make the apllication work harder 
fill the disk space
Overuse a mesurable cloud resourevec
Increase the cloud server response time

##### Operation technology DoS
The hardware and software for industrial equipment: electric grids, traffic control , manufacturing plants, etc..


#### Malicious scripts

Scripts allow you ti automate tasks so you dont have to be there however for attackers it helps automate their attacks.
Windows powershell is a big medium for attackers to attack your system/
Python is used in conjunction with scripts to attack systems , cloud based systems.

- Shell scripts, etcc
##### Macros
Automates functions within an application , desifned to make the applicaitons easier to use but attackers use it to attack unsuspecting users.

**VBA Visual basic for applications** is used to automate processes within windows applications it is a powerful programming language.








## 1.5 Explain different threat actors, vectors, and intelligence sources.



#### Threat actors and attributes

A threat actor is an individual, a group, or an entity that contributes
to an incident—or, more simply, a person or an entity that executes a given threat.
Threat actors are an **Advanced Persistant Threat (APT)** - Meaning they are in the network and undetected for a elogated period of time.

##### Insider Threats

Attacks dont always come from malicious actors from the outside but **from the inside.**
In many cases insiders are just misguided and misinformed employees, that don't know the implications of **not following policy.**
Deliberate malicious insider threats also can be attack sources. These threats are typically
motivated by *financial gain, sabotage, and theft to gain competitive advantage.*

##### Nation states
- Government
- Highest sophistication
- Constant attack massive resources

##### Hacktivists

These are normally ahckers with a purpose , social change or political agenda.
These groups or people can be remarkably sophisticated, as seen in the past with DDoS attacks and public site defacing. Their funding is normally limited.

##### Script kiddies

Runs pre-made scripts without any knowledge of whats really going on. this can be internal or external but it is not very sophisticated but still can be critical. Motivated by the hunt or stroking their own ego.

##### Organized crime

These are the professional criminals , they are motivated by money and very sophisticated and organized which makes them harder to pin down. They normally have access to a wide range of funds and influencers.

##### Hackers 

- Experts with technology ofter driven by money power ego 
1.  **Authorized hackers** (White Hat) are hackers that do it with permission or blue team.
2. **Unauthorized hackers** (Black Hat) are malicious and violates security and policy for monetary gain
3. **Semi-authorized hackers** (Gray Hat)Find a vulnerabilty but dont use , people like those who are looking for bugs with apple as an example.

##### Shadow IT

Shadow IT is **the use of IT-related hardware or software by a department or individual without the knowledge of the IT or security group within the organization**. 
People that think they know better than IT; its like that guy from QCD that thought he was IT.
Need to put up roadblocks for these kinds of people.

##### Competitors

They have many different motivations, 
DoS , espionage, harm reputation.

High level of sophistication
- High fundng
- Huge competittve upside

Many different intents
- Shut down your comptitor during an event
- steal customer lists
- Corrupt manufacturing databases
- Take financial information











#### Vectors 

The path threat actors use to carry out and attack are called attack vectors, understanding them is important to proper risk analysis that may be required for defense.
IT professionals spend their career watching these vectors or **attack surface**.

##### Types

###### Direct access attack vectors
- Physical access to a system is a sinificant attack vector
- Modify the operating system or reseting the administrator password.
- Attach a keylogger . Hot-pluggable usb to collect usernames and passwords.
- Transfer files and take it with you
- Denial or service or just pulling the plug on yoru system

###### Wireless attack vectors
- Default login credentails 
- Rouge access point
- Evil twin: MITM, collects auth details
- Protocol vulnearbilities . use the best security and update regularly

###### Email attack vector
- Biggest , most successful
- Phishing attacks 
- Malware straight to the user
- Social engineering attacks : Nigerian Prince

###### Supply chain (Third-party) attack vectors
- Tamper with the underlying infrastructure 
- gain access to a network using a vendor
- Can be anything you use even something as simple as a air conditioner
- Malware can modify the manufacturing process
- Counterfeit networking equipment : backdoors , bad performance.

###### Social media attack vector
- User profiling : where you were born
- so much information online

###### Removable media attack vectors
- Get around the firewall : Usb connection for gathering information
- Infect air-gapped networksm industrial systems, high-security service.
- Can act as a keyboard
- Data exfiltration : terabyes of data walk out the door

###### Cloud-based attack vectors

- Publicly-facing applications and services
- Security misconfigurations
- Brute force attacks
- Orchestration attack : Increasing the load make the cloud build new application instances
- Denial of service



#### Threat Intellegence Sources

Organizations today increasingly rely on threat intelligence data. This valuable data can be fed into systems and models to help organizations understand their overall risk.


##### Open-source intelligence (OSINT)

- Open-source
- Publicly available sources
- Internet , discussion groups, social media
- Government data , Hearings ,reports , warrents, websites, arrests, etc.
- Commercial data , Map , finacial reports, databases.


##### Closed/proprietary intelligence
- someone else has already compiled
- Threat intel services, analytics, correlation across different data sources
- Constant threat monitoring , identify new threats '


##### Vulnerability databases

Researchers find vulnerabilities and post them to the public so everyone knows about them.
- [Common vulnerabilities and Exposeures (CVE)]((https://cve.mitre.org/))
- [US national vulnerability database (NVD)*](https://nvd.nist.gov/vuln/search)
- [Exploit database ](https://www.exploit-db.com/)


##### Public/private information-sharing centers
- Public threat intelligence 
- Private threat intelligence
- Need to share critical security detail
- Cyber threat Alliance (CTA)

##### Automated indicator sharing (AIS)

- Intelligence industry needs a standard way to share important threat data freely.
- Structured Threat Information eXpression (STIX) : Describes cybe threat information
		- motivations , abilites , vapabnities and response information
- Trusted Automated eXchange of Indivator Information (TAXII)
		- Securely shares STIX data


##### Dark web intelligence 

- Dark web is a overlay network that uses the internet but requires specific software (TOR) and configurations to access
- Hacking groups use the Dark web for their activities, to get new tools and techniques , sell credit cards , accounts and passwords and any other stolen information that would be otherwise hard to sell


##### Indicators of compromise (IOC) 

An event that indicates an intrusion.

- Indicators 
	- Unusal amount of network activity
	- Change to file hash values
	- Irregular internation trafic
	- changes to dns data
	- Uncommon login patters
	- Spikes of read requests to certain files

##### Predictive analysis

- Analyze large amounts of data very quickly
	- Find suspicious patters
- Identify behaviors
	- DNS queires , traffic patters, location data
- Creats a foreecast for potential attack
- Often combined with machine learning

##### Threat map

- identify attacks and trends from a worldwide perspective


##### File/code repositories

- See what the hackers are building
- See what poeple are accidentally releasing
- attackers are always looking for this code , source code.

#### Threat Research

As a Security professional you have to know your enemy and the enemy is always changing so research is a never-ending process; the field is constantly moving and changing.

##### Sources

###### Vendor Websites

The people who wrote the software
They know when problems are announced, and are involved in the disclosure process.
They react when surprises happen.

###### Vulnerability feeds 
- Automated culnerability notifications
- Third-part feedss
- Roll-up to a vulnerability managment system

###### Conferences

- Watch and learn
- Researchers
- Stories from the trenches
- Building relationships


###### Academic journals

- Reasearch from academic professionals
- Evaluations of existing security tech
- Detailed post mortem : tear apart the latest malware
- Extremely detailed information

###### Request for comments (RFC)

- Published by the Internet Society (ISOC)
-  Not all RFCs are standards documents
- Many information RFC analyze threats

###### Local industry groups

- A gathering of local peers
- associations
- Industry user group
- Get info from others

###### Social media

- Hacking group conversation
- Honey monitoring on Twitter
- Keyword monitoring
- analysis of vulnerabilities
- command and control

##### Threat feeds
- Monitor threat announcements
- Many sources of info 

###### TTP
Tactics, techiques, and procedures






## 1.6 Explain the security concerns associated with various **types of vulnerabilities.**

#### Vulnerabitlity types

##### Zero-day attacks

If the attackers do use this vulnerability against you and this vulnerability has never been seen up to this point, then we have a zero-day attack.
A zero-day attack means that we’ve never seen this vulnerability before. It’s brand new. And because of that, there’s probably not a patch or a way to prevent this vulnerability from being exploited.


##### Open Permissions

Where information has been put onto the internet but **no security** has been applied to that data. And it makes it **very easy** for anyone on the internet to access that information.

We’re putting an increasing amount of data on the cloud. And because this data is now located somewhere that can be accessed from anywhere in the world, it’s becoming increasingly common to see misconfigurations that would allow access to this data.

Attackers spend a lot of time on these cloud repositories, trying to find sections of data that may have been left open. So make sure that if you’re storing data in the cloud that you’re putting the proper security in place.

##### Unsecured Root accounts

 we also sometimes leave our accounts open. And if this account is an administrator account or root account, then an attacker may have full control over an operating system.
On many systems, the administrator has chosen not to allow interactive access to log into the administrator account. This means no matter how hard the attacker tries to find the correct username and password combinations, they’ll never gain access to the operating system by logging in with the administrator or the root account.
Administrative account should be closely monitored. And we should always have policies and procedures in place to prevent casual use of these accounts.

##### Error

Occasionally, we can **give too much information** in that error message and that information could be used against us. For example, the error message may show the service that’s being used or the application that we’re using. 
It might show **version information** associated with that application. 
And the message may display debug information that could be memory values or information that’s not commonly seen from the outside.

##### Weak Encryption

just because we’re encrypting data doesn’t necessarily mean that it’s well protected.
That’s why you need to be sure that you’re using encryption protocols that are strong protocols. Encryption protocols, such as AES and triple DES, are very common to see used. And of course, you want to be sure that the length of the encryption key is long enough to provide the proper amount of security.

And if you’re communicating over a wireless network, make sure you’re using the latest wireless encryption protocols.
It’s always good to stay up to date with what the industry believes are the best ciphers to use on your network.
it’s important that you configure your web servers and your clients to make sure that they are using the strongest TLS protocols.

There are many documents for best practices on the internet that will help you know exactly which of these cipher suites is the best to use

128 bits or smaller, which tend to be very easy to brute force.
not using any outdated hashes, like MD5, where known vulnerabilities may exist.


##### Insecure protocols

Protocols, such as Telnet, FTP, SMTP, and IMAP, are good examples of these in the clear protocols

In many cases, you can reconfigure the application to use an encrypted protocol instead of the in the clear protocol. So you might want to change the application to use SSH, SFTP, or IMAPS.

##### Default settings

The attackers know that many people will plug these in and never change that username and password. And they found ways to use this to their advantage.
One such use is the Mirai botnet. It takes advantage of these default usernames and passwords to gain access to these systems and take them over for their own use.
 the Mirai botnet is now open source. So attackers can download the software, modify it for their own purposes, and control even more IoT devices.

##### Open Ports and services
Unfortunately, opening these ports also creates an opening into the server. And we have to make sure that we’re properly adding the security that we need to let the good people in and keep the bad guys out.
We’ll have software based firewalls running on the server and we’ll have network based firewalls on the ingress and egress parts of the network.
The firewall will commonly have a rule set that will allow or disallow access to certain ports on the IP address and thereby keep out anyone who may be trying to attack that device.

It may become very easy to accidentally allow access to a service that was not intended. In fact, it’s very common for someone who is managing one of these firewalls to occasionally audit the rule base, make sure that all of the rules are up to date, and that no mistakes have been made with IP addresses, port numbers, or any of the other services that are configured in that rule base.

##### Improper patch management

We know that these vulnerabilities exist in our software and, of course, many organizations will occasionally release updates to the software that didn’t need to be deployed on all of our systems. 
Many organizations will have processes in place to be able to keep all of their systems up to date with the latest patches.
This is a priority for many organizations because most of these patches are associated with security vulnerabilities.

There’s usually a **group of people that will test these patches,** make sure that they will **operate properly in your environment,** and then **load them on a central server**, which will then deploy to all of the other systems in your organization

##### Legacy Platforms

We refer to these older systems as legacy systems. These legacy devices may be running older operating systems, old applications. There may be middleware that’s installed, but these are systems that we can’t easily turn off or convert because perhaps they’re performing a particular function that can’t be duplicated or no one is really put in the effort to upgrade it to the latest version.
- security concern
-  you may keep some of this legacy equipment around, but you may be adding additional firewalls or other security tools around that system to make sure that you can keep it as secure as possible.


#### Third Party Risks

Because these third parties exist does not mean that we can have less security. We need just as much security because these third parties are on our network.

You should always plan for the worst possible scenario and make sure that your security policies and procedures are expecting those types of problems

Could be non malicious and just a human made problem.

##### System interfration risk
the system integrators have additional access to the systems because they need that access to be able to do their jobs.
And because these integrators are on the inside of the network, they’re past the firewalls and the security devices that we commonly put on the perimeter.
 it’s much easier to put malware into an existing network, because you’ve now gone past all of those security filters.
 in some cases, running software that you thought was safe may inadvertently install malware on systems. And now that those integrators are on the inside


##### Lack of vendor support

We have to make sure that the vendors know a problem exists and that they can fix the problem in a timely manner.
This isn’t always the case. You have to, of course, make sure that the vendor is aware of the problem, and then the vendor themselves has to be motivated enough to make sure that they can keep those systems up to date and safe.

##### Supply chain risk

 it’s always important to maintain your security controls, whether these are devices that you have in-house or things that you bring in from a third party.
 lthough you trusted the software coming from this third party, it, in fact, was able to infect your systems once you installed the trusted software.
 you also have to check the hardware that you’re getting from a third party.
 Organizations need to have processes and procedures in place so that they’re able to monitor all of this coming through the supply chain and be able to react to any type of security concern.

##### Outsourced code development

Not every organization has the resources available to do their own in-house development.

 you need to make sure that you’re building a secure environment for the developers to work in and for you to be able to evaluate the code that’s being created.

a good best practice to make sure that wherever that data is stored and where the developers may be working is isolated and secure from the rest of the network.

The production services should be on a separate, isolated part of the network, and the development team should not have access to the production site of the network.

 it needs to be checked to make sure there’s no other ways to gain access into that application. 
  be sure that the data that’s being used by that application is being stored in a secure way and is being transmitted across the network in encrypted form.

##### DAta storage
With cloud-based services, we are storing a lot of information in a separate, third-party location.
 This data may contain customer information. There may be healthcare data or financial details. And we need to make sure that we’re applying the proper security around the type of data that we’re storing.
  if we are storing that data at a third-party location, we need to be sure that the transfer of data in and out of that facility is all done over an encrypted channel.


#### Vulnerability impacts

##### Data Loss
 In some cases losing the data may be more damaging than losing money.

 A database that has no password or is using default passwords can be at risk for losing the data within that database.
 
It’s very important to always have a backup.

Some attackers don’t delete the data, but instead prefer to steal the data and then use that data for their own purposes.

##### Identity theft

Usually the cost of losing customers precious data.
Catastrophic when this occurs.

##### Financial loss
These vulnerabilities can cause financial loss as well. This particular example is in March of 2016 at the Bank of Bangladesh, and this is around a vulnerability that took advantage of the Society for Worldwide Interbank Financial Telecommunications, or what the industry refers to as SWIFT. Attackers sent messages over the SWIFT network to **transfer nearly $1 billion from accounts** at the Bank of Bangladesh to accounts that are in the Philippines and Sri Lanka.

##### Reputation impacts (Value)

Getting hacked isnt a great look , Organizations are required to disclose breaches


##### Availability loss

Outages and downtime

For example, in September of 2021 of Chile’s largest banks Banco Estado was attacked with ransomware that took out all of their internal systems. The bank was effectively out of business internally, and were not able to process anything on their internal network.

















## 1.7 Summarize the techniques used in security assessments.

#### Threat hunting
The attackers are constantly trying to find a way into your network to gain access to your data.
The strategies that we use to protect against attacks today will be very different than the strategies that we need to follow tomorrow.

One of the problems we have in reacting to these attacks, of course, is that we can’t react until the attack occurs

The goal then is to speed up this reaction time or perhaps prevent the attack from occurring before the attacker even arrives on your network.

##### Intelligence fusion
there is a huge amount of data we have to sift through to even be able to understand if an attack is occurring

Different data types

 You have security operations, security intelligence, threat response teams, operations teams, security operations centers, and more people that are looking at data that can help identify these threats.
 take all of this data, put it into a massive database, use big data analytics. That’s going to allow us to correlate, identify, and pick out individual important pieces of data that can give us some insight into when attacks may be occurring

###### Fusing the data 

- Collect the data : logs sensores network information internet events, intrusion detection
-  add external sources : threat feeds , governkental alerts 
- COrrelate with big data analytics: understand where potentioal problems are coming from.


##### Cybersecurity maneuvers

We can deploy additional firewalls, intrusion prevention, and scanning systems to understand what’s happening on the network right now. "Manuevers"

Unlike a military that takes time to deploy, these systems are virtualized. We can deploy them instantly.

And since all of this is automated, it can identify those threats coming from many different places simultaneously, even if those threats are very different in scope.


#### Vulnerability scans
These scans are designed to look at systems to see if potential vulnerabilities might exist in an operating system, a network device, or an application.
the vulnerability scan is trying to determine from the outside if there is the potential to gain access to those systems.

- Port scan: That’s when we will look at a device and determine what ports happen to be responding on that particular IP address.  From here you may be able to gather information about things that might be less than secure
- Identify systems:  This would be servers, workstations, laptops, and other devices that are connected to the network as well. You want to be able to perform these vulnerability scans from the perspective of the attacker. Also as an insider.
- Gather as much information as possible.

##### Scan types

The vulnerability scanners use are very powerful pieces of software that are designed to look at many different aspects of how your systems are running in the hopes that it will find some vulnerabilities on that device.

- We call these **non intrusive scans**, but of course, there’s a little bit of intrusiveness as it’s scanning the different port numbers and perhaps trying to find out if a potential vulnerability might exist.
- These vulnerability scanners will not try to attempt to take advantage of the vulnerability. Instead they’ll simply decide if a vulnerability might exist or not.
- ***Intrusive scans*** : You can run a penetration test on its own or you can find a specific exploit that might attack that vulnerability and see if that vulnerability does exist.
- **Non-credentialed scans**: The scanner cant login to the remote device
- **Credentialed scan**: Youre a normal user , emulates an insider attack.


##### Identify Vulnerabilities

The scanner looks for everything , well the signatures  that it already knows.
1. Application scans
2. web aplication scans
3. Network scans

Vulnerability Reasearch

- Online cross reference
- Nationa vulnerabilty database
- common vulnerabilittes exposers
- Microsoft security bulletines
- Some cannot be verified

 National Vulnerability Database at nvd.nist.gov.

Common Vulnerability Scoring System. This provides a number associated with the vulnerability that can give you a perspective of just how severe this vulnerability might be. Each vulnerability gets a score between 0 and 10 and this allows you to at least have some measure that you can use to determine which vulnerabilities may be more severe than others.


##### Vulnerability scan log review 

- Lack of security controls
			- no firewall
			- no anti virus
			- no anit spyware

- Misconfiguration
	- Open shares
	- Guest acces
- Real Vulnerabilities 
	- especially the newer ones Occasionally the old ones.

##### False positives
A vulnerabiltiy that doesnt really exist

- This is different than a low-severity vulneratbility

##### False negative
A vulnerability esists but you didnt detect it
Update to the latest signatures

#### Syslog/Security information and event management (SIEM)

 A SIEM is designed to collect information from anything on the network that can create log files, security alerts, or any type of real time information that can tell us about what’s happening on the network right now.

  The SIEM is commonly used as a central repository. So everything will be logged and aggregated into the central database of the SIEM. From there, you can create reports and historical perspectives of what’s been happening on the network over time.
   
  Data correlation: able to correlate data from different devices to see if you can start to see events occurring even though the data sources that you’re receiving are very different between these different devices.

 it’s a perfect place to go to be able to perform forensics after a security event has occurred.

##### Syslog
The data that’s being fed into the SIEM is coming from very different devices.
there needs to be a standard way to be able to send log files from other devices into this central repository. And the name of that standard is called syslog.
This collector is waiting for messages to be sent from all of those different diverse devices on the network.

As you could have probably already guessed, being able to store all of this data from all of these devices over a long period of time is going to require a lot of storage space. So it’s very common on a SIEM to allocate terabytes and terabytes of storage so that you can collect a lot of this information and store it for a long period of time.


##### SIEM data

Inputs
- Server authentication attemps
- vpn connections
- firewall sesson logs
- denied outbound traffic flows
- network utilizations

Packet captures
- Network packets
- Often associated with a critial alert 

##### Security monitoring

- Constant information flow
- Track important statistics; exceptions can be identified.
- Send alerts when problems are found 
- Create triggers to automate responses

##### Security reports

Gathers information for the logs then creates a more human readable form of that dat


##### Analyzing the data

- Big data analytics 
- User and entity behavior analytics (UEBA)
- Sentiment analyis' Public discourse correlates to real-world behavior
- If they hate you they hack you. 


##### SOAR
Security orchestration automation and response
- automate the routine , tendious and time intensive acivites

Orchestration
- connect many different tools together ; firewalls, account management email filters etc

Automation
Hand security tasks automatically


Response 
Makes changes independantly.

