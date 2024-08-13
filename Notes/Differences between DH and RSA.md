


2408131624
	Status: #idea 
		Tags: 

# Differences between DH and RSA


- Purpose:
    - RSA: Primarily used for both encryption and digital signatures.
    - Diffie-Hellman: Used for secure key exchange over an insecure channel.
- Type of Cryptography:
    - RSA: Asymmetric encryption algorithm (uses public and private keys).
    - Diffie-Hellman: Key agreement protocol (allows two parties to establish a shared secret).
- Operations:
    - RSA: Based on the difficulty of factoring large prime numbers.
    - Diffie-Hellman: Based on the discrete logarithm problem.
- Key Usage:
    - RSA: The public key can be freely distributed, while the private key must be kept secret.
    - Diffie-Hellman: Both parties contribute to generating a shared secret key.
- Functionality:
    - RSA: Can be used to encrypt data directly.
    - Diffie-Hellman: Doesn't encrypt data; it only establishes a shared secret.
- Speed:
    - RSA: Generally slower, especially for large amounts of data.
    - Diffie-Hellman: Typically faster for key exchange operations.
- Common Uses:
    - RSA: Often used in TLS/SSL for initial key exchange and in digital signatures.
    - Diffie-Hellman: Commonly used in VPNs and as part of the TLS handshake process.
- Forward Secrecy:
    - RSA: Doesn't provide forward secrecy by itself.
    - Diffie-Hellman: When used in ephemeral mode (DHE), provides forward secrecy.

---
# Reference