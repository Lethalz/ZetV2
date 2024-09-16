2408111106
	Status: #idea 
		Tags:  [[Practical TLS]] [[Cryptography]]



```table-of-contents
```

# Cryptography

[[Practical TLS]]
# Cryptography: A Deep Dive



## 1. Hashing

Hashing is a cryptographic process that takes an input (or 'message') and returns a fixed-size string of bytes, typically a digest that is unique to the input.

```ad-note
title: Hashing algorithim must satisfy 4 requirements

- Infeasible to produce a given digest
- impossible to extract original message
- Slight changes produce drastice differences (avalanche effecr)
- Resulting digest is fixed width(length)

```
Key Concepts:
1. One-way function: Easy to compute hash, computationally infeasible to reverse
2. Deterministic: Same input always produces the same hash
3. Avalanche effect: Small changes in input create significant changes in the hash
4. Collision resistance: Difficult to find two different inputs with the same hash

```ad-note
title: What are Collisions?
collapse: closed

Collisions are when two different messages result in identical digests, it is a byproduct of "fixed width(length) digests"
```

Common Hashing Algorithms:
- MD5, 128bits (deprecated due to vulnerabilities)
- SHA-1 160bits (deprecated)
- SHA-256, SHA-384, SHA-512 (SHA-2 family)
- SHA-3 family

```ad-warning
title: Hash Collisions
collapse: closed
icon: exclamation-triangle

MD5 and SHA-1 are vulnerable to collision attacks. Always use SHA-256 or stronger in production environments.
```

Use Cases:
- Password storage
- Data integrity checks
- Digital signatures
- Proof-of-work in blockchain

## 2. Data Integrity

Data integrity ensures that data has not been altered in an unauthorized manner since it was created, transmitted, or stored.

Methods to Ensure Data Integrity:
1. Hashing: Compute and verify hash of data
2. Message Authentication Codes (MACs): Combine a secret key with the message
3. Digital Signatures: Use asymmetric cryptography to sign data

HMAC (Hash-based Message Authentication Code){RFC 2104}:
- Combines a cryptographic hash function with a secret key
- Provides both data integrity and authenticity

```ad-tip
title: Order of Operations
If the sender of the digest creates the digest by key + message but the reciever does message + key the digest will not be the same. 

```
```ad-tip
title: HMAC vs Simple Hash
collapse: closed
icon: lightbulb

HMAC provides protection against length extension attacks, which simple hashing does not.
```
![[Pasted image 20240907200406.png]]
Use Cases:
- Verifying file downloads
- Ensuring message integrity in communications
- Tamper-evident logging

## 3. Encryption

Encryption is the process of encoding information in such a way that only authorized parties can access it.

Types of Encryption:
1. Symmetric Encryption: Same key for encryption and decryption
   - Examples: AES, DES, 3DES
   - Faster, but key distribution is challenging
   - Cipher text same size as plain-text
   - used for bulk-data

2. Asymmetric Encryption: Different keys for encryption and decryption
   - Examples: RSA, ECC
   - Slower, but solves key distribution problem
   - Cipher text bigger than plain-text
   - for smaller data sets

```ad-note
title: The Key Distribution Problem
collapse: closed
icon: key

The key distribution problem refers to the challenge of securely sharing secret keys between parties who want to communicate using symmetric encryption. 

Main issues:
1. Secure Channel: How to establish a secure channel to exchange keys?
2. Key Management: How to manage, store, and update keys for multiple parties?
3. Scalability: The number of required keys grows quadratically with the number of participants (n(n-1)/2 for n participants).

This problem is one of the main reasons for the development of asymmetric (public-key) cryptography, which addresses these issues by allowing secure communication without needing to share secret keys in advance.
Modes of Operation (for block ciphers):
- ECB (Electronic Codebook) - Not recommended for most uses
- CBC (Cipher Block Chaining)
- CTR (Counter)
- GCM (Galois/Counter Mode) - Provides both encryption and authentication
```

```ad-info
title: AES-GCM
collapse: closed
icon: shield-alt

AES-GCM is widely recommended for providing both confidentiality and integrity in a single operation.
```

## 4. Public and Private Keys

Asymmetric cryptography uses a pair of keys: public key (can be freely shared) and private key (must be kept secret).

Key Properties:
- Mathematically related, but computationally infeasible to derive one from the other
- What is encrypted with a public key can only be decrypted with the corresponding private key, and vice versa

Use Cases:
- Secure key exchange
- Digital signatures
- Email encryption (PGP)
- Secure web browsing (HTTPS) 
- Using the Asymmetric Keys to Encrypt Symmetric Keys

```ad-note 
title: Hybrid Encryption
collapse: Closed
	Cencept of using both Asymmetric and Symmetric Encryption
		Asymmetric Encryption to facilitate a Key Exchange
		Secret Key use with Symmetric Encryption for Bulk Data
	

```

Key Management:
- Secure generation of key pairs
- Safe storage of private keys
- Distribution of public keys
- Key rotation and revocation

```ad-note
title: But what about Signatures?
collapse: closed

signatures- using your private key to encrypt a message, so that anyone with your public key knows it was you who sent it.

The entire message can't be "encyrpted" with Private key
	Asymnmetric encryption has limitations
Could we sign a fixed, represenetational sample of the message?
	Hasing algorithm!
	
```

```ad-note
title: Process for Using an Asymmetric Key Pair for Digital Signatures
collapse: closed
icon: signature

1. Pam calculates a hash of the message.
2. Pam encrypts the resulting digest with her private key (signing).
3. Jim decrypts the signature with Pam's public key.
4. Jim calculates the hash of the received message.
5. Jim compares the decrypted hash with the calculated hash.

If both digests match, this proves two things:
- Integrity: The message hasn't changed since Pam signed it.
- Authentication: Only Pam could have created the signature.

Explanation:
- The matching hash proves the message integrity (hasn't been altered).
- The successful decryption using Pam's public key proves that Pam's private key was used to sign, authenticating Pam as the sender.

This process ensures both integrity and authentication of the message.

```


```ad-note
title: Key Takeaways

Hybrrid Encryption: 
- Use Asymmetric Encryption to securely establish Symmetric Keys
- Symmetric Keys can then be used with Symmetric Encrytpion to protect bulk data

Signatures:
- Uses the Sender's Private Key to encrypt the hash of a data
- Provvides Integrity and Authentication for what is Signed
```


## 5. How TLS and SSL Use Cryptography

TLS (Transport Layer Security) and its predecessor SSL use a combination of symmetric and asymmetric cryptography.


SSL and TLS have three main purposes:
1. Confidentiality(Encryption) - Data is only accessible by Client and server
2. Integrity(Hashing) - Data is not modified between Client and Server
3. Authentication(PKI) - Client/Server are indeed who they say they are

![[Pasted image 20240813095042.png]]

TLS Handshake Process:
1. Client Hello: Client sends supported cipher suites and random number
2. Server Hello: Server chooses cipher suite and sends certificate
3. Key Exchange: Often using Diffie-Hellman or RSA
4. Finished: Both sides derive session keys

Cert Authority Role 
1. CA is trusted by Client
2. CA will generate a Certificate
3. The CA links a particular set of Asymmetric keys to an Identity (Certificate)
4. This Cert is "signed" by the CA provides **Authentication**

Cryptographic Components in TLS:
- Asymmetric cryptography for key exchange and authentication
- Symmetric encryption for bulk data encryption
- MACs(Message Authentication Codes) for message integrity
- Digital signatures for server (and optionally client) authentication

```ad-warning
title: TLS Versions
collapse: closed
icon: exclamation-triangle

All SSL versions and TLS versions prior to 1.2 are considered insecure. Use TLS 1.2 or 1.3 in production.
```

![[Pasted image 20240813124757.png]]
## 6. Public Key Infrastructure (PKI)

PKI is a set of roles, policies, hardware, software, and procedures needed to create, manage, distribute, use, store, and revoke digital certificates.

Anytime you have a session that includes a client , server and CA you have a **public key infrastructure**.

3 Entities that form the PKI: Client , Server, Certificate Authority
	1. Client - needs to connect securely or verify an identity e.g web browsers
	2. Server - needs to prove its identity e.g Websites
	3. Certificate Authority - validate identities &  generates certificates e.g GoDaddy GlobalSign

Other Types of PKI:
1. Code Signing (client is the OS , software is the server, the CA is a code signing specific CA)
   ![[Pasted image 20240813131714.png]]
2. Internal Corporate PKI (Client -  Employees, Server- Corporate resources - HR portals, Ticketing systems,, etc, CA - Internal CA) ![[Pasted image 20240813132028.png]]



```ad-tip
title: Certificate Transparency
collapse: closed
icon: search

Certificate Transparency is a relatively new system for logging and monitoring certificate issuance, helping to detect misissued certificates quickly.
```

## 7. RSA (Rivest-Shamir-Adleman)

RSA is one of the first practical public-key cryptosystems, widely used for secure data transmission.

The most common Asymmetric Encryption algorithm.

Key Concepts:
1. Based on the practical difficulty of factoring the product of two large prime numbers
2. Public key consists of the modulus n and the public exponent e
3. Private key consists of the modulus n and the private exponent d

RSA Operations:
- Key Generation - Creates a pair of "commutative" keys
	- i.e "encrypt with one" "decrypt with the other"
- Encryption: c = m^e mod n
- Decryption: m = c^d mod n

c = Cipher Text 
m=message, E = public key  n = product of two prime numbers
d = private key 

![[Pasted image 20240813141005.png]]


Security Considerations:
- Key size: Minimum 2048 bits recommended
- Padding schemes: Use OAEP for encryption, PSS for signatures

Use Cases:
- Digital signatures
- Key exchange in TLS/SSL
- Email encryption

## 8. Diffie-Hellman Key Exchange

Diffie-Hellman (DH) is a method of securely exchanging cryptographic keys over a public channel. (Shared secret over an unsecure medium)

Key Concepts:
1. Based on the discrete logarithm problem
2. Allows two parties to jointly establish a shared secret over an insecure channel
3. Does not provide authentication by itself

Process:
1. Agree on public parameters (prime p and generator g)
2. Each party generates a private key and computes a public key
3. Exchange public keys
4. Each party computes the shared secret

![[Pasted image 20240813151133.png]]

- Established Shared Secret is then used to generate Symmetric keys
- Or HMAC keys for data integrity

![[Pasted image 20240813151634.png]]



```ad-warning
title: Man-in-the-Middle Attacks
collapse: closed
icon: user-secret

Diffie-Hellman is vulnerable to man-in-the-middle attacks without additional authentication. Always use authenticated Diffie-Hellman in practice.
```

## 9. Digital Signature Algorithm (DSA)

DSA is a Federal Information Processing Standard for digital signatures, based on the discrete logarithm problem. *Simply a signature algorithm*

Key Concepts:
1. Provides authenticity and non-repudiation
2. Faster for signing, slower for verification compared to RSA

Process:
1. Key Generation: Generate public key y and private key x
2. Signing: Compute r and s values based on the message hash and private key
3. Verification: Verify the signature using the public key


![[Pasted image 20240813153408.png]]

Random number is very important, must be unique for each message or DSA fails catastrophically.
If Random # is ever re-used, Private key can be extracted.

[RFC 6979 - generate random # deterministically based on message](https://datatracker.ietf.org/doc/html/rfc6979)

Use Cases:
- Code signing
- Document signing
- SSL/TLS certificates

```ad-info
title: DSA vs RSA
collapse: closed
icon: balance-scale

While DSA was specifically designed for digital signatures, RSA can be used for both encryption and signatures. ECDSA is generally preferred over DSA for its smaller key sizes and faster operations.
```


![[Pasted image 20240813155623.png]]






## Relevant RFCs

1. Hashing:
   - [RFC 1321 - The MD5 Message-Digest Algorithm](https://datatracker.ietf.org/doc/html/rfc1321)
   - [RFC 6234 - US Secure Hash Algorithms (SHA and SHA-based HMAC and HKDF)](https://datatracker.ietf.org/doc/html/rfc6234)

2. Data Integrity:
   - [RFC 2104 - HMAC: Keyed-Hashing for Message Authentication](https://datatracker.ietf.org/doc/html/rfc2104)

3. Encryption:
   - [RFC 3394 - Advanced Encryption Standard (AES) Key Wrap Algorithm](https://datatracker.ietf.org/doc/html/rfc3394)
   - [RFC 5288 - AES Galois Counter Mode (GCM) Cipher Suites for TLS](https://datatracker.ietf.org/doc/html/rfc5288)

4. Public and Private Keys:
   - [RFC 5280 - Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile](https://datatracker.ietf.org/doc/html/rfc5280)

5. TLS and SSL:
   - [RFC 8446 - The Transport Layer Security (TLS) Protocol Version 1.3](https://datatracker.ietf.org/doc/html/rfc8446)

6. Public Key Infrastructure:
   - [RFC 5280 - Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile](https://datatracker.ietf.org/doc/html/rfc5280)
   - [RFC 6960 - X.509 Internet Public Key Infrastructure Online Certificate Status Protocol - OCSP](https://datatracker.ietf.org/doc/html/rfc6960)

7. RSA:
   - [RFC 8017 - PKCS #1: RSA Cryptography Specifications Version 2.2](https://datatracker.ietf.org/doc/html/rfc8017)

8. Diffie-Hellman:
   - [RFC 7919 - Negotiated Finite Field Diffie-Hellman Ephemeral Parameters for Transport Layer Security (TLS)](https://datatracker.ietf.org/doc/html/rfc7919)

9. Digital Signature Algorithm:
   - [RFC 6979 - Deterministic Usage of the Digital Signature Algorithm (DSA) and Elliptic Curve Digital Signature Algorithm (ECDSA)](https://datatracker.ietf.org/doc/html/rfc6979)

```ad-tip
title: RFC Reading
collapse: closed
icon: book-reader

When reading RFCs, start with the Abstract and Introduction sections to get an overview. The "Requirements" sections often provide key insights into the protocol or algorithm's functionality.
```


## Conclusion

Cryptography forms the backbone of information security in the digital age. Understanding these core concepts and algorithms is crucial for anyone working in cybersecurity or developing secure systems. As the field evolves, new algorithms and techniques are continually being developed to address emerging threats and computational advances.

---
# Reference
[[Differences between DH and RSA]]


# Comprehensive Cryptography Quiz

1. What are the four requirements that a hashing algorithm must satisfy?
2. Why are MD5 and SHA-1 no longer recommended for use in production environments?
3. What is the main difference between symmetric and asymmetric encryption in terms of keys used?
4. Explain the concept of "Hybrid Encryption" and why it's useful.
5. What are the three main purposes of SSL and TLS?
6. In the context of Public Key Infrastructure (PKI), what role does a Certificate Authority (CA) play?
7. What is the key concept behind the security of RSA encryption?
8. Describe the basic process of the Diffie-Hellman key exchange.
9. What is the main vulnerability of Diffie-Hellman key exchange, and how is it typically addressed?
10. How does the Digital Signature Algorithm (DSA) differ from RSA in terms of functionality?
11. What are the three main entities that form a basic Public Key Infrastructure (PKI)?
12. Explain the concept of "Certificate Transparency" and its importance.
13. What is HMAC, and how does it differ from a simple hash?
14. In the context of TLS handshake, what is the purpose of the "Client Hello" and "Server Hello" messages?
15. What is the significance of key size in RSA, and what's the minimum recommended size for secure operations?

Bonus Question: 16. Explain the concept of "Perfect Forward Secrecy" and how it relates to key exchange protocols.




### Review Questions Answers



```ad-note
title: Quiz Answers
collapse: closed
icon: check-circle

1. The four requirements for a hashing algorithm are:
   - Infeasible to produce a given digest
   - Impossible to extract the original message
   - Slight changes produce drastic differences (avalanche effect)
   - Resulting digest is fixed width (length)

2. MD5 and SHA-1 are vulnerable to collision attacks, making them insecure for cryptographic purposes.

3. Symmetric encryption uses the same key for encryption and decryption, while asymmetric encryption uses a pair of keys (public and private).

4. Hybrid Encryption combines asymmetric and symmetric encryption. It uses asymmetric encryption to securely exchange a symmetric key, which is then used for bulk data encryption. This approach leverages the security of asymmetric encryption and the efficiency of symmetric encryption.

5. The three main purposes of SSL and TLS are:
   - Confidentiality (Encryption)
   - Integrity (Hashing)
   - Authentication (PKI)

6. A Certificate Authority (CA) validates identities and generates certificates, linking a particular set of asymmetric keys to an identity.

7. RSA's security is based on the practical difficulty of factoring the product of two large prime numbers.

8. Diffie-Hellman key exchange process:
   1. Agree on public parameters
   2. Each party generates a private key and computes a public key
   3. Exchange public keys
   4. Each party computes the shared secret

9. Diffie-Hellman is vulnerable to man-in-the-middle attacks. This is typically addressed by using authenticated Diffie-Hellman, which incorporates additional authentication measures.

10. DSA is specifically designed for digital signatures, while RSA can be used for both encryption and signatures.

11. The three main entities in a basic PKI are:
    - Client (e.g., web browsers)
    - Server (e.g., websites)
    - Certificate Authority (e.g., GoDaddy, GlobalSign)

12. Certificate Transparency is a system for logging and monitoring certificate issuance, helping to detect misissued certificates quickly, enhancing the overall security of PKI.

13. HMAC (Hash-based Message Authentication Code) combines a cryptographic hash function with a secret key. Unlike a simple hash, HMAC provides both data integrity and authenticity, and protects against length extension attacks.

14. In TLS handshake:
    - Client Hello: Client sends supported cipher suites and a random number
    - Server Hello: Server chooses a cipher suite and sends its certificate

15. For RSA, the minimum recommended key size is 2048 bits. Larger key sizes provide stronger security but may impact performance.

Bonus Answer:
16. Perfect Forward Secrecy ensures that if a long-term key is compromised, it doesn't compromise past session keys. It's typically achieved using ephemeral Diffie-Hellman key exchange, where a new set of keys is generated for each session.
```



