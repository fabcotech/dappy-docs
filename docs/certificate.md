---
sidebar_position: 7
---

# Generating the certificate

At the top level, dappy allows you to have a self signed certificate. This is because you are your own certificate authority 🔒🔒🔒, you don't have to ask permission to exist !

In our example we chose a certificate that has `helloworld.d` in the alt name, you may want to use another name of course. Below is the `openssl` command we use yo generate a self signed certificate.

```bash
openssl req \
  -x509 \
  -newkey rsa:2048 \
  -sha256 \
  -days 10000 \
  -nodes \
  -keyout mydomain.key \
  -out mydomain.crt \
  -outform PEM \
  -subj '/CN=mydomain.d'\
  -extensions san \
  -config <( \
    echo '[req]'; \
    echo 'distinguished_name=req'; \
    echo '[san]'; \
    echo 'subjectAltName=DNS.1:localhost,DNS.2:mydomain.d')
```

Change every occurence of `mydomain` in this command to generate a certificate and private key for your zone. Note that you are free to choose for how many days your certificate is valid.

Softwares resolving dappy zones need to get the certificate as base64, therefore you now have to turn it into a base64 and add it to your zone. **Be careful, your base64 should have no return and be only one line**.

```bash
base64 mydomain.crt
```

```json title="dappy.config.json"
{
  config: { ... },
  zones: [{
    "origin": "mydomain",
    "ttl": 3600,
    "records": [
      {
        "name": "@",
        "type": "A",
        "data": "127.0.0.1"
      },
      {
        "name": "@",
        "type": "CERT",
        "data": "LS0tLS1CRUdJTiBDRV..."
      }
    ]
  }]
}
```