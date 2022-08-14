2208031833
	Status: #Exam
		Tags: [[Security+]] [[CyberSecurity]]

# Security+ Study Guide

# 1.0 Threats, Attacks, and Vulnerabilities

## 1.1 Compare and contrast different types of social engineering techniques.

- <u><em>Social engineering</em> is a big part of cybersecurity.</u> It often involves impersonation of some sort, attackers often use *impersonation* tactics, which are not easily countered via technology. It is important to understand that the best defense against this is user awareness and education. "Hacking People"
- Phishing combines technical deceit with the elements of traditional social engineering. Be sure sure to know the variants of phishing attacks. 
- **Know the differences between the different types of phishing attacks.**

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
> - Many organizations now prepend to the subject line some sort of notification if the email is external; this practice is known as prepending.

>[!note] Related:
>- Spearphishing – This type of phishing goes for a specific individual.
>- WhalePhishing (Whaling)—This is a targeted version of phishing, except for the size of the fish. Going after the CEO of a company instead of helpdesk.
>- Vishing - fake caller ID to appear as a trusted organization or vendor.
>-  Pharming - Redirects a user from a legitimate website to a fake one, usually done with DNS cache poisoning.
>- Smishing - SMS phishing. Phishing done over text.
>- SPIM (Spam over Internet Messaging) - The delivery of spam through the use of IM.











>[!attention]+ Misc.
> - Credential harvesting is a common goal of phishing campaigns that involves capturing usernames and passwords.
> - E.g In the form of a bogus email bank's website. From there, the attacker's goal would be to get you to input and submit your username and password.







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









## 1.2  Given a scenario, analyze potential indicators to determine the type of attack.

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

#### Rootkits
- A piece of software that can be installed and hidden on a computer mainly to fuck the system up and gain escalated privileges.
- Enables the attacker to gain root access to the victim's computer, which can compromise other machines on your network.
- Rootkits can be included as part of software packages, can be installed through an unpatched vulnerability, or downloaded.
- Many rootkits run in the background, you can usually spot one by looking in the memory processes, and checking programs.
- Kernel rootkits modify the kernel component of an operating system. Can intercept system calls passed to the kernel and can use encryption to protect outbound communications.
- Will piggyback on commonly used ports to communicate without interrupting other applications to stay hidden from administrators and detection tools.
- You can avoid a rootkit by **not having root privileges in the first place.**




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
- Known for heavy CPU use.
- E.GWannacry



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
Because s are the most common from of authentication and user access control is a password. So you can imagine that it is one of the first places attackers look to exploit.

Different types of Password attacks:
- Dictionary attack: Are the most succesful on simple passwords because the attack just tries each word from the supplied list. 
- **Brute force attack**: Relies on cryptanalysis or hashing algoriths that are capable of performing exhaustive key searches. Can crack short passwords more quickly than can dictionary attacks. **Account lockouts** are a way to mitigate these attacks. Although there are ways to brute-force offline. 
- ***Password spraying*** is a slow approach, it's using a single password attempt over multiple accounts.
- ***Rainbow table*** is a very large set of precomputed hash values for every possible combination of characters that is able to reverse a cryptography has function. 
- Birthday attack is a cryptographic method of attack against a secure hash. Finds collisions within hash functions and so is a more efficient method of brute-forcing one-way hashing. 
    - if 23 people are in a room, the probability that two of those people
have the same birthday is 50%
                 
                                                                                        earson, 2021.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
                                                                                \  

## 1.3 Given a scenario, analyze potential indicators associated with application attacks.

#### Privilege escalation

- This allows the attacker to gain higher-level access to their target's system, this usually is done by exploiting a vulnerability, a bug or a Zero-day exploit.
- With the newly gained access, the attacker has more capabilities or in other words, he expands his attack surface.
- Of course, these types of vulnerabilities are of the highest concern and have to be dealt with quickly.
- *Horizontal privilege escalation* is not gaining a higher privilege, but the privilege of another user.

> [!note] Solutions/Mitigations
> - Patch Quickly
> - Update anti-virus/anti-malware
> - Data execution prevention
> - Address space layout randomization 


#### Cross-site scripting

XSS or cross site scripting is one of the most common web app development errors.
It takes advantage of the trust a user has for a site and its complex and varied.
By placing a malicious client-side script on a website, an attacker can cause an unknowing browser user to conduct unauthorized access activities.
*Can be boiled down to a javascript injection between websites*

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
