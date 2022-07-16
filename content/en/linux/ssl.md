---
title: SSL
---

# SSL

## Create self-signed SSL Certificate
- also see:
  - <https://www.akadia.com/services/ssh_test_certificate.html>
  - <https://devcenter.heroku.com/articles/ssl-certificate-self#generate-ssl-certificate>
  - <https://www.postgresql.org/docs/current/ssl-tcp.html#SSL-CERTIFICATE-CREATION>

```bash
# generate private key
openssl genrsa -des3 -out server.pass.key 2048
# or
openssl genrsa -des3 -out server.pass.key 4096

# remove passphrase from Key
openssl rsa -in server.pass.key -out server.key
rm server.pass.key

# generate csr (certificate signing request)
openssl req -new -key server.key -out server.csr

# generate self-signed certificate
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
or
openssl x509 -req -days 36500 -in server.csr -signkey server.key -out server.crt
```

## Create Client Certifcate that can be used by Firefox and other Browsers
```bash
openssl pkcs12 -export -in client.crt -inkey client.key -out client.p12
```
