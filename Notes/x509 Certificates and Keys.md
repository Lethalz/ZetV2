2408140918
	Status: #idea 
		Tags: [[Practical TLS]] [[Cryptography]]  

# x509 Certificates and Keys


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
   





---
# Reference