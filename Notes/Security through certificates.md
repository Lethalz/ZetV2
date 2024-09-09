2408311401
	Status: #idea 
		Tags: [[Practical TLS]] [[Cryptography]]

# Security through certificates

# Overview of the SSL/TLS Process

## 1. Certificate Authority (CA) Foundation
- CA possesses a public key and a private key
- CA has a self-signed certificate

```ad-info
title: Self-Signed Certificate
collapse: closed
icon: info-circle

A self-signed certificate is one where the issuer and the subject are the same entity. CAs use these to establish the root of trust in PKI.
```

## 2. Server Certificate Acquisition
- Server generates its own public and private key pair
- Server creates a Certificate Signing Request (CSR)
  - CSR contains the server's public key
  - CSR is signed by the server's private key

## 3. Certificate Issuance Process
- Server submits the signed CSR to the CA
- CA inspects and validates the information in the CSR
- CA creates a certificate using information from the CSR
- CA signs the certificate using its private key
- CA provides the signed certificate to the server

## 4. Server Identity Proof
- Server can now use the certificate to prove its identity

## 5. Client-Server Secure Connection
- Client initiates a secure connection to the server
- Web browsers come pre-installed with CA certificates

## 6. Certificate Validation
- Client requests the server's certificate
- Client validates the certificate's legitimacy:
  - Uses CA's public key (pre-installed in the browser)
  - Verifies the server owns the certificate by ensuring it has the private key corresponding to the public key in the certificate

## 7. SSL/TLS Handshake
- Client validates the server's certificate during the handshake
- Handshake produces session keys for:
  - Symmetric encryption (ensuring confidentiality)
  - Message Authentication Code (MAC) (ensuring integrity and authentication)

## 8. Secure Communication Establishment
- Session keys form a secure tunnel to protect all subsequent communication

```ad-warning
title: Certificate Expiration
collapse: closed
icon: clock

Certificates have a validity period. It's crucial to renew them before expiration to maintain secure connections.
```


# Certificate Validation

When a client receives a certificate from a server, two crucial validations must occur:

1. Is the certificate valid?
2. Is the server the true owner of the certificate?

## Is the Certificate Valid?

Certificates are essentially text files, so the client needs a way to trust their contents.

### Certificate Authority (CA) Role
1. CA creates a hash of certificate data
2. CA encrypts the hash with its private key
3. The result is the signature of the certificate
4. This signature can be used to validate the certificate data

### Client Validation Process
1. Client already has the CA certificate (including CA's public key)
2. Client decrypts the signature with CA's public key
3. Client calculates the hash of the certificate data
4. If the decrypted hash matches the calculated hash, the certificate is valid

```ad-note
title: Trust Chain
collapse: closed
icon: link

If we trust the CA, then a valid signature means we can trust the certificate.
```

### Process for Different Signature Algorithms

#### RSA Signed Certificates
- Follow the process described above

#### DSA Signed Certificates
1. CA runs signature generation on certificate data using its private key
2. Client runs signature verification on the signature using CA's public key
3. Result is either 1 (true) or 0 (false)

### Additional Checks
Once the signature is verified, the client checks:
- Validity period: Has the certificate expired?
- Subject: Does the URL match the Common Name or an entry in Subject Alternative Name (SAN)?
- Revocation status: Is the certificate revoked?

## Is the Server the True Owner of the Certificate?

Anyone can present someone else's certificate, but only the true owner will have the matching private key.

### Method 1: Client-Initiated (typically used with RSA)
1. Client generates a random value
2. Client encrypts the value with the server's public key
3. Server decrypts with its private key to extract the original value
4. Values are used to generate session keys
5. If subsequent data can be decrypted with these keys, the server is authenticated

### Method 2: Server-Initiated (typically used with Diffie-Hellman)
1. During the handshake, the server sends a value to the client
2. Server signs the value with its private key
3. Client validates the signature with the server's public key
4. Values (combined with other client-server shared values) are used to generate session keys

```ad-warning
title: Key Exchange Security
collapse: closed
icon: shield-alt

The random values used in key exchange are combined with other values known only to the client and server to prevent eavesdropping attacks.
```

## Asymmetric Key Protocol Comparison

| Protocol | Encryption | Signatures | Key Exchange |
|----------|------------|------------|--------------|
| RSA      | ✓          | ✓          | ✓            |
| DH       | ✗          | ✗          | ✓            |
| DSA      | ✗          | ✓          | ✗            |

```ad-info
title: Protocol Choice
collapse: closed
icon: info-circle

The choice between RSA and DH for key exchange depends on the agreed cipher suite between client and server. RSA is traditionally more common, but DH (especially ECDHE) is increasingly preferred for its perfect forward secrecy.
```

![[Pasted image 20240907135828.png]]
# Certificate Chains

## Purpose and Advantages

Certificate chains provide a more scalable and secure trust system compared to relying solely on root Certificate Authorities (CAs).

1. Scalability: Avoids need for software updates if a CA key is compromised
2. Security: Creates "control points" through intermediate CAs
3. Agility: Allows for quick revocation of compromised intermediate CAs
4. Root CA Protection: Reduces usage of root CA's private key

```ad-info
title: Root CA Security
collapse: closed
icon: shield-alt

Root CA private keys are often stored on air-gapped systems or secure Hardware Security Modules (HSMs) to enhance protection.
```

## Structure of a Certificate Chain

1. Root Certificate Authority (CA)
   - Start of the chain
   - Has a public and private key pair
   - Uses a self-signed certificate
   - Certificate pre-installed in web browsers
   - Provides the "trust anchor"

2. Intermediate Certificate Authorities (ICA)
   - Separate entities with their own public/private key pairs
   - Acquire certificates by sending CSRs to the root CA or another ICA
   - Can form multiple levels in the chain

3. End Entity Certificate (Server Certificate)
   - Also called "leaf cert" or "server cert"
   - Represents the actual server being authenticated

```ad-tip
title: Trust Management
collapse: closed
icon: user-shield

To untrust a CA, uninstall their certificate from your web browser. To trust a new root CA, install their certificate in your browser.
```

## Chain Formation

- Subject and Issuer fields in certificates form the chain back to the root CA
- Each certificate in the chain is signed by the CA above it
- The root CA's certificate is self-signed

## Certificate Transmission to Client

1. Client should already have root CA certificate installed
2. Server must send its end entity (leaf) certificate
3. Server must send every intermediate certificate in the chain
4. Server can optionally send the root CA certificate (client will ignore it)

```ad-warning
title: Trust Anchor Validation
collapse: closed
icon: exclamation-triangle

The client will only trust the root CA certificate from its local certificate store, not the one sent by the server. This prevents potential attacks where a malicious server might try to provide a fake root certificate.
```

## Chain Validation Process

1. Client validates each certificate's signature in the chain
2. Validation starts from the leaf certificate and moves up the chain
3. Each certificate is verified using the public key of the issuer (the CA that signed it)
4. The process continues until reaching a trusted root CA in the client's local store

## Benefits of Certificate Chains

1. Organizational Boundaries: Allows CAs to create different security zones (e.g., separate ICAs for different regions)
2. Improved Security: Compromised ICAs can be quickly revoked without affecting the entire system
3. Reduced Root CA Exposure: Root CA's private key is used less frequently, enhancing its security

```ad-note
title: Chain Length
collapse: closed
icon: link

While theoretically unlimited, most certificate chains are kept relatively short (usually 3-4 levels) to balance security and performance.
```


![[Pasted image 20240831210221.png]]



# Basic Constraints

# Basic Constraints Extension

## Problem Addressed

The Basic Constraints extension addresses a fundamental security issue in certificate chains:

- Valid certificates should have valid chains all the way to the root CA.
- Creating a signed certificate only requires a private key.
- Legitimate servers have their own public and private keys.

However, this leads to potential vulnerabilities:
1. Anyone can create new keys and a Certificate Signing Request (CSR) for any website.
2. Anyone with a valid signed certificate can create a signed certificate for any website.

```ad-warning
title: Potential for Abuse
collapse: closed
icon: exclamation-triangle

Without Basic Constraints, a compromised or malicious end-entity certificate could be used to create seemingly valid certificate chains, potentially leading to widespread security issues.
```

## Solution: Basic Constraints

- Ratified in 1999
- Implemented as an X.509v3 extension

## Structure

The Basic Constraints extension has two main components:

1. CA Flag: Indicates if the subject can issue certificates
   - `cA: TRUE` or `cA: FALSE`

2. Path Length Constraint (optional)
   - Specifies the maximum number of intermediate CAs allowed in the certificate chain below this certificate
   - Only applicable when `cA: TRUE`

```ad-info
title: Path Length Examples
collapse: closed
icon: info-circle

- Path Length 0: The certificate can only issue end-entity certificates
- Path Length 1: The certificate can issue one level of intermediate CA certificates
- No Path Length specified: No limit on the chain length (when cA: TRUE)
```

## Importance in Certificate Security

1. Prevents End-Entity Certificates from Issuing Other Certificates:
   - End-entity certificates should have `cA: FALSE`

2. Limits Chain Depth:
   - Helps control the complexity and potential vulnerabilities in certificate chains

3. Enforces Hierarchy:
   - Ensures that only designated CAs can issue certificates, maintaining the intended trust structure

```ad-tip
title: Validation Best Practice
collapse: closed
icon: check-circle

Certificate validation processes should always check the Basic Constraints extension. Certificates with cA: FALSE should never be accepted as issuers of other certificates.
```

## Implementation

- Certificate Authorities must include this extension in issued certificates
- Certificate validation software must check and enforce the Basic Constraints
- Modern browsers and operating systems typically enforce Basic Constraints by default

```ad-note
title: Historical Context
collapse: closed
icon: history

Before the widespread implementation of Basic Constraints, some systems were vulnerable to attacks where end-entity certificates could be used to sign other certificates. This extension has significantly improved PKI security since its introduction.
```


![[Pasted image 20240901194649.png]]



# SSL Certificate Types

To acquire an SSL certificate, one must generate a Certificate Signing Request (CSR) and submit it to a Certificate Authority (CA). The CA then validates the requester's identity before issuing a certificate. The type of certificate correlates with how thoroughly the identity is validated.

## Domain Validation (DV) Certificates

- Validates that the server owns the domain
- Validation methods:
  1. Send an email from the domain using pre-approved mailboxes
  2. Publish a specific token at a specific URL

```ad-info
title: DV Certificate Characteristics
collapse: closed
icon: info-circle

- Lowest cost (often free)
- Available instantly through automation
- Example: Let's Encrypt (letsencrypt.org)
```

## Organization Validation (OV) Certificates

- Validates server owns the domain
- Validates domain is owned by a legitimate corporation
- CA verifies corporation against public records:
  - Business registration
  - Chamber of Commerce
  - Tax records

```ad-note
title: OV Certificate Details
collapse: closed
icon: building

- Ties a domain name to an actual company
- Can be acquired within a few days
- More expensive than DV certificates
```

## Extended Validation (EV) Certificates

- Validates server owns the domain
- Validates domain is owned by a legitimate corporation
- Extensive additional validation:
  - Corporation's physical address
  - Corporation has been in operation for at least 3 years
  - CSR requester is authorized to request certificates
  - Verifies reliable means of communication between CA and company

```ad-warning
title: EV Certificate Controversy
collapse: closed
icon: exclamation-triangle

Criticisms against EV certificates:
- Viewed by some as a ploy for CAs to charge more money
- Underlying cryptography and SSL handshake are unaffected
- Only affects "security" in how the certificate was acquired
- Chrome, Safari, and Firefox have removed visual indicators for EV certificates
```

```ad-info
title: EV Certificate Characteristics
collapse: closed
icon: certificate

- Most expensive option
- Takes 7-14+ days to acquire
- Historically, browser address bar showed indicator for EV certificates
```

## Identifying Certificate Types

Certificate types can be identified with an X.509v3 extension:

- EV Certificates: Certificate Policy: 2.23.140.1.1
- OV Certificates: Certificate Policy: 2.23.140.1.2.2 (most cases)
- DV Certificates: Certificate Policy: 2.23.140.1.2.1 (most cases)

## Comparison Table

| Feature | DV | OV | EV |
|---------|----|----|------|
| Domain Ownership | ✓ | ✓ | ✓ |
| Organization Verification | ✗ | ✓ | ✓ |
| Extensive Validation | ✗ | ✗ | ✓ |
| Typical Issuance Time | Minutes | Days | 1-2 Weeks |
| Cost | Low/Free | Medium | High |
| Visual Indicator in Browser | ✗ | ✗ | ✗ (Previously ✓) |

```ad-tip
title: Choosing a Certificate Type
collapse: closed
icon: lightbulb

The choice between DV, OV, and EV certificates depends on your organization's needs, budget, and the level of trust you want to establish with your users. For many websites, a DV certificate provides sufficient security.
```


# Certificate Revocation

Certificate revocation becomes necessary when a private key is compromised. This requires:
1. Generating new keys
2. Acquiring a new certificate

However, the old certificate still exists and remains technically valid. Revocation is the process of invalidating these certificates to prevent malicious use.

## CRL (Certificate Revocation List)

CRL is a list of revoked certificates maintained by the Certificate Authority (CA).

### Key Points:
- Location of CRL is embedded in each certificate
- CRL contains certificate serial numbers and revocation dates
- Optionally includes revocation reasons

### Process:
1. Client requests certificate from server
2. Server provides that cert and any other certs in the chain
3. Client looks into the certificate and downloads the CRL from CA
4. Client checks CRL for the certificate's serial number

```ad-warning
title: CRL Criticisms
collapse: closed
icon: exclamation-triangle

1. Tedious and slow: CRLs can be thousands of lines long
2. Adds processing time when accessing secure websites
3. CRLs are typically updated every 5-14 days
4. Often not checked as users favor speed over security
```

```ad-info
title: Browser Behavior
collapse: closed
icon: browser

- Google Chrome historically skipped CRL security checks for faster performance
- Some browsers maintain local CRLs to balance security and speed
```

## OCSP (Online Certificate Status Protocol)

OCSP provides real-time certificate status checks.

### Key Points:
- OCSP responder maintained by CA
- Status is requested individually by serial number
- Location (Authority Information Access) is embedded in each certificate
- Requests made via HTTP (status is not sensitive, but is signed by CA)

### Process:
1. Client acquires server cert
2. Client looks up responder URI
3. Client requests status from OCSP responder
4. OCSP responder replies with status: Good, Revoked, or Unknown

```ad-tip
title: OCSP Advantages
collapse: closed
icon: thumbs-up

OCSP improves upon the CRL process by providing real-time, individual certificate checks, reducing bandwidth and processing requirements.
```

```ad-warning
title: OCSP Criticisms
collapse: closed
icon: exclamation-triangle

1. Privacy concerns: CA is contacted on every client visit
   - CA knows server visit statistics
   - CA potentially knows client browser history
2. Requires resilient OCSP responders
   - E.g., Google Chrome: ~200k requests per second
3. HTTP request can be disrupted
```

## OCSP Stapling

OCSP Stapling is an improvement on the standard OCSP protocol, designed to address some of its criticisms.

### Key Points:
- Server periodically requests its own OCSP response from the CA
- Server "staples" this time-stamped OCSP response to the TLS handshake
- Client can verify the stapled OCSP response without contacting the CA

### Process:
1. Server requests its OCSP status from the CA periodically (e.g., daily)
2. CA provides a signed, time-stamped OCSP response
3. During TLS handshake, server sends its certificate along with the stapled OCSP response
4. Client verifies the OCSP response signature and timestamp

```ad-tip
title: OCSP Stapling Benefits
collapse: closed
icon: star

1. Improves performance: Eliminates separate OCSP request by client
2. Enhances privacy: Client doesn't need to contact CA directly
3. Reduces load on OCSP responders
4. Provides fault tolerance: Server can cache a valid response
```

### Limitations:
- Requires server-side support and configuration
- Stapled response has a limited validity period
- Doesn't completely eliminate the need for fallback revocation checking methods

```ad-info
title: Must-Staple Extension
collapse: closed
icon: certificate

Certificates can include a "must-staple" extension, indicating that the server should always provide a stapled OCSP response. This helps ensure the revocation check occurs.
```

## Comparison Table: CRL vs OCSP vs OCSP Stapling

| Feature | CRL | OCSP | OCSP Stapling |
|---------|-----|------|---------------|
| Update Frequency | Every 5-14 days | Real-time | Periodic (e.g., daily) |
| Data Transfer | Entire list | Individual cert status | Stapled response |
| Privacy | Better | Worse | Best |
| Speed | Slower | Faster | Fastest |
| Server Load | Lower | Higher | Moderate |
| CA Load | Lower | Higher | Lower |
| Real-time Accuracy | Lower | Higher | Moderate |
| Client Implementation | Complex | Moderate | Simple |

```ad-note
title: Balancing Security and Performance
collapse: closed
icon: balance-scale

The choice between CRL, OCSP, and OCSP Stapling often involves balancing security needs with performance considerations. Some systems use a hybrid approach to mitigate drawbacks of individual methods.
```

![[Pasted image 20240902091334.png]]



# Detailed Walkthrough: Checking Certificate Revocation Status

## CRL (Certificate Revocation List)

### 1. Retrieve the Certificate

Use OpenSSL's s_client to connect to the server and retrieve the certificate:

```bash
openssl s_client -connect example.com:443 -servername example.com < /dev/null | openssl x509 -outform PEM > certificate.pem
```

This command connects to the server, retrieves the certificate, and saves it as `certificate.pem`.

### 2. Retrieve the CRL

Examine the certificate to find the CRL distribution point:

```bash
openssl x509 -in certificate.pem -text -noout | grep -A 2 "CRL Distribution Points"
```

This will output the CRL distribution point URL. Download the CRL using curl or wget:

```bash
curl -o crl.pem http://crl.example.com/crl.pem
```

### 3. Check the Certificate Serial Number Against the CRL

First, get the certificate's serial number:

```bash
openssl x509 -in certificate.pem -noout -serial
```

Then, check if this serial number is in the CRL:

```bash
openssl crl -in crl.pem -text -noout | grep -i "Serial Number: <serial_from_previous_step>"
```

If there's a match, the certificate has been revoked.

```ad-tip
title: Automating CRL Checks
collapse: closed
icon: robot

For large-scale operations, consider using scripts to automate these steps, especially for checking multiple certificates against a CRL.
```

## OCSP (Online Certificate Status Protocol)

### 1. Retrieve the Certificate

Use the same method as in the CRL section to retrieve the certificate.

### 2. Find the OCSP Responder URI

Examine the certificate to find the OCSP responder URI:

```bash
openssl x509 -in certificate.pem -oscp_uri -noout 
```

### 3. Make an OCSP Request

Use OpenSSL's ocsp command to check the certificate status:

```bash
openssl ocsp -issuer issuer.pem -cert certificate.pem -url http://ocsp.example.com -text
```

You'll need the issuer's certificate (`issuer.pem`). If you don't have it, you can often extract it from the server's certificate chain:

```bash
openssl s_client -connect example.com:443 -servername example.com < /dev/null | openssl x509 -outform PEM > issuer.pem
```

Or you can look under the x509 Authority Information Access extensions and Use `wget` on the CA Issuers information.

```bash
wget http://e6.i.lencr.org/
```

```ad-warning
title: OCSP Response Interpretation
collapse: closed
icon: exclamation-triangle

The OCSP response will typically be "good", "revoked", or "unknown". Be prepared to handle all possible responses in your verification process.
```

## OCSP Stapling

OCSP Stapling is simpler from the client's perspective, as the server provides the OCSP response during the TLS handshake.

### Check OCSP Stapling

Use OpenSSL's s_client with the -status option:

```bash
openssl s_client -connect example.com:443 -status -servername example.com < /dev/null | grep -i "OCSP response"
```

If OCSP Stapling is enabled and working, you should see an "OCSP Response Status" in the output.

```ad-info
title: OCSP Stapling Support
collapse: closed
icon: info-circle

Not all servers support OCSP Stapling. If you don't receive an OCSP response, it doesn't necessarily mean the certificate is revoked; the server might not support stapling.
```

## Additional Considerations

1. **Certificate Chain**: In real-world scenarios, you often need to verify the entire certificate chain. Each certificate in the chain (except the root) should be checked for revocation.

2. **Handling Failures**: Implement appropriate error handling. Network issues or unavailable OCSP responders shouldn't necessarily result in treating a certificate as revoked.

3. **Caching**: Consider caching OCSP responses and CRLs (respecting their validity periods) to improve performance in high-volume environments.

4. **Fail-Open vs Fail-Closed**: Decide whether your system should fail-open (accept the certificate if revocation checking fails) or fail-closed (reject the certificate if revocation checking fails). This decision should be based on your specific security requirements.

```ad-warning
title: Security vs. Performance
collapse: closed
icon: balance-scale

Revocation checking can impact performance, especially with CRLs or in high-traffic scenarios. Balance security needs with performance requirements when implementing these checks in production environments.
```















# Reference

![[Pasted image 20240902084332.png]]


