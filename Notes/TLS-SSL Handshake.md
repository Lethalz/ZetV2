2409161636
	Status: #course #idea
		Tags:  [[Practical TLS]] 
# TLS-SSL Handshake


# TLS/SSL Records Structure and Types

## Overview

TLS/SSL conversations are composed of records. These records form the basic unit of data transmission in the TLS/SSL protocol.

## Record Types

1. Handshake
2. Alert
3. Change Cipher Spec
4. Application Data

## Record Subtypes

Some record types are further divided into subtypes:

### Handshake Subtypes:
- Client Hello
- Server Hello

### Alert Subtypes:
- Handshake Failure

## Record Transmission Characteristics

Records have a flexible relationship with network packets:

1. One record per packet
2. Multiple records in one packet
3. One record sent across multiple packets

Important: Records are not confined to or limited by IP datagram length.

## Record Structure

Each record begins with a header followed by the payload:

### Record Header Components:
1. Record Type
2. SSL Version
3. Record Length

### Record Payload:
- Contains the actual data for the specific record type

## Key Points

1. TLS/SSL uses a record-based structure for all communications.
2. Records are the fundamental units of data in TLS/SSL protocols.
3. The relationship between records and network packets is flexible.
4. Each record has a defined structure with a header and payload.
5. Understanding record types and structure is crucial for analyzing TLS/SSL traffic.



![[Pasted image 20240916163703.png]]
---






# TLS/SSL Records: Detailed Type Information

## Change Cipher Spec (Type 20)

- Indicates sender has everything needed to speak securely (cipher suites and session keys)
- Sent independently by both client and server
- Everything sent after this is encrypted
- Record payload is binary 0000 0001
- Length: 1 byte
- Signals readiness to speak securely

## Alert (Type 21)

- Informational notification
- Contains two items:
  1. Severity:
     - 01: Warning (session can continue)
     - 02: Fatal (session terminates)
  2. Description: Notification details
- Sent unencrypted unless after Change Cipher Spec

### Alert Description Codes

| Description | HEX | DEC |
|-------------|-----|-----|
| Handshake failure | 0x28 | 40 |
| Certificate revoked | 0x2A | 42 |
| Certificate expired | 0x2B | 43 |
| Unsupported extension | 0x6E | 110 |
| Unrecognized name | 0x70 | 112 |

## Handshake (Type 22)

- TLS/SSL negotiation messages
- Classified into sub-types
- Sent unencrypted, except for certain fields within specific subtypes

## Application Data (Type 23)

- Bulk data protected by SSL/TLS
  - Confidentiality
  - Integrity
  - Authentication
- TLS process:
  1. Calculates MAC on record header and plaintext data
  2. Encrypts:
     - Plaintext data
     - MAC digest
     - Padding

### TLS Encryption Approach

- TLS uses MAC-then-encrypt
  - Potential issue: Receiver doesn't know about tampering until decryption
  - Padding not included in MAC (no integrity on padding)

### AEAD (Authenticated Encryption with Associated Data)

- Solution to MAC-then-encrypt vulnerabilities
- Performs hashing and encryption in the same step
- AE (Authenticated Encryption): Integrity + Encryption
- AD (Associated Data): Integrity only
- Recommended approach
- TLS 1.3: All ciphers are AEAD
- TLS 1.2: AES-GCM, ChaCha20-Poly1305 support AEAD

```ad-note
title: Evolution of TLS Security
collapse: closed
icon: shield-alt

The move towards AEAD ciphers in TLS 1.2 and mandating them in TLS 1.3 represents a significant improvement in the protocol's security, addressing vulnerabilities associated with the traditional MAC-then-encrypt approach.
```



















# Reference