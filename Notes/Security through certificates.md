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






# Reference


