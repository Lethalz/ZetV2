
 2409071253
	Status: #idea 
		Tags: 

# Cipher Suite


# Cipher Suites

## Fundamentals

A cipher suite is a combination of algorithms that help secure a network connection using SSL/TLS. It defines the specific protocols used for:

1. Authentication: Verifying the server's identity
2. Key Exchange: Securely establishing a shared secret
3. Encryption: Ensuring confidentiality of bulk data
4. Message Authentication Code (MAC): Providing data integrity

```ad-example
title: Cipher Suite Notation
collapse: closed
icon: code

TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384

This example specifies:
- Key Exchange: ECDHE (Elliptic Curve Diffie-Hellman Ephemeral)
- Authentication: RSA
- Encryption: AES-256 in GCM mode
- MAC: SHA-384 (used for key derivation in TLS 1.2)
```

![[Pasted image 20240907125316.png]]
## Key Exchange
![[Pasted image 20240908111514.png]]

Purpose: Establish a shared secret (seed value) to generate symmetric session keys.

### Key Exchange Methods:

1. PSK (Pre-Shared Key):
   - Seed value manually specified before TLS handshake
   - Considered least secure but requires zero overhead
   - Rare in web contexts, but making a comeback with IoT devices

2. RSA:
   - Client generates random seed value, encrypts with server's public key
   - Server decrypts with private key
   - Vulnerable if private key is compromised (no forward secrecy)

3. Diffie-Hellman Variants:
   - DH: Basic Diffie-Hellman
   - DHE: Ephemeral Diffie-Hellman
   - ECDH: Elliptic Curve Diffie-Hellman
   - ECDHE: Elliptic Curve Diffie-Hellman Ephemeral

```ad-info
title: Ephemeral vs. Static DH
collapse: closed
icon: info-circle

Ephemeral versions (DHE, ECDHE) generate new parameters for each session, providing forward secrecy. Static versions (DH, ECDH) use fixed parameters, which are less secure but slightly faster.
```

### Forward Secrecy

"Once encrypted, always encrypted" principle:
- Without forward secrecy (e.g., RSA), compromised private key can decrypt past communications
- With forward secrecy (DHE, ECDHE), each session uses unique parameters, protecting past sessions if the key is compromised

```ad-note
title: TLS 1.3 Requirement
collapse: closed
icon: lock

TLS 1.3 mandates forward secrecy, allowing only DHE and ECDHE key exchanges.
```



| Protocol | Security Level | Forward Secrecy | Recommendation |
|----------|----------------|-----------------|----------------|
| PSK      | Low            | No              | Avoid          |
| RSA      | Medium         | No              | Avoid          |
| DH       | Medium         | No              | Avoid          |
| ECDH     | High           | No              | Avoid          |
| DHE      | High           | Yes             | Accept         |
| ECDHE    | Very High      | Yes             | Prefer         |
| NULL     | None           | N/A             | Never Use      |

```ad-note
title: Key Size for DHE
collapse: closed
icon: key

For DHE, ensure key size is ≥ 2048 bits to be considered secure.
```



## Authentication
![[Pasted image 20240908111545.png]]

Purpose: Verify the server's identity (and optionally the client's).

Methods:
1. PSK: Pre-shared key, rare in web contexts
2. RSA: Widely supported, uses large key sizes
3. DSA (Digital Signature Algorithm):
   - Limited to 1024 bits in many implementations
   - Requires unique random numbers for each signature
   - Vulnerable if random number is reused
4. ECDSA (Elliptic Curve Digital Signature Algorithm):
   - More efficient than RSA at comparable security levels
   - Smaller key and signature sizes

```ad-tip
title: RSA vs. ECDSA
collapse: closed
icon: balance-scale

- RSA: More widely supported, larger keys
- ECDSA: More efficient, smaller keys and signatures
- Best practice: Support both for maximum compatibility and efficiency
```



| Protocol | Key Size (bits) | Security Level | Recommendation |
|----------|-----------------|----------------|----------------|
| PSK      | N/A             | Low            | Avoid          |
| DSS      | Any             | Low            | Avoid          |
| RSA      | < 2048          | Low            | Avoid          |
| RSA      | ≥ 2048          | High           | Accept         |
| ECDSA    | 256-384         | Very High      | Prefer         |
| EXPORT   | 40              | None           | Never Use      |







## Encryption
![[Pasted image 20240908111430.png]]

Symmetric encryption algorithms used to protect bulk data transfers.

### Types:

1. Stream Ciphers:
   - ChaCha20: Modern, efficient in software
   - RC4-128: Deprecated due to vulnerabilities

2. Block Ciphers:
   - AES (Advanced Encryption Standard): 128, 192, or 256-bit keys
   - 3DES (Triple DES): Older, less efficient
   - DES: Deprecated, insecure

### Block Cipher Modes:

- ECB (Electronic Codebook): Insecure, not used in TLS
- CBC (Cipher Block Chaining): Vulnerable to padding oracle attacks
- CTR (Counter): Turns block cipher into stream cipher
- GCM (Galois/Counter Mode): AEAD cipher, provides encryption and authentication

```ad-warning
title: AES Key Sizes
collapse: closed
icon: key

While AES-256 is theoretically more secure than AES-128, there's debate about its practical advantage. AES-128 is not considered insecure, and AES-256 requires more processing power.
```

### AEAD Ciphers

Authenticated Encryption with Associated Data:
- Provide both confidentiality and integrity in a single operation
- Examples: AES-GCM, ChaCha20-Poly1305
- Required in TLS 1.3



| Protocol    | Type   | Security Level | Recommendation |
|-------------|--------|----------------|----------------|
| DES         | Block  | Very Low       | Avoid          |
| RC4         | Stream | Low            | Avoid          |
| 3DES        | Block  | Low            | Avoid          |
| AES-CBC     | Block  | High*          | Accept         |
| AES-GCM     | AEAD   | Very High      | Prefer         |
| ChaCha20    | AEAD   | Very High      | Prefer         |
| NULL        | N/A    | None           | Never Use      |

```ad-warning
title: AES-CBC Security
collapse: closed
icon: exclamation-triangle

*AES-CBC is considered secure only with TLS 1.1 or greater, which protects against padding oracle attacks.
```





## Hashing (for MAC)

![[Pasted image 20240908111448.png]]

Purpose: Provide data integrity and authentication for bulk data.

Common Algorithms:
1. MD5: 128-bit digest, considered insecure
2. SHA-1: 160-bit digest, deprecated for digital signatures
3. SHA-256, SHA-384 (SHA-2 family): Considered secure
4. Poly1305: Used with ChaCha20, efficient in software

```ad-info
title: HMAC
collapse: closed
icon: shield-alt

HMAC (Hash-based Message Authentication Code) is a specific type of MAC that uses a cryptographic hash function combined with a secret key. It's more resilient to certain types of attacks compared to using the hash function directly.
```

## TLS 1.3 Changes

Major changes in TLS 1.3 affecting cipher suites:
1. Removed support for insecure algorithms (MD5, SHA-1, RC4, DES, 3DES)
2. Mandated forward secrecy (only DHE and ECDHE allowed)
3. Required AEAD ciphers
4. Simplified cipher suite notation (removed redundant information)

## Choosing a Cipher Suite

Considerations:
1. Security: Use the strongest algorithms available
2. Compatibility: Ensure support across target systems
3. Performance: Balance security with computational overhead
4. Compliance: Meet regulatory requirements

```ad-tip
title: Best Practices
collapse: closed
icon: star

1. Prefer ECDHE over DHE for key exchange
2. Use RSA or ECDSA for authentication (ECDSA preferred where supported)
3. Choose AES-GCM or ChaCha20-Poly1305 for encryption
4. For hashing/MAC, use SHA-256 or higher
5. Enable forward secrecy
6. Stay updated with the latest security recommendations and vulnerabilities
```

# Cipher Suite Recommendations: Avoid, Accept, Prefer

## Key Exchange Protocols

### Avoid
- PSK (Pre-Shared Key)
- RSA
- DH (Diffie-Hellman)
- ECDH (Elliptic Curve Diffie-Hellman)

```ad-warning
title: Lack of Forward Secrecy
collapse: closed
icon: exclamation-triangle

These methods do not provide forward secrecy, making past communications vulnerable if the private key is compromised.
```

### Accept
- DHE (Diffie-Hellman Ephemeral)
  - Key size >= 2048 bits

### Prefer
- ECDHE (Elliptic Curve Diffie-Hellman Ephemeral)

```ad-tip
title: Forward Secrecy
collapse: closed
icon: shield-alt

ECDHE provides forward secrecy and is generally more efficient than DHE.
```

### Avoid at All Costs
- NULL (No key exchange)

```ad-danger
title: NULL Key Exchange
collapse: closed
icon: ban

NULL provides no key exchange, confidentiality, or integrity. Never use in production environments.
```

## Authentication Protocols

### Avoid
- PSK
- DSS (Digital Signature Standard)
- RSA < 2048 bits

### Accept
- RSA >= 2048 bits

### Prefer
- ECDSA (Elliptic Curve Digital Signature Algorithm)

```ad-info
title: RSA and ECDSA Configuration
collapse: closed
icon: info-circle

You can configure both RSA and ECDSA for better compatibility. Use ECDSA when supported, falling back to RSA when necessary.
```

### Avoid at All Costs
- EXPORT grade encryption

```ad-danger
title: EXPORT Grade Encryption
collapse: closed
icon: history

EXPORT grade limits encryption key size to 40 bits. It's a relic from old U.S. export restrictions and is extremely insecure.
```

## Encryption Protocols

### Avoid
- DES (Data Encryption Standard)
- RC4 (Rivest Cipher 4)
- 3DES (Triple DES)

### Accept
- AES-CBC (Advanced Encryption Standard - Cipher Block Chaining)
  - Only with TLS 1.1 or greater (protects against padding oracle attacks)

### Prefer
- AES-GCM (AES - Galois/Counter Mode)
- ChaCha20

```ad-tip
title: AEAD Ciphers
collapse: closed
icon: lock

AES-GCM and ChaCha20 are AEAD (Authenticated Encryption with Associated Data) ciphers, providing both confidentiality and integrity. These are considered the future of secure communication.
```

### Avoid at All Costs
- NULL (No encryption)

## Hashing Algorithms (for MAC)

### Avoid
- MD5 (Message Digest 5)

### Accept
- SHA (Secure Hash Algorithm)
  - Note: SHA-HMAC for data integrity is still considered secure
  - SHA for signatures is considered insecure

### Prefer
- SHA-256
- SHA-384
- Poly1305

```ad-tip
title: AEAD Preference
collapse: closed
icon: star

When using AEAD ciphers, prefer the associated MAC:
- With AES-GCM, use SHA-256 or SHA-384
- With ChaCha20, use Poly1305
```



| Algorithm | Digest Size (bits) | Security Level | Recommendation |
|-----------|-------------------|----------------|----------------|
| MD5       | 128               | Very Low       | Avoid          |
| SHA-1     | 160               | Low            | Avoid for signatures, Accept for HMAC |
| SHA-256   | 256               | High           | Prefer         |
| SHA-384   | 384               | Very High      | Prefer         |
| Poly1305  | 128               | High           | Prefer (with ChaCha20) |


## General Recommendations

1. Always prioritize forward secrecy in key exchange.
2. Use strong authentication with key sizes of at least 2048 bits for RSA.
3. Prefer AEAD ciphers for encryption.
4. Use SHA-256 or stronger for hashing/MAC operations.
5. Regularly update cipher suite preferences based on the latest security research and recommendations.

```ad-warning
title: Future-Proofing
collapse: closed
icon: clock

Cryptographic standards evolve. What is considered secure today may be vulnerable in the future. Always stay informed about the latest developments in cryptography and adjust your cipher suite preferences accordingly.
```


| Key Exchange | Authentication | Encryption | MAC     | Overall Recommendation |
|--------------|----------------|------------|---------|------------------------|
| ECDHE        | ECDSA          | AES-GCM    | SHA-384 | Excellent              |
| ECDHE        | RSA (≥2048)    | AES-GCM    | SHA-256 | Very Good              |
| DHE          | RSA (≥2048)    | AES-CBC    | SHA-256 | Good                   |
| RSA          | RSA (≥2048)    | AES-CBC    | SHA-1   | Acceptable             |
| DH           | DSS            | 3DES       | MD5     | Poor (Avoid)           |

```ad-tip
title: Cipher Suite Selection
collapse: closed
icon: lightbulb

When selecting cipher suites, prioritize those with:
1. Forward secrecy (ECDHE or DHE)
2. Strong authentication (ECDSA or RSA ≥2048 bits)
3. AEAD ciphers (AES-GCM or ChaCha20)
4. Strong hash functions (SHA-256 or higher)
```







---
# Reference




![[Pasted image 20240907202031.png]]

