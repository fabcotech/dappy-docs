---
sidebar_position: 4
---

# Create a zone (domain name helloworld.d)

Let's setup our first zone in `dappy.config.json`. A zone is simply the equivalent of a DNS (domain name system) zone, in the dappy name system. We will create a zone that is hardcoded in dappy CLI (a basic hello world example), we will later launch the webserver that matches this zone (same TLS configuration).

```bash
npx dappy-cli helloworldzone
# You should have log "Zone created !"
```

```json title="dappy.config.json"
{
  "options": { ... },
  "zones": [
    {
      "origin": "helloworld",
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
          "data": "...="
        }
      ]
    }
  ]
}
```
🔍 Take the time to understand what is going on. Dappy CLI has created a new entry in the `config.zones` array. This new entry has three interesting properties:
- `origin: "helloworld"` : this is the TLD (or identifier in the dappy name system), it does not exist yet but dappy CLI will try to purchase NFT `"helloworld"` in the dappy name system contract.
- `type "A" record with data: "127.0.0.1"` : this tells dappy browser or any program that can resolve dappy names that `"127.0.0.1"` is the IP address at which the web app corresponding to `"helloworld"` will be served.
- `type "CERT" record` : when you use dappy you don't have to deal with certificate authorities, you can generate a key pair with `openssl` (self signed certificate), and upload it on the blockchain. Co-resolution will make sure that there is no man-in-the-middle attack, and that the true certificate has been resolved.

