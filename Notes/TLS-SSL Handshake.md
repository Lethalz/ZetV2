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
# Reference