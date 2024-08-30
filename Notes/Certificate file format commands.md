

2408300943
	Status: #idea 
		Tags:  [[Practical TLS]]

# Certificate file format commands

# File Format Conversion Cheatsheet

## Viewing File Contents

```
# View PEM file
cat filename.pem

# View certificate details
openssl x509 -in filename.cert -noout -text

# View private key details
openssl rsa -in filename.key -noout -text

# View PFX file contents
openssl pkcs12 -in filename.pfx -nodes -info
```

## PEM Conversions

```
# PEM to DER (Certificate)
openssl x509 -in input.pem -outform DER -out output.der

# PEM to DER (Private Key)
openssl rsa -in input.pem -outform DER -out output.der

# PEM to PFX
openssl pkcs12 -in cert.pem -inkey key.pem -export -out output.pfx
```

## DER Conversions

```
# DER to PEM (Certificate)
openssl x509 -in input.der -inform der -out output.pem

# DER to PEM (Private Key)
openssl rsa -in input.der -inform der -out output.pem
```

## PFX Conversions

```
# PFX to PEM (All contents)
openssl pkcs12 -in input.pfx -out output.pem -nodes

# Extract only certificates
openssl pkcs12 -in input.pfx -out certs.pem -nokeys

# Extract only private key
openssl pkcs12 -in input.pfx -out key.pem -nodes -nocerts

# Extract client cert and key (no CA certs)
openssl pkcs12 -in input.pfx -out client.pem -nodes -clcerts
```

```ad-tip
title: Password Prompts
collapse: closed
icon: key

For PFX files, you may be prompted for an import/export password. If not set, press Enter to leave it blank.
```

```ad-warning
title: File Extensions
collapse: closed
icon: exclamation-triangle

File extensions (.pem, .der, .pfx) don't guarantee the format. Always verify the actual format of the file.
```
---
# Reference