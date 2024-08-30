2408140918
	Status: #idea 
		Tags: [[Practical TLS]] [[Cryptography]]  

# x509 Certificates and Keys

[[Practical TLS]]
## Overview of the SSL Process


1. CA is the cornerstone of the TLS/SSL Process
		1. CA has a public key and a private key
		2. CA has a self-signed certificate
2. Server wants to acquire a Certificate
3. Server generates a public key and a private key
4. Server generates a CSR(Certificate Signing Request) - the file you submit to a CA to apply for a Certificate.
		1. CSR contains Server's Public Key
		2. CSR is signed by Server's Private key
5. Server gives signed CSR to Certificate Authority
6. CA inspects and validates information is CSR
7. CA creates certificate using information from CSR
8. CA signs Certificate using CA's Private Key
9. CA give certificate to Server
10. Server can then provide certificate to prove its identity

```ad-note
title: What is a Signature?
icon: lightbulb
collapse: closed


The sender takes the entire message to be sent and create a digest.
	Digest is the output of a hashing algorithm
The sender then takes their private key and encrypts the digest.
The receiver then uses the senders public key to decrypt the signature and cross-references if the message outputs the same digest as the signature's digest.

```
## What is in a Certificate?

#### X.509 Certificate Contents

X.509 is a standard format for public key certificates, widely used in various internet protocols, including TLS/SSL (Transport Layer Security/Secure Sockets Layer).'


###### 3 Sections of a Certificate

1. **Certificate Data** - Version #, Serial Number, signature algorithm, etc
2. **Signature Algorithm** - The type of Hashing Algorithm that was used in the below step is specified here.
3. **Signature** - the CA takes all the information data put it through a hashing algorithm and encrypt it with their private key to sign the cert.

[[What's in a Certificate Diagram]]

##### Key Components of an X.509 Certificate:

1. **Version Number**: Indicates the X.509 version (v1(0x0), v2(0x1), or v3(0x2))  {not to be confused with SSL/TLS Version}
	1. v3 Adds Certificate Extensions
		1. Optional fields that add features to SSL/TLS Certificates
2. **Serial Number:** Unique identifier assigned by the Certificate Authority (CA)
	1. 20 bytes (160 bits)
	2. Uniquely identifies a Certificate issued by a given CA
		1. Every cert is issued by Orange CA has unique serial number
		2. Every cert issued by Purple CA has a unique serial number
		3. Serial Numbers can be identical between Orange CA and Purple CA (because the SN is just the identifier for this particular certificate for a CA)
	3. Used to look-up the validity of a certificate
		1. Request is made to the CA which issued Cart by Serial number
			1. CRL - Certificate Revocation List
			2. OCSP - Online Certificate Status Protocol
3. **Signature Algorithm ID**: Hashing Algorithm that was used to Hash Certificate Data and Algorithm used by the CA to sign the certificate.
4. **Issuer Name**: Identity of the CA that issued the certificate
5. **Validity Period**: Duration a Cert is calid for
   - Not Before: Start date of certificate validity
   - Not After: Expiration date of certificate
6. **Subject Name**: Identity of the entity the certificate is issued to (What the Cert is trying to Identify)
7. **Subject Public Key Info**:
   - Public Key Algorithm
   - Subject Public Key
	   - RSA -Modulus(product) and Exponent (public key)
	   - Elliptic Curve - pubic key, Curve
1. **Issuer** Unique Identifier (optional) (CA that issued the certificate) 
2. **Subject Unique Identifier** (optional)
3. **Extensions** (X.509 v3 only):
    - Key Usage
    - Extended Key Usage
    - Subject Alternative Name
    - Basic Constraints

```ad-info
title: Certificate Fields and Their Purposes
collapse: closed
icon: id-card

- Serial Number & Issuer: Together uniquely identify the certificate
- Subject Name: Typically includes Common Name (CN), which for web servers is usually the domain name
- Public Key: The actual public key being certified
- Signature: The CA's digital signature, verifying the certificate's authenticity
```

```ad-attention
title: Self-signed CA certificate
collapse: closed

Certificate Authorites also have their own Certificates
	CAs issue their own Certificates
	Subject: CA 1
	Issuer: CA 1
```

### Subject and issuer are specified in Distinguished Name (DN) format:
![[Pasted image 20240814112646.png]]

![[Pasted image 20240814112720.png]]

#### Common Name (CN)

- Every certificate must have one Common Name
- Browsers verify CN against URL in address bar
- CN can include a wildcard(\*) which allows a single CN to cover a single subdomain

![[Pasted image 20240814113919.png]]

Notice it covers www.google.com but not google.com, the wildcard makes it so there has to be something before .google.com.

![[Pasted image 20240814114130.png]]





#### Related RFC:

[RFC 5280 - Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile](https://datatracker.ietf.org/doc/html/rfc5280)

[RFC 4519 - Lightweight Directory Access Protocol (LDAP): Schema for User Applications](https://www.rfc-editor.org/info/rfc4519)- Common Names

```ad-note
title: Is common name and Canonical name the same?
collapse: closed
No, Common Name and Canonical Name are not the same, although they are related concepts in the context of networking and digital certificates. Let me explain the differences:

1. Common Name (CN):
    - Used in X.509 digital certificates
    - Typically represents the server name protected by the SSL certificate
    - For websites, it's usually the domain name
    - In older SSL certificates, it was limited to a single domain
2. Canonical Name (CNAME):
    - Used in DNS (Domain Name System)
    - A type of DNS record that maps an alias name to a true or canonical domain name
    - Used to create aliases for domain names

Key Differences:

1. Context:
    - CN is used in SSL/TLS certificates
    - CNAME is used in DNS records
2. Purpose:
    - CN identifies a specific entity (like a website) in a certificate
    - CNAME creates an alias for a domain name
3. Structure:
    - CN is part of the certificate's subject field
    - CNAME is a type of DNS record
4. Usage:
    - CN is checked during SSL/TLS handshake for certificate validation
    - CNAME is used for domain name resolution and redirection
5. Flexibility:
    - Modern certificates use Subject Alternative Name (SAN) instead of CN for multiple domains
    - CNAME can point to another CNAME, creating a chain (though this is not recommended)

Example:

- A certificate might have a CN of "[www.example.com](http://www.example.com)"
- A CNAME record might map "mail.example.com" to "example-com.mail.protection.outlook.com"

```


## Certificate Extensions


# X.509 Certificate Extensions

Certificate extensions are additional fields in X.509 certificates that provide extra information and constraints on the certificate's usage.

## Nine Prevalent Certificate Extensions:

1. Key Usage:
   - Purpose: Defines the intended use of the public key in the certificate
   - Examples: Digital signature, key encipherment, certificate signing

2. Extended Key Usage:
   - Purpose: Specifies additional purposes for which the certified public key may be used
	   - Limits by Protocol and/or Role
   - Examples: TLS (Transport Layer Security) Web server authentication, email protection

```ad-note
title: Importance of Limiting Key Usage
collapse: closed
icon: shield-alt

Limiting key usage through extensions like Key Usage and Extended Key Usage is crucial for security:

1. Damage Control: If a certificate is compromised, the potential damage is limited to its specified uses. For example, a compromised SSL/TLS server certificate can't be used for code signing if its usage is properly restricted.

2. Principle of Least Privilege: By specifying exact uses, we adhere to the principle of granting only the permissions necessary for the task at hand.

3. Preventing Misuse: It stops accidental misuse of certificates for unintended purposes, reducing the risk of security vulnerabilities.

4. Compliance: Many regulatory standards require specific key usage limitations for different types of certificates.

5. Trust Model Integrity: It maintains the integrity of the PKI (Public Key Infrastructure) trust model by ensuring certificates are used as intended by the issuing CA (Certificate Authority).

Remember: Properly limited key usage significantly reduces the "failure domain" if a certificate is compromised, containing potential security breaches to a smaller, more manageable scope.
```
3. Basic Constraints:
   - Purpose: Indicates if the subject is a CA (Certificate Authority) and the maximum depth of certification path
   - Key fields: CA (true/false), Path Length Constraint

```ad-note
title: Understanding Basic Constraints
collapse: closed
icon: sitemap

Key points about the Basic Constraints extension:

1. CA Flag: 
   - When set to TRUE, it indicates that the certificate can be used to sign other certificates.
   - Critical for preventing end-entity certificates from being misused as CAs.

2. Path Length:
   - Limits the number of intermediate CAs allowed in a certificate chain.
   - A value of 0 means the CA can only issue end-entity certificates, not intermediate CA certificates.
   - If absent, there's no limit on the certification path length.

3. Security Implications:
   - Properly set Basic Constraints are crucial for maintaining the PKI hierarchy.
   - Misconfiguration could lead to unauthorized certificate issuance or excessively long certificate chains.

4. Processing Rules:
   - Typically marked as a critical extension.
   - Certificate-using systems MUST reject the certificate if it's marked as a CA but doesn't have Basic Constraints or if the CA flag is FALSE.

Remember: Correct configuration of Basic Constraints is essential for maintaining the security and integrity of the entire PKI ecosystem.
```

4. Name Constraints:
   - Purpose: Limits the names that can be issued in subsequent certificates in a certification path
	   - Limits CA signing to specific domain
	   - typically internal corp CA
   - Types: Permitted subtrees, Excluded subtrees

5. Subject Key Identifier:
   - Purpose: Provides a means of identifying certificates containing a particular public key
   - Usually: A hash of the public key

6. Authority Key Identifier:
   - Purpose: Identifies the public key corresponding to the private key used to sign a certificate
   - Helps in building certification paths

```ad-note
title: Subject Key Identifier and Authority Key Identifier
collapse: closed
icon: key

These two extensions play crucial roles in certificate management and verification:

1. Subject Key Identifier:
   - Provides a unique identifier for the public key contained in the certificate.
   - Allows tracking of keys across certificates:
     * Certificates expire and get renewed with new serial numbers.
     * Renewing a certificate doesn't require creating new asymmetric keys.
   - Enables efficient certificate management, especially during key rollovers.

2. Authority Key Identifier:
   - Identifies the key which signed the certificate.
   - Particularly useful because:
     * CAs often have multiple key pairs.
     * CAs rotate through their keys when issuing certificates.
   - Facilitates building of certification paths in complex PKI environments.

3. Relationship:
   - The Subject Key Identifier in a CA certificate corresponds to the Authority Key Identifier in certificates it issues.
   - This linkage simplifies certificate chain validation and helps in quickly identifying the correct issuer certificate.

Remember: These extensions are critical for efficient PKI operations, especially in environments with frequent certificate renewals or multiple CA keys.
```



7. Subject Alternative Name (SAN):
   - Purpose: Allows identities to be bound to the subject of the certificate
	   - Allows one certificate to protect multiple domains
	   - [[x509 Certificates and Keys#Common Name (CN) | Wildcard Certs]] allows multiple sub-domains for single domain.
	   - S.A.N allows multiple whole domains.
   - Examples: DNS names, IP addresses, email addresses

8. CRL (Certificate Revocation List) Distribution Points:
   - Purpose: Indicates how CRL information is obtained
	   - List of Revoked certificates 
	   - Maintained by CA
   - Usually contains URLs where the CRL can be downloaded

9. Authority Information Access:
   - Purpose: Indicates how to access CA information and services
	   - Provides a place for CAs to provide information for whoever might be using the certificate that they issue.
   - Key fields:
     - CA Issuers: Where to find certificates of the issuing CA
     - OCSP (Online Certificate Status Protocol) location: Where to check certificate validity status

```ad-info
title: Extension Criticality
collapse: closed
icon: exclamation-circle

Extensions can be marked as "critical" or "non-critical". If an extension is marked critical, the certificate must be rejected if the extension cannot be processed or understood. Non-critical extensions can be ignored if not recognized.
```

## Related RFC:

[RFC 5280 - Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile](https://datatracker.ietf.org/doc/html/rfc5280)
   

## What is in a Private Key?

# What is IN a Private Key


## Contents of Private Keys

The contents of a private key depend on the cryptographic algorithm being used. Here are the contents for some common algorithms:

Bunch of values used in Asymmetric math. [[Cryptography#7. RSA (Rivest-Shamir-Adleman) | RSA Math Example]]

```ad-note
title: How to find out what key matches to what Cert
collapse: closed

If the modulus in the private key file matches with the modulus of the cert file you know you have a match.

![[Pasted image 20240827145903.png]]
```
### RSA (Rivest-Shamir-Adleman) Private Key

An RSA private key contains:

1. p and q: Two large prime numbers
2. n: The modulus (n = p * q)
3. d: The private exponent
4. e: The public exponent (usually a small number like 65537)
5. Additional values for optimization:
   - dp: d mod (p-1)
   - dq: d mod (q-1)
   - qinv: q^(-1) mod p

```ad-info
title: RSA Key Format
collapse: closed
icon: file-code

RSA private keys are often stored in PKCS#1 or PKCS#8 format, which include additional metadata along with these numerical values.
```

### ECC (Elliptic Curve Cryptography) Private Key

An ECC private key is simpler and contains:

1. d: A random integer between 1 and the order of the curve
2. Information about the specific elliptic curve being used

### DSA (Digital Signature Algorithm) Private Key

A DSA private key contains:

1. p: A large prime modulus
2. q: A prime divisor of p-1
3. g: A generator of order q in the multiplicative group of integers modulo p
4. x: The private key (a random integer less than q)
5. y: The public key (y = g^x mod p)

```ad-warning
title: Key Security
collapse: closed
icon: lock

Regardless of the algorithm, the numerical values in a private key must be kept strictly confidential. Exposure of these values compromises the security of the cryptosystem.
```

## Private Key Formats

Private keys are typically stored in standardized formats:

1. PEM (Privacy Enhanced Mail): Base64 encoded DER certificate, enclosed between "-----BEGIN PRIVATE KEY-----" and "-----END PRIVATE KEY-----"
2. DER (Distinguished Encoding Rules): Binary format
3. PKCS#8: A standard syntax for storing private key information

## Related RFCs

- [RFC 3447 - Public-Key Cryptography Standards (PKCS) #1: RSA Cryptography Specifications Version 2.1](https://datatracker.ietf.org/doc/html/rfc3447)
- [RFC 5915 - Elliptic Curve Private Key Structure](https://datatracker.ietf.org/doc/html/rfc5915)
- [RFC 6979 - Deterministic Usage of the Digital Signature Algorithm (DSA) and Elliptic Curve Digital Signature Algorithm (ECDSA)](https://datatracker.ietf.org/doc/html/rfc6979)





# What's in a CSR (Certificate Signing Request)

## Structure of a CSR

A CSR consists of three main sections:
1. Certificate Request Information
2. Signature Algorithm
3. Signature

## Certificate Request Information

This section contains:
1. Version
2. Subject Distinguished Name (DN)
3. Public Key
4. Attributes

### Version
- Value: 0x0
- Meaning: CSR version 1
- Note: This is currently the only version in use

### Subject Distinguished Name (DN)
- Contains the subject's distinguished name
- Imported by the CA into the certificate
- CA adds its own DN as the certificate's issuer field

### Public Key
- Presented as two values: modulus and exponent
- Includes the algorithm used

### Attributes
- Optional additional CSR features
- Common attributes include:
  1. Extension Requests
  2. Challenge Password

```ad-info
title: Extension Requests
collapse: closed
icon: puzzle-piece

- Where the server adds requests for specific extensions for the ensuing certificate
- Examples: Subject Key Identifier, Subject Alternative Name (SAN)
```

```ad-info
title: Challenge Password
collapse: closed
icon: key

- Used when requesting admin action from CA
- Limits who can ask CA to revoke the certificate
- Legacy: Now often replaced by web portals for certificate management
```

- Note: `a:00` indicates when the CSR contains 0 attributes

## CSR Process

1. Server Creation: The server creates the CSR
2. Signing: The server signs the CSR (not the CA)
3. Submission: CSR is submitted to the CA
4. CA Processing:
   - CA imports subject information
   - CA adds its own DN as the certificate issuer
   - CA processes extension requests
5. Certificate Issuance: CA issues the certificate based on the CSR

```ad-warning
title: CSR Security
collapse: closed
icon: shield-alt

The private key corresponding to the public key in the CSR never leaves the server. This ensures the security and integrity of the key pair.
```


## Related RFC

[RFC 2986 - PKCS #10: Certification Request Syntax Specification Version 1.7](https://datatracker.ietf.org/doc/html/rfc2986)


# Cryptography and Certificate File Formats

## DER (Distinguished Encoding Rules)

- Binary encoded format
- Used for certificates on the wire
- Not typically used for exchanging files
- File extensions: .der, .cert, .crt, .csr

```ad-warning
title: File Extension Caution
collapse: closed
icon: exclamation-triangle

File extensions are not sufficient to identify the file format. Always verify the actual format of the file.
```

## PEM (Privacy Enhanced Mail)

- Base64 encoded version of DER format
- Easy to copy/paste, editor-friendly
- Contains identifiers like "BEGIN CERTIFICATE", "BEGIN PRIVATE KEY", "BEGIN CERTIFICATE REQUEST"
- A single PEM file can contain multiple certs and CSRs
- File extensions: .pem, .cert, .crt, .key, .csr

```ad-info
title: Base64 Encoding
collapse: closed
icon: info-circle

Base64 encoding converts binary data into a text format by mapping 6 bits to one character. The '=' character is used for padding to ensure the encoded data length is a multiple of 4.
```

## PFX / PKCS#12 (Personal Information Exchange)

- Initially released by Microsoft in 1996
- Re-released as PKCS#12 by RSA Laboratories in 1999
- Contains one certificate and matching key in the same file
- Can include additional chain certificates (optional)
- Binary encoded (cannot open in text editors)
- File extensions: .pfx, .pkcs12, .p12

```ad-note
title: PFX vs PKCS#12
collapse: closed
icon: lightbulb

True PFX formatted files are rare. Most files with .pfx extension are actually in PKCS#12 format.
```

## PKCS#7

- Public Key Cryptography Standard #7
- Base64 encoded file (editor-friendly)
- Contains certificates and/or chains only - no keys
- Originally used for S/MIME (Secure Multipurpose Internet Mail Extensions)
- Not typically used for SSL/TLS
- File extensions: .p7b, .p7c

## Software Preferences for File Formats

Different software and systems prefer different file formats:

- Java: Typically uses DER format
- Apache: Generally uses PEM format
- Windows: Primarily uses PKCS#12 format

```ad-tip
title: Format Conversion
collapse: closed
icon: exchange-alt

Many tools exist for converting between these formats. OpenSSL is a popular command-line tool that can handle most conversions.
```

## Summary Table

| Format | Encoding | Contains | Typical Use | File Extensions |
|--------|----------|----------|-------------|-----------------|
| DER | Binary | Certificates, keys, or CSRs | On-wire transmission | .der, .cert, .crt, .csr |
| PEM | Base64 | Certificates, keys, CSRs (can contain multiple) | File exchange, Apache | .pem, .cert, .crt, .key, .csr |
| PFX/PKCS#12 | Binary | Certificate with matching key, optional chain | Windows, complete cert package | .pfx, .pkcs12, .p12 |
| PKCS#7 | Base64 | Certificates and/or chains (no keys) | S/MIME, certificate sharing | .p7b, .p7c |

```ad-warning
title: Security Consideration
collapse: closed
icon: shield-alt

Files containing private keys (like some PEM files and PKCS#12) should be handled with extreme care and protected with strong passwords when possible.
```


---
# Comprehensive X.509 Certificates and Keys Quiz

1. What are the three main sections of an X.509 certificate?

2. What is the purpose of the Serial Number in a certificate?

3. What does the 'Subject Name' field in a certificate represent?

4. What is the difference between Key Usage and Extended Key Usage extensions?

5. What is the purpose of the Basic Constraints extension?

6. How does the Subject Alternative Name (SAN) extension differ from the Common Name (CN)?

7. What is the difference between a Common Name (CN) and a Canonical Name (CNAME)?

8. What are the contents of an RSA private key?

9. What is the purpose of the Subject Key Identifier and Authority Key Identifier extensions?

10. What is a CSR, and what are its main components?

11. In the context of certificates, what does 'DN' stand for and what does it specify?

12. What is the purpose of the CRL Distribution Points extension?

13. How does a self-signed CA certificate differ from a regular certificate?

14. What is the significance of the 'Version Number' in an X.509 certificate?

15. What is the purpose of the Authority Information Access extension?

```ad-note
title: Quiz Answers
collapse: closed
icon: check-circle

1. The three main sections of an X.509 certificate are:
   - Certificate Data
   - Signature Algorithm
   - Signature

2. The Serial Number uniquely identifies a certificate issued by a given CA. It's used to look up the validity of a certificate.

3. The Subject Name represents the identity of the entity the certificate is issued to (what the certificate is trying to identify).

4. Key Usage defines the intended use of the public key in the certificate, while Extended Key Usage specifies additional purposes for which the certified public key may be used, limiting by protocol and/or role.

5. The Basic Constraints extension indicates if the subject is a CA and specifies the maximum depth of the certification path.

6. The SAN extension allows multiple identities (like multiple domains) to be bound to the certificate, while the CN typically represents a single domain.

7. CN is used in X.509 digital certificates to represent the server name, while CNAME is a DNS record type that maps an alias to a true domain name.

8. An RSA private key contains:
   - p and q (two large prime numbers)
   - n (the modulus, n = p * q)
   - d (the private exponent)
   - e (the public exponent)
   - Additional optimization values (dp, dq, qinv)

9. The Subject Key Identifier provides a means of identifying certificates containing a particular public key, while the Authority Key Identifier identifies the public key corresponding to the private key used to sign a certificate.

10. A CSR (Certificate Signing Request) is a file submitted to a CA to apply for a certificate. Its main components are:
    - Certificate Request Information
    - Signature Algorithm
    - Signature

11. DN stands for Distinguished Name. It specifies the subject and issuer in a standardized format, including elements like Common Name, Organization, Country, etc.

12. The CRL Distribution Points extension indicates how Certificate Revocation List information can be obtained.

13. In a self-signed CA certificate, the Subject and Issuer are the same, as the CA issues its own certificate.

14. The Version Number indicates the X.509 version (v1, v2, or v3). V3 adds support for certificate extensions.

15. The Authority Information Access extension indicates how to access CA information and services, including where to find the CA's certificates and the location of the OCSP service for checking certificate validity.
```

---
# Reference


[[Certificate file format commands]]

[[Base64 table conversion]]