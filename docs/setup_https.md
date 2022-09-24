---
sidebar_position: 5
---

# Setup HTTPS/TLS

At the top level, dappy allows you to have a self signed certificate. This is because **you are your own certificate authority** 🔒🔒🔒, you don't have to ask permission to exist !

Below is the `openssl` command we use yo generate a self signed certificate. Change `mydomain` so that it fits your domain of course.

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

You are free to choose for how many days your certificate is valid.

Softwares resolving dappy zones need to get the certificate as base64, therefore you now have to turn it into a base64 and add it to your zone. **Be careful, your base64 should have no carriage return and be only one line**.

```bash
# turn to base64 and remove carriage returns
base64 mydomain.crt > tmp.crt && tr -d '\n' < tmp.crt > mydomain.base64
```

Now we must add the CERT record to our config file and push again.

```json title="dappy.config.json"
{
  config: { ... },
  zones: [{
    "origin": "mydomain",
    "ttl": 3600,
    "records": [
      ...
      {
        "name": "@",
        "type": "CERT",
        "data": "LS0tLS1CRUdJTiBDRV..."
      }
    ]
  }]
}
```

```bash
npx @fabcotech/dappy-cli pushzones
npx @fabcotech/dappy-cli check
```

**💡 Note :** the certificate you have forged **is a true root certificate** not signed by any certificate authority (you are the CA), it will be retreived with co-resolution by dappy browser, just like the IP addresses.

[Check the website](check_the_website.md)