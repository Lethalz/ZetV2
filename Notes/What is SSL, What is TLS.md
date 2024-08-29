2408081250
	Status: #idea 
		Tags: [[Practical TLS]] 

# What is SSL, What is TLS

[[Practical TLS]]
# SSL (Secure Sockets Layer) and TLS (Transport Layer Security)


## Fundamentals

SSL/TLS create a secure, protected tunnel across the internet. 
- Lets the client and server send and share information safely across the internet.
- SSL/TLS can also protect other data transfers (SSL VPN)
- HTTPS is HTTP protected by SSL

We need some way to protect our data going over the wire or else everyone's data would be under attack constantly.

### SSL (Secure Sockets Layer)


SSL is a cryptographic protocol designed to provide secure communication over a computer network. It was the predecessor to TLS.

Key Points:
1. Developed by Netscape in 1995, IETF renamed this protocol TLS
2. Provides encryption, authentication, and integrity
3. Operates between the Application and Transport layers
4. All versions are now considered deprecated and insecure

### TLS (Transport Layer Security)

TLS is the successor to SSL, providing improved security and performance.

Key Points:
1. First version (TLS 1.0) released in 1999
2. Current version is TLS 1.3 (as of 2021)
3. Provides the same core functionality as SSL, but with stronger algorithms and more robust handshake process
4. Widely used for securing web browsing (HTTPS), email, instant messaging, and VoIP

```ad-info
title: SSL vs TLS Naming Convention
collapse: closed
icon: info-circle

Despite TLS replacing SSL, many people still use the term "SSL" when actually referring to TLS. In technical contexts, it's important to use the correct terminology.
```



## Key Differences Between SSL and TLS

1. Security: TLS offers stronger encryption algorithms and more secure handshake processes.
2. Handshake Process: TLS has a more robust handshake process, reducing the number of round trips required.
3. Message Authentication: TLS uses HMAC for message authentication, while SSL uses MAC.
4. Alert Protocol: TLS has a more extensive alert protocol for indicating errors.
5. Record Protocol: TLS has an improved record protocol structure.

```ad-warning
title: SSL Vulnerability
collapse: closed
icon: exclamation-triangle

All versions of SSL are considered vulnerable to various attacks, including POODLE and BEAST. It's crucial to use TLS in all production environments.
```

## How does SSL/TLS Protect Your Data?

Data sent across a wire can be captured by anyone in the middle, which leave cleartext data susceptible to hijacking.

SSL/TLS was created to protect this data in 3 ways (CIA):
**Confidentiality**- Data is only accessible be client and server  (*Encryption*)
**Integrity**- Data is not modified between client and server (*Hashing*)
**Authentication**- client/Server are indeed who they say they are. (*PKI)*

To truly understand SSL/TLS, you need to understand all three parts.


## Anti-replay and Non-repudiation

Anti-replay 
- Adds a sequence number that increments for every message sent by SSL/TLS
- Built into the integrity and Authentication mechanism

Non-repudiation
- Repudiate - refusing to have anything to do with something

	Makes it so that once a message is sent, the sender cannot later deny having sent that message.
	 If the data has integrity and authentication then non-repudiation is inherit in SSL and TLS



## Key Players

SSL/TLS ecosystem involves three key players
	Client
	 Server
	 Certificate Authority (CA)

Client - Entity initiating the TLS Handshake
- When we say client we don't necessarily mean the users but the software that will make the request 
- Web Browser Chrome Safari
- Phones, apps , smart toaster, IOT
- If its going to connect to the internet securely it is going to need to be a SSL Client
- Optionally authenticated (rare)

Server - Entity receiving the TLS Handshake 
- Web Server
	- Apache, IIS, NginX, etc
	- Load Balancer or SSL Accelerator
	- Always Authenticated

There is a way to have both sides authenticate all the time and thats called mutual SSL/TLS


Certificate Authority
- Governing Entity that issues Certificates 
- Trusted by client ad server
- provides trust anchor
	- if we trust the ca we trust what the ca trusts
- Five orgs secure 98% of the internet:
![[Pasted image 20240809112532.png]]







 
## Evolution from SSL to TLS

1. SSL 1.0 - Never publicly released due to security flaws
2. SSL 2.0 - Released in 1995, deprecated in 2011
3. SSL 3.0 - Released in 1996, deprecated in 2015
4. TLS 1.0 - Released in 1999, deprecated in 2020
5. TLS 1.1 - Released in 2006, deprecated in 2020
6. TLS 1.2 - Released in 2008, widely used
7. TLS 1.3 - Released in 2018, current standard

```ad-note
title:Security vs Accessibility 

You might want to just use the newest version of ssl/tls but you need to take other factors into account. What if you have older devices connecting to your server that arent compatible with newer TLS versions?

```

## Version Changes

Here's a concise overview of SSL/TLS versions with key points and upgrades:

1. SSL 1.0 (Deprecated)
   • Never publicly released
   • Contained significant security flaws
   • Developed by Netscape

2. SSL 2.0 (Deprecated)
   • First publicly released version
   • Vulnerable to downgrade attacks
   • Introduced the SSL handshake process

3. SSL 3.0 (Deprecated)
   • Completely redesigned from SSL 2.0
   • Vulnerable to POODLE attack
   • Introduced support for Fortezza cipher suites

4. TLS 1.0 (Deprecated) (secure-ish)
   • Based on SSL 3.0 with minor differences
   • Vulnerable to BEAST attack (Cipher Block Chaining Vulnerability)
   • Introduced HMAC for message authentication

5. TLS 1.1(Deprecated) (secure-ish)
   • Added protection against CBC attacks
   • Introduced explicit IV for CBC mode ciphers
   -  Formally Deprecated EXPORT based ciphers
   • Improved handling of padding errors

6. TLS 1.2 (secure)
   • Allows negotiation of hash and signature algorithms
   • Supports AEAD ( Authenticated Encryption with Associated Data) cipher modes (e.g., GCM)
   • Removed support for weak hash functions (MD5/SHA-1)

7. TLS 1.3 (secure)
   • Reduced handshake latency (1-RTT, 0-RTT)
   • Removed support for obsolete and insecure features
   - Required Forward Secrecy
   - AEAD Required
   • Introduced encrypted handshake messages


## Related RFCs

1. [RFC 8446 - The Transport Layer Security (TLS) Protocol Version 1.3](https://datatracker.ietf.org/doc/html/rfc8446)
2. [RFC 5246 - The Transport Layer Security (TLS) Protocol Version 1.2](https://datatracker.ietf.org/doc/html/rfc5246)
3. [RFC 6101 - The Secure Sockets Layer (SSL) Protocol Version 3.0](https://datatracker.ietf.org/doc/html/rfc6101)

## Industry Standards and Best Practices

1. [NIST SP 800-52 Rev. 2 - Guidelines for the Selection, Configuration, and Use of Transport Layer Security (TLS) Implementations](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-52r2.pdf)
2. [Mozilla SSL Configuration Generator](https://ssl-config.mozilla.org/)


```ad-warning
title: Ongoing Vigilance
collapse: closed
icon: shield-alt

Cryptographic standards continue to evolve. Stay informed about new vulnerabilities and updates to ensure your implementations remain secure.
```
---
# Reference



## Comprehensive SSL/TLS Quiz

1. What is the primary purpose of SSL/TLS?

2. What are the three main ways SSL/TLS protects data (CIA)?

3. What is the current version of TLS, and when was it released?

4. Name two key differences between SSL and TLS.

5. Why is it crucial to use TLS instead of SSL in production environments?

6. What are the three key players in the SSL/TLS ecosystem?

7. What does "mutual SSL/TLS" refer to?

8. What is the significance of the "Certificate Authority" in SSL/TLS?

9. What two additional security features does SSL/TLS provide beyond CIA?

10. In the evolution of SSL/TLS, which versions are considered "secure-ish" and which are considered "secure"?

11. What major improvements were introduced in TLS 1.3?

12. What is the POODLE attack, and which version of SSL/TLS is vulnerable to it?

13. What does AEAD stand for in the context of TLS 1.2?

14. Why might an organization choose to support older versions of TLS despite security concerns?

15. What is Forward Secrecy, and in which TLS version did it become required?

```ad-note
title: Quiz Answers
collapse: closed
icon: check-circle

1. SSL/TLS creates a secure, protected tunnel across the internet, allowing clients and servers to send and share information safely.

2. The three main ways (CIA) are:
   - Confidentiality (Encryption)
   - Integrity (Hashing)
   - Authentication (PKI)

3. The current version is TLS 1.3, released in 2018.

4. Two key differences (any two of these):
   - TLS offers stronger encryption algorithms
   - TLS has a more robust handshake process
   - TLS uses HMAC for message authentication, while SSL uses MAC
   - TLS has a more extensive alert protocol
   - TLS has an improved record protocol structure

5. All versions of SSL are considered vulnerable to various attacks, including POODLE and BEAST.

6. The three key players are:
   - Client
   - Server
   - Certificate Authority (CA)

7. Mutual SSL/TLS refers to when both the client and server authenticate each other.

8. The Certificate Authority provides a trust anchor. If we trust the CA, we trust what the CA trusts.

9. The two additional features are:
   - Anti-replay
   - Non-repudiation

10. TLS 1.0 and 1.1 are considered "secure-ish", while TLS 1.2 and 1.3 are considered "secure".

11. Major improvements in TLS 1.3 include:
    - Reduced handshake latency (1-RTT, 0-RTT)
    - Removed support for obsolete and insecure features
    - Required Forward Secrecy
    - AEAD Required
    - Introduced encrypted handshake messages

12. The POODLE attack affects SSL 3.0.

13. AEAD stands for Authenticated Encryption with Associated Data.

14. Organizations might support older versions for compatibility with older devices that aren't compatible with newer TLS versions.

15. Forward Secrecy ensures that if a long-term key is compromised, it doesn't compromise past session keys. It became required in TLS 1.3.
```