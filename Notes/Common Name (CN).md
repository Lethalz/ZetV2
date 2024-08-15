#### Common Name (CN)

- Every certificate must have one Common Name
- Browsers verify CN against URL in address bar
- CN can include a wildcard(\*) which allows a single CN to cover a single subdomain

![[Pasted image 20240814113919.png]]

Notice it covers www.google.com but not google.com, the wildcard makes it so there has to be something before .google.com.

![[Pasted image 20240814114130.png]]





##### Related RFC:

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