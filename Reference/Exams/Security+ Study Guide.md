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

An **integer overflow** is another type of overflow that is specific to whole numbers, known as integers.
Putting too much information into too small of a space that has been set aside for numbers.
**Usually causes the error to be unexpected.**


For example, 12 is an integer, but 12.1 is not. When programs do not carefully account for integer overflows, undesirable behaviors and
consequences can result.



#### Replay Attack

A **replay attack** is when a third party intercepts and “replays” a secure data transmission, allowing the third party to *interact with the receiver* as though they were the original sender. It’s a relatively common and surprisingly simple form of cyberattack.
Hackers can eavesdrop on data exchanges being sent through networks—this type of eavesdropping is known as **packet sniffing**. Once data is intercepted it is replayed in the same form—usually a session ID, an email, or a message. Replay attacks are often used to steal *usernames and passwords*, or trick users into sending funds to the hacker.

> [!note] Solutions
> - **To prevent this, passwords are often “[hashed and salted](https://www.expressvpn.com/blog/internet-security-technical-glossary/).”**
> - Encryption : Use a session ID with the password hash to create a unique authentication hash each time.
> - Data/Time stamps


#### Session replay

- an attacker steals a valid session ID of a user and reuses it to impersonate an authorized user and perform fraudulent transactions or activities
- disallow session ID  reuse in web apps

##### Cookies and Session IDs

- Cookies are information stored on your computer by the browser, they are used for tracking, personalization, session management and security.
- Could be considered a privacy risk because of all the personal data those cookies contain about you.
- *Session IDs* are typically stored in the cookie in order to maintain sessions across multiple browser sessions.
- ***Pass the hash—A type of replay attack in which the attacker provides the hashed password to an accepting authentication scheme.
- a technique whereby and attacker captures a password hash and then passes it through for *authentication and lateral access*
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

**Drivers** are the integration between the hardware of your computer and your OS, which makes them a perfect medium for attack.

- Shimming :
- Involves creating a library (or modifying and existing one) to bypass a driver and perform a function other than the one for which the API was created
- Filling the space between two objects. A middleman.
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
- a timing vulnerability that occurs when a program check access permissions *too far in advance of a resource request*
 it is an asynchronous attack that exploits timing. TOCTOU takes advantage of
the time delay between the checking of something and the usage of something.

EXAMPLE: A simple example of a race condition is a light switch. In some homes, there are multiple light switches connected to a common ceiling light. When these types of [circuits](https://www.techtarget.com/whatis/definition/circuit) are used, the switch position becomes irrelevant. If the light is on, moving either switch from its current position turns the light off. Similarly, if the light is off, then moving either switch from its current position turns the light on.


##### Memory vulnerabilities

Memory leak: Unused memory not properly released, so it begins to slowly grow in size it eventually uses all available memory and the system crashes.
- Solutions: A *static code analyzer* can check to see if all memory allocation commands have a matching deallocation command.
 - **NULL pointer**/object deference 
	 - Dereferencing means taking away the reference and giving you what it was actually referring to.
	 - Technique that references a empty portion of memory, application crashes, debug information displayed also a denial of service. 
	 - Prevented by good code practices

##### Directory Traversal / Path traversal 
Read files from a web server that are outside the website file directory.

Web server software vulnerability and web app code vulnerability.

Able to view files you aren't supposed to read.

May allow the attack to get to the site's root directory.

- Solutions: Run a scanner and keep the web sever software patched.


##### Improper error handling
- Make sure that your error messages aren't showing too much information such as network info memory dump stack traces database dumps, etc.
- easy to fix and find
- Related to input validation
- If a program crashes that's a sign of bad error handling

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

An *unauthorized wireless access point*, may be added by an employee doesn't necessarily have to be an attack, but it is still a problem to your network. It's becoming very easy to plug in a wireless AP or enable wireless sharing on your phone or OS. It's always a good idea to schedule a periodic survey and be aware of your surroundings.

NAC (Network Access Control) 802.1X is a good deterrent. 
A NAC system can deny network access to noncompliant devices, place them in a quarantined area, or give them only restricted access to computing resources, thus keeping insecure nodes from infecting the network.


##### Evil Twins

An evil twin attack is **a spoofing cyberattack that works by tricking users into connecting to a fake Wi-Fi access point that mimics a legitimate network**. 

The most dangerous evil twin attacks work by tricking victims into thinking that they are connecting to a reliable public Wi-Fi network. To make the attack as believable as possible, hackers will choose a location with free Wi-Fi and set up an AP, then name it something that a victim thinks is the right Wi-Fi.


#### Bluejacking and Bluesnarfing

##### Bluejacking
Sending of unsolicited messages to another device, via Bluetooth. The typical functional distance of Bluetooth is about 10 meters, depending on antenna and interference.
However, Bluejacking **does not involve device hijacking**, despite what the name implies. The bluejacker may send only *unsolicited messages.* Hijacking does not actually occur because the attacker never has control of the victim’s device. At worst, bluejacking is an annoyance.

**Bluesnarfing and bluebugging,** however, are actual attacks that may result in a user losing control of his device. Bluesnarfing (data theft), Bluebugging(eavesdropping or hacking backdoor attack). To prevent use long pin 2fa and disable discovery mode.

#### Wireless Disassociation Attacks 

A type of DoS attack in which the attacker *breaks the wireless connection* between the victim device and the access point.
The method is based on the use of a *special disassociation frame* specified under IEEE 802.11. 
Transferring such a frame to the target device breaks the connection, and the Wi-Fi protocol does not require any encryption for it. For a successful attack, the cybercriminal needs to know only the victim’s MAC address or Wi-Fi address.
**It gives the attacker a window to inject an evil twin.**


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

Built on RFID often used with payment systems Subject to many of the same vulnerabilities as RFID.
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

DNS spoofing: attacker sends false replies to a requesting system, beating the real reply from the valid DNS server.

Usually done by either modifing the client host file or sending a fake response to a DNS request (MITM/On-Path)

> [!note] Solutions
> allow only authorized changes to DNS 
> restrict zone transfers, verified fowarders and
> log all privileged DNS activity

##### Domain hijacking

The attacker gets access to the domain registration has control on where the traffic flows.
Done by social engineering, or brute forcing.

##### URL hijacking (Hyperlink Spoofing)
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

> [!note] Solutions
> Firewalls,Routers, IDS
> SIEM
> Disable broadcast packets entering/leaving
> disable echo replies patching

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

















## 1.7 Summarize the techniques used in **security assessments.**

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


## 1.8 Explain the techniques used in **penetration testing**.

#### Types of Penetration Tests

##### Known environment *white box test*
- penetration tester is given a map or target systems and networks, They go into the test with *subnstatial/full information* of the target systems and networks.

##### Unknown environment (black box test)
- penetration tester knows nothing about target systems and networks. They go into the test completely blind and buil out the database of everything they find as they go

##### Partially known environment (grey box test) 
- limited information is shared with the tester, sometimes in the form of login creadentials. Simulates the level of knowledge that a hacker with long-term access to a system would achieve through research and system footprinting

##### Rules of Engagement
- Define the purpose of the test and what the scope will be for the people who are performing this test on the network.
- They ensure everyone will be aware of what systems will be considered, date and time and any constraints all should be aware of.

#### Concepts

##### Lateral Movement
Gaining access to an inital system, then moving to other devices on the inside of the network

##### Privilege escaltion 
A securtiy hole created whne code is executed with higher privileges than those of the user running it

##### Persistence
In the context of penetration testing refers to the testers ability tp achieve a persistent presense in the exploited system - long enough for a bad actor to gain in-depth access.



##### Cleanup
The final stage of a penetration tes in which all work done during the testing process is cleaned up/removed.

##### Bug bounty
A monetary reward given to ethical hackers for successfully discovedring and reporting a vulnerability or bug to the applications developer.

##### Pivioting
Also known as island hopping, is *when a compromised system is used to attack another system on the same network* following the inital exploitiation if the compromise in introduced at a different time than the attack then it is said to involve persistance


#### Passive and Active Reconnaissance


##### Passive Reconnaissance 
One is not interacting directly with the taget and as such, the target has no way of knowing, recording, or logging activity.

- War driving: gathering wireless network information while driving around the streets.
- Drones: Can be leveraged in multiple wats for passive recon from assessing phyical security to gathering wireless network info
- War flying: combines war driving with a drone and simply float above all of these organizations to gather wireless details.
- OSINT : Much of this info in the open source can be categorized as open-source intelligence or OSINT.

##### Active reconnaissance 
Interacts directly with the target in some way and as such, the target may discover , record, or log these activities.

- Footprinting: An ethical hacking technique uesed to gather as much data as possible abot a specific targeted computer system , infrastructure and networks to identify opportunities to penetrate them.
- Active: Ping sweep ,Tracert , Nmap , Extracting DNS information
- Passive: Browsing taget website, google seach(dorking) . Whois lookiup

##### Exercise types

###### Red team : offense
###### Blue Team : defense
###### Purple Team : Process improvement
###### White team: Referees




# 2.0 Architecture and Design
## 2.1 Explain the importance of security concepts in an enterprise environment.

#### Configuration Management 
- Ensures that systems are configured similarly, configurations are **known and documented.**
 - **Baselining:** ensures that systems are deployed with a common baseline or starting point, and imaging is a common base lining method.

##### Diagrams
- *Network diagrams* : Document the physical wire and device, detailed diagrams to show the relationship of all the interconnected devices. Full topology.
	- Physical data center layout: Can include physical rack locations.
	- Device diagrams: individual cabling.

##### Baseline configuration
- The security of an application environment should be well-defined. 
- Firewall rules: can be used to block traffic, and we can use either an MDM solution or group policy to change the configuration on endpoint devices.
- It is vital that each type of device being placed on the network has a secure baseline configuration.
- Integrity measurements check for the secure baseline, these should be performed often and will check against well-documented baselines.

##### Standard naming conventions

- Makes identifying device type (router, server, printer) easier.
- Needs to be easily understood by everyone.
- Devices should have asset tag names and numbers, serial numbers and pc names—location or region. 
- Network racks and plates should identify what port the device is going to 
- Domain configurations. Should have identifiable user account names and standard email addresses.


##### IP Schema

- An IP address plan or model for consistent addressing for network devices.
- Use *network segmentation* to reduce broadcast traffic and enable filtering/restricting traffic to subnets containing sensitive resources.
- Number of subnets, and hosts per.
- IP ranges of all the different subnets within the company and reserved addresses for certain important network devices (switch, router, gateways)

##### Asset Management

- Maintain an up-to-date asset register to ease the process of tracking and maintaining assets.
- Scan for unknown devices that may be threats, and ensure each asset is patched,


### Protecting data 

#### Data sovereignty 

A primary task of cybersecurity experts is to protect data, and an organization is out of business without data. And it is everywhere, on a storage drive, on the network, in a CPU.

This task is normally accomplished by encryption, security policies and data permissions.

**Data sovereignty:** 
Digital data is subject to the laws and regulations of the country in which it was created.
It cannot be moved to another region-even for a backup-related reason.
Data is subject to the laws of where it is stored, which can bring significant legal implications.

For example, the EU and the **GDPR** (General Data Protection Regulation).

##### Data Masking

- It is when only partial data is left in a data field. 
- Example: *\**\* *\*\**\ 1234

- Used to protect PII and any other sensitive data.


#### Data Encryption
Encode information into unreadable data, original information is plaintext, encrypted form is ciphertext.
The encrypted data is drastically different from the plaintext.

##### Diffusion 

Change one character of the input, and many characters change of the output.


##### Data at-rest 

- The data is on a storage device 
- Encrypt the data 
- Apply permissions

##### Data in-transit

- Data transmitted over the network 
- Not much protection as it travels
- Network based protection
- Provide transport encryption : TLS, IPsec

##### Data in-use

- Data is actively processing in memory 
- The data is almost always decrypted
- The attackers can pick the decrypted information out of RAM


##### Tokenization

Replace sensitive data with a non-sensitive placeholder
- Common with credit card processing, uses a temporary token during payment
- no encryption stateless stronger than encryption.
- Stored in a remote vault.

##### Information rights management 
- Control how data is used
- Restrict data access to unauth persons
- Each person has own rights


### Data Loss Prevention

Stop the data before the attackers get it
Endpoint DLP is on your computer
on your network 
on your server

USB blocking on a workstation : allow or deny certain tasks


##### Cloud based DLP 

Located between users and the internet
Block custom defined data strings
Manage access to URLs
block viruses and malware

**DLP and Email**

Email continues to be the most critical risk vector 

Check every email, inbound and outbound

**Inbound**
Block keywords identify impostors

**Outbound**
Fake wire transfers w-2 info employee information


#### Geographical considerations

- Legal implications
- Business regulations vary between states
- for a recovery site outside the country personnel must have a passport and be able to clear immigration
- refer to your legal team

- Offsite backup
- - Organization-owned site or 3rd-party secure facility
- Offsite recovery
- Hosted in a different location, outside the scope of the disaster
- Travel consideration for the support staff

#### Response and recovery controls

- Incident responses and recovery has become common place
- Incident response plan should be established Documentation is critical
- Limit the impact of an attacker: Limit data exfiltration
- Limit access to sensitive data.


#### SLS/TLS INSPECTION

- Commonly used to examine outgoing SSL/TLS 
- Examine encrypted traffic
- SSL/TLS relies on trust, without trust none of this works.
- Your browser contains a list of trusted CA's
- CA = Certificate authority
- Your browser doesn't trust a website unless a CA has signed the web server's encryption cert 
- The CA has ostensibly performed some checks, validated against the DNS record, phone call, etc.

SSL/TLS proxy

<img src="https://i.gyazo.com/57fb1d26b78228fb394cb921ff208237.png">



Decrypting it from the outside and encrypting it internally with the internal CA

#### Hashing

- Represent data as a short string of text.
- One-way trip: its impossible to recover the original message from the digest
- Verify a downloaded document is the same as the original
- Can be a digital signature for authentication, non-repudiation and integrity
- Different messages will not have the same hash (collsion)

#### API considerations
- Application programming interfaces - controls software or hard ware programmatically 
- Secure and harden the login page.
- On-path attacks can intercept and modify api messages, replay API commands.
- API INJECTIONs
- DDoS - One bad api can bring down a system.

**API Security** 

Authentication : Limit API access to legitimate users
Authorization: API should not allow extended access, each user should only have the permissions they need.
WAF (Web Application Firewall) : How you apply rules to API  commuincation.

### SIte resiliency

- Recovery site is prepped, data is synced
- A dister is called , business processes failover to the alternate processing site 
- Can take hours, weeks, or longer to resolve issue.

#### Hot site
- An exact replica
- Stocked with hardware, constantly updated, you buy two of everything
- Applications and software are constantly updated
- Flip a switch that moves everything to the hot site

#### Cold site
- No hardware 
- No data 
- No people 

#### Warm site
- Somewhere in the middle between cold and hot 
- Big room with rack space , just need the hardware
- Hardware is ready and waiting , you bring the software and data.


### Honeypots and deception


#### Honeypots

- Attracts the bad guys for recon on how they are trying to break into your system
- Create a virtual world to explore
- Many different options of this
- ITs a constaant battle to dicern the real from the fake.

#### Honeynet
= More than one honeypot on a network
- More than one source of information
- Projecthoneypot.org

#### Honeyfiles
- Bair for the honeynet
- An alert is sent if the file is accessed
- A virtual bear trap

#### Fake telemetry

- Machine learning, interprets big data to identify the invisible
- Tain the machine with actual data , learn how malware looks and acts, stop malware based on actions and not signatures
- Send the machine learning model fake telemetry


#### DNS sinkhole

- A DNS  that hands out incorrect IP addresses.
- Ab attacjer cab redirect users to a malicious site
- Can watch for any users hitting that IP address 
- can be integrated with a firewall , ifentify infected devices not directly connected


## 2.2 Summarize authentication and authorization design concepts.

### Cloud Models

#### Infrastructure (Hardware) as a Service
- Outsource your equpment
- Responsible for the management and security, And your data is within your control (can be encrypted from the provider)
- Web server 

#### Software as a service
- On-demand software
- Log into the system and begin to use
- no logs, updates, or mainteinance
- Central management of data and applications
- Less control of your data 
- i,e google mail

#### Platform as a service 

- No servers, no software, no maintenance team
- Someone else handles the platform, you handle the development
- You dont have direct control of the data people or infrastructure
- Put the buiding blocks together 
- Salesforce.com , Wix.com

#### Anything as a Service

- Service delivered over the internet
- Flixbible consumption model , no large upfront costs or ongoing licensing
- It becomes more of an operating model

<img src = "https://i.gyazo.com/1ee1c112042bae699f852e80925751f2.png"> 



#### Managed service providers

- Handle many ascpets of tech for their clients
- MSP support 
- Connectivity managemen
- Backups and disaster recovery
- Growth management and planning


#### On-premises vs off-premises

On-Premises 
- Your applications are local 
- your servers are in your data center in your building

Off-premises
- Your servers are not in your building 
- They may not even be running on your hardware


#### Cloud deployment models

Public
- Available to everyone over the internet

Community
- Several organizations share the same resources

Private 
- Your own virtualized local data center

Hybrid
- A mix of public and private




##### Cloud Computing Pros and Cons

Pros
- Computing on-demand
- Fast implementation

Cons
- Latency - the cloud is far away
- Limited bandwitdh
- Difficult to protect data
- Requires internet/network connectivity


#### Edge computing

- Over 30 billion IoT devices on the Internet 
- Process application data on an edge server, close to the user.
- Often process data on the device itself
	- low latency not network requirment
	- Increase speed and performance
	- Process where the data is, instad of processs in the cloud.
	- i.e a thermostate controlling the temperature

#### Fog computing

- Fog: A cloud thats close to your data 
- Fog computing - a distributed cloud architecture , extends the cloud
- DIstribute the data and processing
	- Immediate data stays local no latency
	- Local decisions made from local data - No bandwidth requirements
	- Private data never leaves - minimizes security concerns 
	- Long-term analysis can occur in the cloud - Internet aonly when required
	- Think of fog as the "middleman" before the internet/cloud

<img src= "https://i.gyazo.com/257732ba5fd101a6510b45f49c5de694.png">



#### Designing the cloud

- Elasticity : Scale up or down as needed
- Applications also scale if needed and accessible from anywhere

##### Thin client

Basic application usage for applications so they run on a remote server
- VDI (Virtual Desktop Infrastructure)
- Local devices is a keyboard, mouse , and screen

Minimal operating sustem on the client

Network connectivity


##### Virtualization 
Run many different operating systems on the same hardware 
- I.e Proxmox

Each application instance has its own operating system


##### Containerization
- Container : Contains everything you need to run an application
- Code and dependencies

- AN isolated process in a sandbows

- Specified container image

![[Pasted image 20220828192951.png]]



##### Microservices and API's

- Monolithic applications: One big application that does everything
- APplication contains all decision making processes
	- User interface
	- Business logic 
	- Data input and output
- Code challenges
	- Large codebase
	- Change control challenges
<img src = "https://i.gyazo.com/8fe752c103a31d242e86a2c1a1b91467.png">


APIs

API is the "glue" for the microservices
![[Pasted image 20220828193334.png]]



#### Serverless architecture

Function as a service (FaaS)
- Applications are separated into individual, autonomous functions
- Remove the operating system from the equation
- Like what Rob does on docker with all his containers

Dev still created the server-side logic: Runs in a statless compute container
	-May be event triggered and ephemeral

#### Transit gateway

- VPC - Virtual private cloud
	- A pool of resources created in a public cloud
- COmmon to create many VPCs
	- Many different application clouds
- Think of like a "Router" But in the cloud
- Connect VPCs with a transit gateway

![[Pasted image 20220828194009.png]]


#### Service intergration and management

(SIAM)
- Many different service providers (multisourcing)
	- Up and running regardless of provider going down
- SIAM allows you to bring all those service providers into one view and service all of them


### Infrastructure as code

- Decribe an infrastructure
	- Define servers, network, and applications as code
- Modify the infrastructure and create versions
	- The same way you vaersion application code
- Use the descrioption (code) to build other application instances
- very efficent

##### SDN - Software Defined Networking
 
_ Networking devices_ have two function planes of oeperation
- Control plane, data plate.

- Directly programmable
- Agile
	- Changes can be made at any time
- Centrally managed
	- Global view - "single pane of glass"
- Programmatically congiured
- Open standards
- Having certain network devices not physically be there but virtually like a firewall, router , switch etc

##### Softrwre defined visibility

- Dynamic deploymnents include security and network visibilty device
	- Next-generation firewalls,
- Data is encapsulated and encrypted
- Security devices monitor application traffic 
	- Visibiltiy expands as the application instances expands


### Virtualization Security

#### VM Sprawl Avoidance
- Click a button
	- Youve built a server
	- Or multiple serves, networkds, and firewalls

- need to make sure the process we have for deploying these instantces aso considers the proces of recoveirng those instances and returning them to the pool
- The vms are sprawled everywhere makes it important to have a formal process to deal with creation and deprovisioning

#### VM escape protection

- Break out of the VM and interact with the ohst operating sustem or hardware
- Once you escape the VM you have great control
- Segment the network


## 2.3 Summarize secure application development, deployment, and automation concepts.

### Secure Deployments

#### Development to production
If you’re an organization that does your own development work, there’s always a challenge in getting the application from the development process and move it into the production environment.

Each of these scenarios where you’re **moving an application from a nonproduction environment to the production environment should be very closely monitored.**

#### Sandboxing

- A sandbox is an isolated testing environment that can be used by the developers to test different aspects of the application that they’re building.
	- A technological saffe space
- Use during the development process, if something doesn’t work or goes wrong, the only people it will affect are people using that particular sandbox.

#### Building the application

The application development process generally **starts with a developer.** This would be a programmer who writes the code in a secure environment and begins testing out different aspects of the code’s functionality.
- The developers will commonly use the sandbox to perform tests, until it is fit for live production.
The application devs bring all the code together to see how the different parts will react and will be able to check if everything is working as expected.

#### Verifying the application
- Quality Assurance (QA)
	- verifies features are working as expected.
	- tests new features that have been added making sure they work
	- Verifies that old errors don't appear
- Staging
	- Almost ready to roll it out
	- Works and feels exactly like the production environment
	- Working with a copy of production data
	- Run performance test
	- Test usability and features.

#### Using the application

- Production
	-  Application is live
	- Rolled out to the user community
- Logistical challengers
	- new servers
	- new software
#### Secure baselines
- The security of an application environment should be well-defined
	- All application instance must follow this baseline
	- Firewall settings, patch levels, OS file versions
	- May require constant updates
- Integrity measurements check for the secure baseline
		-  These should be performed often—check against well documented baseline		
		- Failure requires an immediate correction

### Provisioning and De-Provisioning


#### Provisioning

- Provisioning is the process of making something available. If you are provisioning an application, then you’re probably going to deploy a web server, a database server. There may be a middleware server and other configuration and settings to be able to use this particular application.
- the provisioning of this application instance also includes security components. We want to be sure that the operating system and the application are up-to-date with the latest security patches.
- be sure that our network design and architecture is also secure. So we might want to create a secure VLAN just for this application.
	- There might be a set of configurations and a firewall for internal access and a completely different set of security requirements for external access.

-  if we’re deploying software to a workstation, we may want to run our own scans of that software and make sure there’s nothing inside of that binary that may look malicious.
	-  check the security posture of the workstation and make sure that the workstation itself is up to date with the latest patches and is running all of the latest security configurations.
-
#### Scalability and elasticity
- Handle application workload and adapt to dynamic changes
- Scalability
	- The ability to increase the workload in a given infrastructure 
- Elasticity 
	- Increase or decrease available resources as the workload changes
		- Like a a rubber band

#### Orchestration

- Automation is the key to cloud computing
	- Automate the provisioning and deprovisioning these applications
- Entire application instance can be instantly provisioned
	- All servers , networks, switches, firewalls, and policies
- Instances can move around the world as needed
	- Follow the sun
- The security policies should be part of the orchestration
	- As applications are provisioned, the proper security is automatically included.

#### Deprovisioning

- Dismantiling and removing an application instance
- Security deprovisioning is important 
	- Don't leave open holes, don't close important ones
- Firewall policies must be reverted
	- If the application is gone so is the access
- What happens to the data?
	- Dont leave that out there delete that bitch.

### Secure Coding Techniques

#### Secure coding concepts
- A balance between time and quality
- Testing, testing, testing
	- QA process
- Vulnerabilities will eventually be found

#### Stored procedures

- SQL databases
	- Client sends detailed requests for data
- Client requests can be complex and sometimes modified by the user
- Stored procedures limit the client interactions
- Attack cant use database calls
- Think of it as a placehold for the actual command

#### Obfuscation/camouflage

- Obfuscate
	- Not human readable
- Makes it more difficult for attackers to look for holes in code.


#### Code reuse/dead code

- Code reuse 
- If the old code has security vulnerabilities all the new apps have the same one
- Dead code
	- Calculations are made, code is executed, results are tallied but not used anywhere else in the app
	- ALL code is an opportunity for a security problem

#### Input validation

- Find a place where the input is not properly validated
- Document all input types
- Check and correct all input if not then could be a possible hole 

#### Validation points

- Server-side validation
	- All check occur on the server
	- Helps protect against malicious users
- Client-side validation
	- The end-user's app makes the validation decisions
	- may provide better speed
- Server side is safer less manipulable

#### Memory management

Malicious users will try to get around some of these input validations, to put their own data into the memory of your computer,
	- buffer overflow
		- the user might be able to send more data than what was expected and overflow a section of memory.
	- fuck a third party library write your own shit

#### Third-party libraries and SDKs 
- SDK: software development kits , speeds up the dev process.
- Security risk 
	- App code written by someone else
	- Might be secure, might not

- DO YOUR REASEARCH

#### Data exposure

In many applications, we’re inputting a lot of sensitive data. We could put in our name, our address, our birthday, our social security number, information about our family, our medical information, and so much more. That information needs to be secure. We need to make sure that we are encrypting this data when we’re storing it into some type of database or storage system.
- Encryption of data when handing it.

#### Version control

- Create a file, make a change, make another change and another…

- Commonly used in software development
- Useful for security
	- compare versions over time
- A security challenge make sure a third party doesn't gain access to that information
- GIT MY BOYS


 ###  **Software diversity**

**Compiler**: _To make executables most robust against attacks, an organization may choose to use a special compiler that creates different binary executables every time._
    -   **Binary** file will be different every time
    - An attack with only be successful on a fraction of the users

###  **Automation/scripting**: 

Automated testing uses special testing software that works with scripts commonly written by the programmers (or perhaps the quality assurance team) to create automated courses of action for the deployment process.

- **Continuous monitoring**: _Automated processes that monitor the functioning of the application._
    - **Continuous validation**: _Tests to verify the code is running as expected._
    -   **Continuous integration**: _Processes to verify different parts of the application software are working together properly._
    -   **Continuous delivery**: _Automated tools to deploy the latest version to a customer._
    -   **Continuous deployment**: _The process that makes continuous delivery happen._

DEVOPS WOOOO



## 2.4 Summarise authentication and authorisation design concepts.

-   -   **Directory services**:
			- Keeps all of an organization's usernames and passwords in a single database.
			- Access via Kerberos or LDAP
    -   **Federation**: _A federated system involves the use of a common authentication system and credentials database that multiple entities use and share. This ensures that a user’s credentials in Company A would be acceptable in Company B and Company C, and only access permissions would be the determining factor in accessing systems and data. Windows Active Directory is a good example of a federated system in practice; user credentials from different domains could be used in other domains if they are all part of the same Active Directory forest._
		    - Provide network access to others
		    - Third-parties can establish a federated network
		    - Third-parties must establish a trust relationship
    -   Attestation
	    - Prove the hardware is really yours
	    - Your having the system 'attest' that the hardeware that is connecting into the network is the hardware you originally setup that is trustworthy to connect to the system.
	    - OTP "One time password"
			     -   Technologies of Attestat
        -   **Time-based One Time Password (TOTP)**: _A time-based one-time password (TOTP) uses time as a factor to assist in generating a OTP. Normally, the user has a set number of seconds to input the correct password before it changes and another one must be used. This has many advantages, including the prevention of replay attacks._
        -   **HMAC-based One Time Password (HOTP)**: _The Hash-based Message Authentication Code (HMAC) provides for message authentication and data integrity. HMAC can use either MD5 or the SHA series of hashing algorithms and various key sizes. In the case of HOTP use, the user is authenticated against the centralised authentication database, and the authentication server calculates the HMAC value and sends it to the user via an authentication device such as a token. Several popular authentication mechanisms that use mobile devices, such as smartphones, make use of HOTP._
        -   **Short Message Service (SMS)**: _Many security systems use standard communication methods to convey an OTP. Common systems send an OTP via short message service (SMS) to a smartphone, for example._
        -   **Token key**: _Hardware tokens are physical devices such as a USB security key linked to a specific account and plugged into the client computer. Software tokens are applications that generate OTPs._
        -   **Static codes**: _Expect a question on the CompTIA Security+ exam on static codes for authentication. These refer to personal identification numbers (PINs) that you use to log into a Microsoft account, for example, or to finish authenticating with an automated teller machine (ATM) at the bank. Most smartphones require a static code for login (i.e., authentication)._
        -   **Authentication applications**: _You can use general authentication applications as a part of two-factor authentication at various websites. The [https://login.gov](https://login.gov/) website, for example, enables users to add one of various apps to their smart devices, such as Google Authenticator, Authy, LastPass, or 1Password, to create that second authentication factor._
        -   **Push notifications**: _Another way of receiving a OTP._ Similar process to an SMS notification. Still more secure than SMS.
        -   **Phone call**: _Another way of receiving a OTP._
    -   **Smart card authentication**: _Adding a storage chip to a standard credit card–sized plastic card creates a way for an individual to store personal information, a smart card. Smart cards can store any binary data, not just certificates. Some applications use smart cards that store symmetric keys, digital signatures, PINs, or personally identifiable information (PII)._
-   **Biometrics**: _Human physical characteristics that can be measured and saved to be compared as authentication in granting the user access to a network or resource. Common biometric factors used in access control include fingerprints, facial scans, retinal scans, voice pattern recognition, and others._
    -   **Fingerprint**: _Self explanatory._
    -   **Retina**: _Self explanatory._
    -   **Iris**: _Self explanatory._
    -   **Facial**: _Self explanatory._
    -   **Voice**: _Self explanatory._
    -   **Vein**: _Self explanatory._
    -   **Gait analysis**: _Gait analysis measures the unique way a person walks or runs by using machine vision–based tools—external cameras, in other words—or via the sensors built into existing smartphones._
    -   **Efficacy rates**: _Biometric systems are not foolproof._
    -   **False acceptance**: _The FAR is the rate of errors from incorrectly authenticating unauthorised users._
    -   **False rejection**: _The FRR is the rate of errors from incorrectly rejecting authorised users._
    -   **Crossover error rate**: _The crossover error rate (CER) is the point at which the system must be tuned to reduce both types of errors effectively without increasing either one of them._
-   **Multifactor Authentication (MFA) factors and attributes**: _Multifactor authentication (MFA) uses more than one factor or attribute to identify a user and validate her credentials._
    -   **Factors**
        -   **Something you know**: _The knowledge factor relates to something you know, typically used when you identify yourself to a system with a user name and password combination. You know your user name and password, and use your memory to present them to the system._
        -   **Something you have**: _The possession factor relates to something you have. You physically possess an object to use as an authenticator. Scanning a gym membership card to gain access, for example, uses something you have._
        -   **Something you are**: _The inherence factor relates to something you are, relying on a person’s unique physical characteristics that can be used as a form of identification, such as fingerprints, retinal eye patterns, iris patterns, handprints, and voiceprints._
    -   **Attributes**
        -   **Somewhere you are**: _The location attribute relates to your location when you authenticate. This attribute could use either physical or logical locations and requires you to be in a certain location when you authenticate to the system._
        -   **Something you can do**: _Something you do, meaning that when you present your credentials to the system, you must perform an action, is a common attribute that accompanies authentication factors. The best example of this type of authentication attribute is when you use a finger or hand gesture on a smartphone or tablet to log in._
        -   **Something you exhibit**: _Something you exhibit can refer to something neurological that can be measured or scanned; it could be a personality trait or a mannerism. Speech analysis systems could very easily identify Barak Obama from the cadence of the way he talks, for example, with distinctive pauses._
        -   **Someone you know**: _The someone you know attribute reflects a trust relationship._
-   **Authentication, Authorization, and Accounting (AAA)**:
    -   **Authentication**: _Authentication gets you in the door of a shared resource; the key unlocks the box._
    -   **Authorization**: _Authorization defines what you can do once you authenticate._
    -   **Accounting**: _Accounting or auditing enables security professionals to keep track of the accesses that take place on any given resource over time._


## 2.5 Given a scenario, implement cybersecurity resilience.
### Redundancy
  **Geographic dispersal**: _Self explanatory. The gold standard for system redundancy is to make perfect copies of the same system and spread them apart geographically, then use the Internet to keep the copies identical._ So that in the case of partial failure, a backup is always available.
    -   **Disk** Redundancy
        -   **Redundant Array of Inexpensive Disks (RAID) levels**: _Redundant array of inexpensive disks (RAID) is a fault tolerance technology that spans data across multiple hard disk drives or solid state drives within a server or workstation. This level of fault tolerance specifically addresses hard drive failure and balances the need for data redundancy with speed and performance. RAID uses multiple physical mass storage drives to create logical drives, usually making it transparent to users. Data is spanned across the different physical drives, along with metadata (usually parity information), so that if any one drive fails, the other drives in the RAID set can continue to provide data while the single drive is replaced._
            
           RAID Level
            
            Details
            
            Minimum Number of Physical Drives Required
            
            RAID 0
            
            Striping, no mirroring of parity.
            
            -
            
            RAID 1
            
            Mirroring, no striping or parity.
            
            -
            
            RAID 5
            
            Striping with parity. 1/n of the total disk space is used for parity.
            
            -
            
            RAID 6
            
            Striping with double distributed parity. Allows for failure of up to 2 drives.
            
            -
            
            RAID 10
            
            A stripe of mirrors.
            
            -
            
            RAID 01
            
            A mirror of stripes.
            
            -
            

-   **Multipath**: _A multipath solution provides more than one way to access storage. A RAID 1 implementation with two controllers, one for each drive, is the traditional multipath solution. More than one connection to a SAN is also a typical implementation of multipath._

-   **Network** Redundancy
    -   **Load balancers**: _A load balancer is a network device used to provide efficient and seamless workload sharing between network devices (such as routers or firewalls) or hosts, typically Web or file servers or storage devices. Placed strategically between devices, a load balancer enhances security and efficiency._
    -   **Network Interface Card (NIC) teaming**: _Network interface cards rarely fail, but when one does, the system with the bad NIC is offline until the NIC is replaced. Network interface card (NIC) teaming addresses this issue by using two or more NICs on a single system that act as though they are a single NIC with one MAC address and one IP addresses. Not only does NIC teaming increase throughput (sort of), but if one NIC fails, the other continues to work._
	    - Port aggregation.
-   **Power**
    -   **Uninterruptible Power Supply (UPS)**: _An uninterruptible power supply (UPS) uses a small battery (often the same type used in motorcycles) as a backup power source if the power ever sags or goes out completely._
    -   **Generator**: _If you need to ensure that a system has uninterrupted power for an extended period of time after a power failure, you need to consider an onsite generator as a source of backup electricity._
    -   **Dual supply**: _Many higher-end devices support dual power supplies. These aren't complicated: if one power supply goes out, the other takes over._
    -   **Managed Power Distribution Units** (PDUs): _At the simplest end a simple power strip is a PDU, but if you’re going to distribute power, why not use a managed PDU that can monitor power usage, send alarms, and so forth?
	    - <img src = "https://i.gyazo.com/c4a1983571fd3937fd5a5438b8febc6a.png">
	    
- ### **Replication**:
    -   **Storage Area Network**: _A storage area network (SAN) is a network storage that enables you to access the shared folders by using block-level controls rather than the network stack. This gives SANs some unique capabilities, mainly on-the-fly volume creation/manipulation. On most systems, if you want to add storage, you first get a storage device, configure it, mount it, and format it. On a SAN, you just tell the SAN controller to add another disk to your local system. You can create a new volume, or you can mount an existing volume._
    -   **VM**: _The capability to push out multiple identical copies of VMs from a master image is categorized as replication on the CompTIA Security+ exam._
-   **On-premises vs cloud**: _Nothing beats virtualization, especially cloud-based services, for giving you all the benefits of redundancy, especially high availability, without outrageous cost and time. First, virtualization solutions are incredibly scalable. Virtualization also makes geographic dispersal easy to achieve. Is your new Website huge in Japan? Just tell Amazon to spin up some new servers over in Japan, so your customers in Tokyo get the same speed and response as your US users._
	- Speed'Money'Security 
- ### **Backup types**
    -   **Full**: _In a full backup, regardless of whether you back up a shared folder, a single hard drive, a RAID array, or an entire server, everything is included in the backup set. At the basic file system level, a full backup also sets the archive bits on files to indicate that the files have been backed up. One important difference between the standard full backup method and copy or image is that the latter two do not turn off the archive bit.
    -   -   **Incremental**: _The incremental backup typically backs up only files that have changed since the last full backup. In other words, when an incremental backup runs, it backs up only the files that have the archive bits turned on. After it backs up those files, it turns off the archive bits. If a full backup is run, and then files subsequently change, an incremental backup backs up only those files._
    - <img src = "https://i.gyazo.com/652f9bbf51e947018f30c2f01af68d77.png">
    - 
    -   **Snapshot**: _A snapshot stores a version of an operating system (including applications) at a given moment in time. These are common for individual system backups, such as restore points in Windows and Time Machine backups in macOS. For servers and such, a snapshot as a backup refers to the powerful feature with virtual machines that enables you to save a version of a functional VM to restore very quickly if anything negative happens to the functional server._
    -   **Differential**: _The differential backup also gets only a subset of the total data and is also based upon the archive bit setting. However, the major difference between a differential backup and an incremental backup is that the differential backup does not clear the archive bit—it leaves it turned on.
    - <img src = "https://i.gyazo.com/402b602dbadf887d83fb4e47fd2feed4.png">  
    -   **Tape**: _A lot of cloud storage providers still use tape for archival backup, especially for records an organisation probably won’t need but must store for a set number of years to comply with government regulations._
    -   **Disk**: _Backing up to a hard disk._
    -   **Copy**: _A full copy (typically using dd). Does not affect archive bits._
    -   **Network Attached Storage (NAS)**: _A network-attached storage (NAS) system is a standalone box filled with removable hard drives._
    -   **Storage Attached Network (SAN)**: _A storage area network (SAN) typically combines multiple devices into a coherent block-storage space, then connects to hosts using blazingly fast Fibre Channel networking. The block storage enables a SAN to provide simultaneous high-speed access to multiple users, divide space in whatever way makes sense for the network, and even create what appears to be external hard drives connected to local machines. SANs are much more complicated and expensive than NASs but are pretty much the solution for enterprise on-premises backup and storage._
    - **Other Backups**:
    -   **Cloud**: _Backing up to cloud storage._
    -   **Image**: _Creating an image, usually using dd. Does not affect archive bits._
-  
    -   **Online vs offline**: _The concept of online versus offline backups refers to the state of the data at the time of the backup. When dealing with a big database, for example, an online backup means the backup happens while the database is live and in use by however many numbers of simultaneous users. With an offline backup, in contrast, the database is shut down._
    -   **Offsite storage**: _Storing backup drives at a location distant from your primary organisation provides essential security in the event of a disaster._
        -   **Distance considerations**: _Storing backup drives at a location distant from your primary organisation provides essential security in the event of a disaster. The location of offsite backups and services matters because of law and international jurisdictions._

### Resiliency
-   **Non persistence**: _Non-persistence simply means to possess a method to bring a system back quickly to its pre-attack state._
    -   **Revert to known state**: _Every major OS has some form of revert/rollback method to bring a system back to a previous state, what the CompTIA Security+ objectives call revert to known state. All revert/rollback methods work by making the OS aware of changes and then storing files or settings in such a way that techs can look up previous states and tell the OS to go back to one of those states._
    -   **Last known good configuration**: _Older Windows versions (such as Windows 7) offered a boot feature called last known good configuration that enabled quick recovery from installation of a buggy driver._
    -   **Live boot media**: _Live boot media are complete, installed operating systems that exist on bootable media._
-   **High availability**
    -   **Scalability**: _Redundancy provides high availability. High availability means using redundancy in such a way as to ensure that certain levels of operational performance are balanced against risk._
-   **Restoration order**:
	- Application-specific
		- Certain components may need to be resotred first
		- Databases should be restored before the application
	- Backup-specific 
		- Incremental backups restore the full backup, then all subsequent incremental backups
		- Differential  backups restore the full backup, then the last differential backup
-   **Diversity**: _Diversity refers to the practices of using a variety of technologies, vendors, cryptographic systems, and controls to avoid the possibility that all systems have the same vulnerability and can be taken out en masse. When organisations rely on multiple redundant technologies, vendors, cryptographic systems, and security controls, that diversity provides cybersecurity resilience. If a single technology fails, a vendor disappears, the crypto system is cracked, or security controls change and conflict, an organization that employs multiple systems through diversity can quickly pivot and implement fixes._
    -   **Technologies**
	    - A zero-day OS vulnerability can cause significant outages
	    - Multiple security devices
    -   **Vendors**
	    - A single vendor can be a vulnerability
    -   **Crypto**
	    - All cryptography is temporary
	    - Diverse certificate authorities can provide additional protection
    -   **Controls**
	    - Administrative controls
	    - Physical 
	    - Technical 
	    - Combine them together
	    - Defense in depth

## 2.6 Explain the security implications of embedded and specialised systems.

-   **Embedded systems**: _CompTIA uses the term embedded system to describe discrete hardware components that make up portions of systems._
    -   **Raspberry Pi**: 
    - Multiple Components on a single chip
    - Acts like a desktop computer
    - Small form factor
    - Security considerations: Difficult to upgrade hardware, Limited off-the-shelf security options.
	- **(SoC) System on a Chip**. 
	
    -   **Field Programmable Gate Array (FPGA)**: _Embedded systems that require flexibility in processing capabilities use field- programmable gate array (FPGA) computers that, as the name suggests, you can reprogram to optimize for various tasks. An FPGA does not have a fixed CPU, like the Raspberry Pi, but rather has integrated circuits (ICs) that developers can redefine as needed. You’ll see FPGAs used in vehicular systems, such as airplanes and automobiles, where switching hardware to make changes would be prohibitively expensive. Reprogramming the hardware for updates or corrections makes more sense. Embedded systems running on an FPGA tend to run a real-time operating system (RTOS), such as Windows Embedded Compact (Figure 9-2). An RTOS is designed to respond in real time to inputs. An RTOS is critical for anti-lock brakes, safety stops, and so forth. From a security standpoint, keeping the firmware up to date to work through bugs helps. Plus, limiting physical access to control ports or connections minimises the potential for an attacker to damage your systems._
	    - An integrated circuit that can be configured after manufacturing 
	    - A problem doesn't require a hardware replacement 
    -   **Arduino**: _Arduino systems have security concerns. Physical access, like with FPGA systems, presents a clear danger. The limited memory on Arduino-based systems leaves them vulnerable to buffer overflow and heap attacks. The systems often connect automatically to the nearest access point when the default connection fails, again providing an opportunity for mischief. As with all computing systems, assume Arduinos need careful thought and preparation for security._
-   **Supervisory Control and Data Acquisition (SCADA)/Industrial Control System (ICS)**: _Supervisory control and data acquisition (SCADA) systems are used in industrial applications. SCADA systems are more and more often being connected to the Internet, and often in an unprotected state. They run TCP/IP protocols and use embedded versions of some of the popular consumer operating systems, such as Windows or Linux. This makes SCADA systems prime targets for hackers, who attack them to damage critical infrastructure, launch denial-of- service (DoS) attacks, and generally create mischief and outright harm._
    -   **Facilities**
    -   **Industrial**
    -   **Manufacturing**
    -   **Energy**
    -   **Logistics**
-   **Internet of Things (IoT)**: _The term Internet of Things (IoT) describes the many computing devices (other than PCs, routers, and servers) that connect through the Internet, which is about as broad a definition as it gets. IoT often refers to smaller helper devices, such as lightbulbs you can turn on or off remotely, but it also applies to heating and cooling systems (facility automation tools), smart devices like a refrigerator that can tell you how much milk is left, diapers that inform you when junior needs a change, and so on._
    -   **Sensors**
    -   **Smart devices**
    -   **Wearables**
    -   **Facility automation**
    -   **Weak defaults**: _What IoT devices have in common from a security standpoint are weak default settings. Most manufacturers of IoT devices in the consumer sphere, for example, err on the side of ease of use for the consumer rather than rigorous security for the power user or IT security specialist. Fine-tuning options such as connectivity and notification settings can go a long way toward adding worthwhile security to IoT devices._
	    - For the love of God don't keep your admin user/pass.
-   **Specialized**: _Both CompTIA and many writers throw up their hands at the rest of the dedicated systems, calling them simply specialized._
    -   **Medical systems**: _IoT pacemakers not only provide stimulus to regularize the heartbeat, but also transmit over the Internet so doctors and technicians can monitor the patient’s heart and the current level of battery power. Other Internet of Medical Things (IoMT) devices—both wearable and implanted—monitor all sorts of things, from general vital signs to specific things like glucose levels in diabetic patients. The IoMT field continues to grow, combining medical systems with phenomenal technology advances. The inherent security risks involved with IoMT devices cannot be dismissed. Any device that connects to a network has vulnerabilities and the potential for hacking. A hacked medical lifesaving device could have deadly consequences._
    -   **Vehicles**: _From a security perspective, in-vehicle computing systems have some of the same common vulnerabilities that other systems have, which may include network security issues, such as the vulnerabilities inherent to Bluetooth, Wi-Fi, and cellular technologies. There are also issues involving firmware and patch updates to the systems. Many of these systems have USB or SD card ports, for example, to upload firmware updates or play media content on the devices. Perhaps someday someone will develop a virus or other type of malware that could be injected into these types of systems via a removable media device._
    -   **Aircraft**: _Aircraft of all sorts, both manned and unmanned, have increasingly sophisticated computing systems, many connected to extended networks and the Internet._
    -   **Smart meters**: _Smart meters rely on cellular and wireless networks to communicate to consumers and utility companies real-time information about power usage, usually electricity, but also natural gas or water.
-   **Voice over IP (VoIP)**: _You need to secure VoIP communications just like you would any other IP network. Typical VoIP attacks include denial of service, spoofing telephone numbers, and just harassment._
-   **Heating, Ventilation, Air Conditioning (HVAC)**: _Self explanatory._
-   **Drones**: _Drones typically have multiple embedded camera systems, high-end wireless networking capabilities, and an SoC to run them all._
-   **Multifunction Printer (MFP)**: _Multifunction devices (MFDs) that combine printers, scanners, and copiers into one machine and then add Internet capabilities. You can print to MFDs from a variety of devices, including smartphones like the Apple iPhone via AirPrint, plus scan and send PDF files directly to Internet or e-mail destinations._
-   **Real Time Operating System (RTOS)**: _A RTOS is designed to respond in real time to inputs. An RTOS is critical for anti-lock brakes, safety stops, and so forth._
	-  Airline traffic control systems, Command Control Systems, Airlines reservation system
	- Military Enviornments
	- Extremely sensitive to security issues
-   **Surveillance systems**: _The security implications and considerations with modern IoT surveillance systems run from paranoia to downright scary. Ring devices, for example, interface with Amazon Alexa home infotainment devices to send your security footage to “the cloud.” Nothing stops “the cloud” from sharing your footage with local law enforcement or companies that can monetise the information in some other way. Other device manufacturers have been accused of sending personal information gathered from their devices secretly to other nation states._
	- Sometimes physically difficult to replace cameras
	- Segment the Cameras just in case they are compromised
-   **System on Chip (SoC)**: _The system on chip (SoC) design concept is where all the processing components reside on a single circuit board—that includes CPU, RAM, system BIOS, Ethernet networking, and Wi-Fi networking._
- #### **Communication considerations**
    -   **5G**: _5G networks operate at three distinct bands: Low-band, Mid-band, and High-band. The higher the band, the faster the connection speed, but the shorter the range. 5G devices connect automatically at the fastest speed available at range. Cellular voice and data services these days offer very robust security. Direct sniffing of these networks is difficult at best (assuming you’re using a late-generation 4G/LTE or 5G phone). Carriers will quickly detect and act on any attempts to emulate a cell tower, for example, which could lead to serious legal ramifications for the bad actor._
    -   **Narrow band**: _Developers use the Narrowband Internet of Things (NB-IoT) technology for high connection density IoT deployment, specifically with an eye to maximising battery life and minimising costs. Narrowband means NB-IoT uses only a single radio frequency — 200 KHz. The goal with NB-IoT is to provide good coverage and devices that don’t need recharging for years._
	    - SCADA
	    - Oil Fields
    -   **Baseband radio**: _Part of the underlying physical layer of NB-IoT can rely on devices that use baseband radio processors that manage radio functions from multiple devices. Sounds like a circular definition, but you might see the term on the exam._
	    - SIngle cable w a digital signal
	    - Bidirectional communication
	    - Ethernet standart
    -   **Subscriber Identity Module (SIM) cards
	    - provide information to a cellular network provider
	    - contains mobile details
	    - Important to manage
    -   **Zigbee**: _Devices and systems that rely on the Zigbee communication protocols offer ad hoc personal area networks that use very low-power radios. This low-bandwidth solution works perfectly for things like medical device data collection and home automation. Zigbee is an open standard, so adoption by manufacturers is increasing._
	    - IoT networking
	    - Less power than wifi , longer distance than bluetooth
-   **Contraints**
- These systems have to trade one thing for a another , for example more ram but less space for power; more portability less ability to patch.
    -   **Power**
    -   **Compute**
    -   **Network**
    -   **Crypto**
    -   **Inability to patch**
    -   **Authentication**
    -   **Range**
    -   **Cost**
    -   **Implied trust**

## 2.7 Explain the importance of physical security controls.

-   **Bollards/barricades**: _Barricades are physical security devices that can block unauthorised personnel from entering an area. Barricades are often used in the area surrounding a facility to keep vehicles from getting too close to a building, for example. They can also be used inside a facility to control the flow of people through secure areas.
	- Prevent access
	- Channels people through a specific access point
	- Identify safety concerns
	- Prevent large items from entering a certain area
-   **Access control vestibules**: _CompTIA uses the nonstandard term access control vestibule to refer to mantrap-designed rooms. Although the non-gendered term should be used, you’re unlikely to hear it in common speech for many years. Be prepared for either term on the CompTIA Security+ exam. A mantrap usually has some type of authentication station in the room, or even a one-way glass window so that a guard can observe the individual and confirm his or her identity, or ensure that the visitor doesn't possess any unauthorised weapons or items. The individual may have to use biometrics or a smart card and PIN to authenticate themselves at the station. If the individual is properly authenticated, the exit doors open and allow the person to enter into the secure area. If the individual is not authenticated, or the guard suspects an issue with the person, he or she can be detained in the mantrap until the proper authorities or security personnel can be summoned to help secure the person. 
	- **Mantraps** are normally used in highly secure facilities, such as data centers, where positive authentication of personnel is of critical importance._
-   **Badges**: _Positive identification and authentication using access badges can mitigate vulnerabilities associated with tailgating._
-   **Alarms**: _Physical alarm systems and intrusion detection systems are a must in any physical security program. Alarm systems can be loud and obnoxious, such as fire or tornado alarms, but they can also be silent alarms that sound or activate only at a guard station._
	- Motion detection
	- Circut - based - opening of a door or window
	- Duress/Panic button
-   **Signage**: _Signage helps deter unwanted visitors. Signs can warn intruders away from restricted areas and instruct authorised personnel to follow the proper security and safety procedures. Signs can direct personnel during an evacuation to the correct exit points, warn personnel about potential safety hazards in the facility, or help them find proper safety or fire suppression equipment. In short, the value of signs cannot be understated, because they may be required to help deter unauthorised activities or intruders but can also help protect the safety of the people who work in the facility._
	- Clear and specific instructions
	- Workers and visitors
	- Safety, fire exits, chemicals, first aid , etc...
	- Informational
-   **Cameras**: _CCTVs use cameras to record surveillance video and transmit it to a central monitoring station, which enables guards to extend their view of the facility._
    -   **Motion recognition**: _Recording systems should automatically kick in with motion recognition hardware detecting movement, thus capturing anything larger than a squirrel that enters a camera’s field of view. CCTVs should also date and time stamp those recordings so that a realistic time frame of events can be reconstructed if needed._
    -   **Object detection**
-   **Closed Circuit Television (CCTV)**: _CCTVs use cameras to record surveillance video and transmit it to a central monitoring station, which enables guards to extend their view of the facility._
-   **Industrial camouflage**: _Conceal an important facility in plain sight but it blends into the local enviornment. There should be no identifying features that would tell you that this unsuspecting build is for example a data center._
-   **Personnel**
    -   **Guards**: _Security guards have specific training and skills to monitor and maintain facility security._
    -   **Robot sentries**: _Self explanatory._ EXTREME ROOMBAS
    -   **Reception**: _Guards in the reception area of a building manage people in real time. They can actively review people who step up to the entryway and, again, actively allow or deny access to the facility. They can and should log in and out every single visitor on a visitor log._
    -   **Two person integrity/control (TPIC)**: _Expect a question on the CompTIA Security+ exam that addresses two-person integrity/control. In a general sense, two-person integrity (TPI) simply means that you have two guards in the same space at all times, so one guard can’t mess up (inadvertently or on purpose) without the other guard catching the problem. Specifically, TPI refers to the nuclear weapons controls in the United States; again, so one person can’t make a catastrophic mistake. It’s a failsafe mechanism._
-   **Locks**: _Locks are physical security controls that can help keep unauthorised persons from entering doorways, secure areas, and perimeters._
    -   **Biometrics**: _Security controls that use biometrics to verify authorisation._
    -   **Electronic**: _Electronic locks are more sophisticated and may use various protection mechanisms. Usually, an electronic lock uses a PIN code and may be known as a cipher lock. Electronic locks usually have their mechanisms protected by metal containers or embedded into wall._
    -   **Physical**: _Combination locks, which require a numerical combination or PIN code to unlock them, and locks built into the door or other type of entrance (such as a gate, vault, or safe) are also popular hardware locks. Each has advantages and disadvantages, depending on the level of security you require. Each also has different variations. Ordinary padlocks, referred to as warded locks, may appear to be strong, but they can easily be cut or picked._
    -   **Cable locks** , Locks computer down temporarily , can be cut but is a means of friction for attackers
-   **USB data blocker** 
	-  Don't connect to unknown USB interfaces
	- Allow the voltage , reject potential data.
-   **Lighting**: _Lighting is another critical aspect of perimeter security. During evening or dark hours, lighting can help ensure that trespassers, attackers, and thieves are deterred from venturing out into open areas when trying to approach a facility or harm its personnel._
-   **Fencing**: _Fencing deters unwanted and unauthorised visitors. Fencing is often used at facilities that require higher security than a simple lock on the door. Fencing can intimidate trespassers or attackers._
-   **Fire suppression**: _Most modern data centers these days have foam fire suppression systems, such as FM-200 or another approved chemical foam. This type of system not only is very effective for putting out large fires but is also typically safe for humans and equipment._
-   **Sensors**
    -   **Motion detection**: _Motion detection involves sensing the presence of a person in an area using different types of sensors._
    -   **Noise detection**: _Noise detection sensors pick up unusual sound levels and are used in very specific security settings, such as hospitals._
    -   **Proximity reader**: _A proximity reader device is used to help authenticate personnel entering or exiting a facility. The person places a smart card or other access device near the sensor so it can be read via RFID or another passive wireless technology. The reader receives information from the card regarding the individual’s identity. The individual may further authenticate by using a PIN or biometric method, such as a thumbprint scan, retinal scan, or voiceprint._
    -   **Moisture detection**: _A device that monitors humidity in a data center is called a hygrometer or, if it can measure both temperature and humidity at the same time, a hygrothermograph. Like automated temperature controls and other HVAC equipment, these devices can be centrally monitored through a remote console and alert operators whenever the temperature or humidity changes from certain levels. HVAC controls can be automatically or remotely adjusted based upon information received from these monitors._
    -   **Cards**: _Smart card sensors._
    -   **Temperature**: _Thermometers._
-   **Drones**: _Small, remotely controlled flying surveillance vehicles — drones — form increasingly useful tools for security professionals to patrol areas._
-   **Visitor logs**: _Guards in the reception area of a building manage people in real time. They can actively review people who step up to the entryway and, again, actively allow or deny access to the facility. They can and should log in and out every single visitor on a visitor log._
-   **Faraday cages**: _Faraday cages are devices that prevent RFI or EMI from damaging contents stored. Faraday cages are named for the English scientist—Michael Faraday—who created the design way back in the 19th century._
-   **Air gap**: _Passive security methods also include network design, such as providing physical separation between secure and nonsecure networks, an air gap. A highly secure facility, for example, would have interconnected internal systems to enable people to get work done, but have an Internet-connected system in a reception area for visitors to use. That system would in no way connect with any of the secure systems._
-   **Screened subnet (previously known as a Demilitarised Zone (DMZ))**: _A network that includes public servers must have a more complex topology that protects Internet systems but still enables less-protected access for public servers. To do this, create a screened subnet—also known as a demilitarised zone (DMZ) - a LAN, separate from the internal LANs that contain workstations and private servers. The DMZ connects to the Internet via a lightly firewalled router, and an internal network connects to the DMZ via a much more aggressively firewalled router._
-   **Protected cable distribution**: _Protecting physical cabling is as much about facility design as anything else. The facility should be designed so that physical cabling is run outside of normal traffic areas, through ducts in the walls or ceiling. The end connection points of the cabling should be physically protected from unauthorised access, by placing termination points such as switches in locked closets, and protecting end-user device connection points in offices and other rooms from unauthorised access. In addition to physical security design, protecting cabling involves other possible measures, including using shielded cabling to prevent eavesdropping (or using fiber cable); configuring systems to send alarms when a connection is lost, possibly indicating a cut or damaged cable; and even using technical or logical controls that prevent unauthorised devices from connecting to end- user cable connection points, such as network outlets, by controlling port access._
#### **Secure areas**
  - **Air gap**: _Passive security methods also include network design, such as providing physical separation between secure and nonsecure networks, an air gap. A highly secure facility, for example, would have interconnected internal systems to enable people to get work done, but have an Internet- connected system in a reception area for visitors to use. That system would in no way connect with any of the secure systems._
		- Disconnection from the network
		- I.e Stock Market Networks, Power systems, Airplanes , Nuclear power plants, etc...
    -   **Vault**: _A vault you've likely seen in every cops and robbers movie. A giant metal door with a super-complicated lock protects the contents of a thick-walled room._
    -   **Safe**: _Most organisations have a designated safe, a smaller version of a vault for storing valuables, such as secure passwords and important papers._
    -   **Hot and cold aisles**: _The concept of hot and cold aisles relates to designing the layout of data centers intelligently and efficiently. In this type of setup, aisles of equipment racks are set up such that there are alternating hot and cold aisles, enabling cooler air to be blown into equipment as hotter air is pulled away from them._
    - <img src = "https://i.gyazo.com/2f4a4bd7200a00215c38d4112a212954.png">
    

-   **Secure data destruction**
    -   **Burning**: _Self explanatory._
    -   **Shredding**: _Self explanatory._
    -   **Pulping**: _Self explanatory._
    -   **Pulverising**: _Self explanatory._
    -   **Degaussing**: Remove the magnetic field
    -   **Third party solutions**: _Self explanatory._



## 2.8 Summarise the basics of cryptographic concepts.


**Common terms**

- Plaintext - An unencrypted message *in the clear*
- Ciphertext - An encrypted message
- Cipher - The algorithm used to encrypt and/or decrypt
- Cryptanalysis  - The art of cracking encryption

Cryptographic keys

**Keys**
	- Add the key to the cipher to encrypt 
	- Larger keys are generally more secure

**Key stretching libraries**

Key stretching is like hashing a hash.
blueboy = kdfjakdlsdkf3423kl but then you take that hash
kdfjakdlsdkf3423kl = fdasfuhdsoafdhaifudhsjfouiahdsfodhfosdufha
hash that bitch again.

**Bcrypt**
 - Generates hashes from passwords
 - An extention to the UNIX crypt library
 - Uses Blow fish cipher to perform multiple rounds of hashing

- Password-Based key Derivation Function 2 (PBKDF2)

Lightweight cruptography
	- Cryptography with the least amount of power, great for IoT devices.
	- Emerging


-   **Digital signatures**:

_The challenge to key exchange isn't handing out the keys. The Web server and client can automatically share their public keys the moment they connect. The problem comes with the key itself. Imagine a scenario where a third party intercepts the data and tries to send a bogus public key to the client. Digital signatures address this scenario. To send a message in a typical asymmetric encryption cryptosystem, the sender encrypts using the recipient’s public key; the recipient decrypts using her private key. The reverse, however, can also work. The sender can encrypt with his private key; the only key that would enable decryption is his public key. This concept makes digital signatures possible. Here’s the full process of creating a digital signature. To prove that the public key your client receives came from the proper server, the Web server adds a digital signature. The Web server takes the current Web page and does the following:_

1.  _Encrypts the page with the client’s public key_
2.  _Hashes the page._
3.  _Encrypts the hash with the server’s private key._
4.  _Sends the page, the public key, and the hash to the client._

<img src = "https://i.gyazo.com/16bce479ddd410918e9f191ee4ebbd5b.png">


_Now it’s the client’s turn:_

1.  _The client decrypts the hash using the server’s public key to verify it really came from the server. (Only the server’s public key can decrypt something encrypted with the server’s private key.)_
2.  _The client decrypts the message with the client’s private key._

<img src = "https://i.gyazo.com/422d53b59628a96d3a876d9d2f581ca6.png">


_The hash value encrypted with the private key and that accompanies the public key is a digital signature. Digital signatures alone work great to verify the identity of a source. Successfully decrypting the message using the source’s public key means the message could only have come from that source._

#### Key Terms
-   **Key length**: _Key length or key size refers to the number of bits in a key; this number implies security — a hacker can readily break a short key, for example. With the unbelievable growth in computing power today, on the other hand, a long key doesn't necessarily equate to better security._
-   **Key stretching**: _Keys are almost always generated from some plain English password. If we just hash the password, it doesn't take a lot of time for an attacker to pick a potential password, hash it, then compare the results to a password hash file. But what if we were to make the process by which a key is derived from a password more complex? We can do so with a key derivation function. What if, for example, we hashed an initial password five times to then derive the key? This would require the attacker to run not just one hash, but five hashes for every iteration. Using key derivation functions that intentionally slow this derivation of keys is key stretching._
-   **Salting**: _A salt is an arbitrary value, usually created by the application or operating system storing passwords, added to the end of a password before it is hashed. 
- Salts defeat rainbow tables simply because (hopefully) there are no rainbow tables that include dictionary terms plus the string akxcf3sf. 
- Salts are common in just about everything that stores passwords. The downside is that a salt must be stored. If someone had access to your hashes, they also have access to the salt. 
- They can run dictionary attacks, but now they must add the salt every time and recalculate the hash, slowing cracking down immensely. Also, it is possible to grab a salt and re-create a rainbow table, although this is also a slow process._
-   **Hashing**: _Hashing provides integrity in the confidentiality, integrity, availability (CIA) triad of security by creating unique numbers for data and originators of information. In the hashing process, variable-length text, such as a document or spreadsheet, or even a password, is exposed to a cryptographic algorithm that produces a cryptographic sum, or hash (also sometimes called a message digest), of the document. This hash is only a representation of the text; it is not the same thing as the text itself. 
- Think of a hash as a unique fingerprint that identifies a very specific piece of plaintext. The piece of plaintext can be any length, and it generally does not matter how large the input plaintext is. 
- The resulting hash will always be a fixed-length piece of ciphertext, usually expressed in a hexadecimal format. Unlike the encryption and decryption process, hashing was not designed to be reversible. In other words, you don’t simply encrypt text with a hashing function with the expectation of decrypting it later. 
- Hashing is a one-way mathematical function whose sole purpose is to produce the cryptographic sum of the input plaintext. Think of the hashing process as sort of a measuring process for the data, with the resultant hash being the actual measurement itself. 
- Although its purpose is not to decrypt text, the cryptographic sum produced by hashing has some uses. First, hashing is used to provide for integrity of data. \
- A hash is unique to a particular piece of text. If one letter or word of the text is altered in any way, if even one binary digit changes, the resulting hash will differ from the original hash.
- Hashing assures the integrity of a piece of plaintext, since any changes would produce an easily detected different sum. Data transmitted over a network can be hashed before transmission and after reception, and the two resulting hashes can be compared. If the hashes match, you have unaltered data._
	- Fingerprint
	- Message digest
	- One-way trip
-   **Key exchange**: _Key exchange refers to the process used to exchange keys between users who send a message and those who receive it. Without the key, an authorised user or message recipient can’t decrypt the message; the message will simply remain as ciphertext.
- In-band key exchange involves using the same communications channel you are using to send the message to send the key. This may not be the most secure way, since that channel may be monitored by a malicious person. 
- Out-of-band key exchange involves the use of a separate, independent channel, such as snail mail, phone call, USB stick, or even a different network connection, to send the key to the authorised users.

-   **Perfect forward secrecy**: _Forward secrecy means to protect a cryptosystem from one key giving away some secret that makes it easier to crack. If an algorithm achieves this, we call it perfect forward secrecy. There is no such thing as perfect forward secrecy other than using a key only once and throwing it away —a one-time pad._
	- Elliptic curve or Diffie -Hellman ephemeral
	- Single-session use
	- Every session has new keys
	- PFS requires more computing power
	- Browser needs to support PFS
	- 

#### Quantum computing
 
-   **Communications**: _The field of quantum communication has established connections between quantum computers over fiber-optic lines that regularly transact business using Quantum Key Distribution (QKD). The connection between Shanghai and Beijing banks using quantum communication is over 2000 kilometers._
 -   **Computing**: _Quantum cryptography relies on quantum computers to accomplish a couple of things. First, future complex quantum computers (theoretically) can easily crack modern secure cryptosystems, especially RSA and Diffie-Hellman. Second, key distribution using something called quantum entanglement holds the promise that it should become completely secure, a positive development. Quantum cryptography remains in the realm of theory, not practical application today. The math works, but building machines that can handle the complexities involved seems a decade or more in the future._
-   **Post-quantum**: _The flip side to quantum cryptography, called post-quantum cryptography, speculates cryptographic algorithms that can withstand any attack using quantum computers. Wildly complex forms of encryption are already being developed, although it will be years before any form of encryption algorithm will be forwarded for public use._
-   **Ephemeral**: _Parts of the Diffie-Hellman (DH) key exchange process requires each side to create a temporary key, called an ephemeral key, which is used in only one exchange and then discarded. This ephemeral key usage is called Diffie-Hellman Ephemeral (DHE). DH relies on pseudorandom number generation to create the ephemeral keys. In most cases, this relies on pseudorandom number code that uses aspects of the underlying system like dates, MAC address of the network interface card (NIC), and other seemingly random information to make these values._

#### Stream and block cipher 
-   **Modes of operation**: _Modes of operation are **defined methods** that determine how a plaintext block is input and changed to produce ciphertext. 
- The modes of operation used in symmetric cryptosystems can run in a couple of different ways, as unauthenticated or authenticated. 
- The strength of the encryption doesn't change either way, but unauthenticated modes offer a flaw when used in online applications. An attacker can use an attack called a chosen ciphertext attack to intercept, modify, and, eventually, decrypt messages._
    -   **Authenticated**
    -   **Unauthenticated**
   

-   **Cipher suites**: _Groups of algorithms used to secure network connections._
    -   **Stream**: _Streaming algorithms operate on individual bits, one bit at a time. Streaming algorithms don’t work on blocks of text; instead, they look at each individual bit and perform a mathematical operation on that bit and then move on to the next bit. Streaming algorithms tend to work much faster than block algorithms and are used in cryptographic methods that support fast communications requirements, such as wireless technologies._
	    - Used with symmetric encryption
	    - One bit at a time
	    - You dont know what your getting in the stream until you get to that specific byte
	    - The starting state should never be the same twice
    -   **Block**: _A block algorithm operates on a predefined size of a group of bits, known as a block. Different block algorithms use different block sizes, but typical sizes are 16-, 64-, and 128-bit blocks._
	    - ECB (Electronic Codebook)
		    - The simplest encryption mode
		    - Each block is encrypted with the same key
			- CBC (Cipher block chaining)
				- Each plaintext black is XORed with the precious ciphertext block
				- <img src = "https://i.gyazo.com/8b3b11f6669d2f5bd7bbdb6b1b6ec074.png">
			-  **Counter**: _In DES, counter (CTR) mode uses a random 64-bit block as the first IV, then increments a specified number or counter for every subsequent block of plaintext. CTR mode offers the best performance._
	<img src = "https://i.gyazo.com/72d3df77f4e06e79d523081421e13329.png">
	
		
####   **Symmetric vs asymmetric**
 **Symmetric**: _Symmetric cryptography uses **a single key** that both encrypts and decrypts data. All parties that require access to a piece of encrypted data know that key. 
 Symmetric keys are sometimes called **secret keys or session keys**. Session keys, more specifically, are created and used for a single communications session. Symmetric keys require **minimal computational overhead**.
  Symmetric keys **do not scale well**: what if 100 users want to exchange information with every other user? Symmetric key cryptography excels in speed, efficiency, and the ability to handle large amounts of data easily. 
  The disadvantages primarily involve **scalability and key exchange.**
  Often **combined with asymmetric** in order to transfer a symmetric key_
    -   **Asymmetric**: _Asymmetric cryptography uses two separate keys — a key pair — for secure communication. Data encrypted with one key requires the other key in the key pair for decryption. In public key cryptography — the primary asymmetric implementation — these keys are called a public key and a private key. Each user is issued or generates a key pair for his or her own use. The user gives the public key to anyone, even posting it on the Internet. The user keeps the private key, on the other hand, secret. With public key cryptography, what one key encrypts, only the other key can decrypt, and vice versa. If the key in the pair is used to encrypt a message, it cannot decrypt the same message. This makes the cryptography process, particularly sending and receiving confidential messages, different from the process used in symmetric key cryptography. Asymmetric key cryptography has several advantages over symmetric key cryptography, the major one being key exchange. The process eliminates key exchange issues, since no one really has to exchange a key. Anyone can acquire the public key. Asymmetric key cryptography has a couple of disadvantages as well. First, it’s slower than symmetric key cryptography and more computationally intensive to generate keys. Second, it works well only with small amounts of data; it’s not suited for bulk data encryption or transmission._
-    **Elliptic-curve cryptography**: _Elliptic-curve cryptography (ECC) is an asymmetric method of cryptography based on problems involving the algebraic structure of elliptic curves over finite fields. It requires low computational power and memory usage, so ECC has been widely implemented in smartphones and other low-power mobile devices. ECC typically **uses much smaller key sizes than other asymmetric algorithms**, but these smaller-sized ECC keys are also harder to break. The largest known ECC key broken to date is only a 112-bit key, for example, compared to a 768-bit key size that has been broken with RSA._

Symmetric key from asymm key 

<img src = "https://i.gyazo.com/376d19401245c40f869fe52ba47aef2f.png">

#### Other Cryptography
-   **Lightweight cryptography**: _Low-powered IoT devices rely on light- weight cryptographic algorithms that don’t offer as much security as heavier ones—because they need to function using much lower computing power._
-   **Steganography**: _The science of hiding information in other data_
    -   **Audio**
    -   **Video**
    -   **Image**
-   **Homomorphic encryption**: _Homomorphic encryption enables manipulation of encrypted data — without decrypting — that then applies to that data when it’s decrypted._
-   **Common use cases**
    -   **Low power devices**
    -   **Low latency**
    -   **High resiliency**
    -   **Supporting confidentiality**
    -   **Supporting integrity**
    -   **Supporting obfuscation**
    -   **Supporting authentication**
    -   **Supporting non-repudiation**
-   **Limitations**
    -   **Speed**
    -   **Size**
    -   **Weak keys**
    -   **Time**
    -   **Longevity**
    -   **Predictability**
    -   **Reuse**
    -   **Entropy**
    -   **Computational overheads**
    -   **Resource vs security constraints**

#### BlockChain Tech

-   **Blockchain**: _Blockchain is a decentralised, peer-to-peer system for secure interaction between buyer and seller.
    -   **Public ledgers**: _A peer to peer record/distributed database._

Verified transactions are added to a new block of data containing other recently verified transactions
	- A secure code (hash) is calculated from the previous blocks of transaction data in the blockchain and added to the new block of transactions.
	- So if anything on any of those blocks are changed the hash will change
	
