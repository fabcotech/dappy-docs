---
sidebar_position: 4
---

# Create a zone

One JSON file can manage hundreds of zones and domain names. Let's setup our first zone in `dappy.config.json`.

A zone is simply the equivalent of a DNS (domain name system) zone, in the dappy name system. We will create a simple zone, the goal is to have a https website running on `localhost` (IP `127.0.0.1`).

**Maybe your zones are already up to date**

Depending on how you started, your zones may already be in sync with the blockchain state, it's always worth checking. 

```bash
npx @fabcotech/dappy-cli check
```

Let's create a new record in one of the zones that you have downloaded (you can also create from scratch).

```json title="dappy.config.json"
{
  "options": { ... },
  "zones": [
    {
      "origin": "mydomain",
      "ttl": 3600,
      "records": [
        {
          "name": "@",
          "type": "A",
          "data": "127.0.0.1"
        }
      ]
    }
  ]
}
```

🔍 Take the time to understand what is going on. Dappy CLI has created a new entry in the `config.zones` array. This new entry has three interesting properties:
- `origin: "mydomain"` : this must obviously be replaced by your domain (without the `.d` or `.gamma` at the end) this is the TLD.
- `type "A" record with data: "127.0.0.1"` : this tells dappy browser or any program that can resolve dappy names that `"127.0.0.1"` is the IP address at which the web app corresponding to `"mydomain"` will be served.

```bash
npx @fabcotech/dappy-cli pushzones
```

**The owner TXT record, what is it ?**

If you created **dappy.config.json** file from scratch, you may have the following log.

```
Using dappy network gamma
⨯ mydomain           : local zone is invalid, no owner
```

That is great, it means the config file lacks the only record that is always needed for a zone to be valid : a TXT record with the owner (identified with the public key).

This record (and public key) is used by each member of a dappy network when he wants to check that a zone update is legitimate. Only you with your private key will be able to air messages that will be accepted by the dappy network as a whole.

If you don't know your public key :

```bash
npx @fabcotech/dappy-cli printpublickey
```

```json title="dappy.config.json"
{
  "options": { ... },
  "zones": [
    {
      "origin": "mydomain",
      "ttl": 3600,
      "records": [
        ...
        { "name": "@", "type": "TXT", "data": "OWNER=mypublickey" }
      ]
    }
  ]
}
```

The `no owner` error should be gone now.

```bash
npx @fabcotech/dappy-cli pushzones
```

You should have the following log.

```
Using dappy network gamma
Will process the following zones        : mydomain
Dappy network   :  gamma
Public key      :  abcdefgh
Purchases and updates were deployed, now do dappy-cli check to verify the state of your domains
```

That's it, our zone is created or updated, you can check as many time as you want now that your DNS zone is stored in the dappy name system, and ready to be resolved (co-resolved) by clients.

```bash
npx @fabcotech/dappy-cli check
```

**🔍 What's hapenning under the hood ?**

When you do the `pushzones` command, dappy CLI takes your private key, signes the zone, sends this signed message to a member of the dappy network it knows. The network members will each verify the message, update the zone and gossip the message to others. After few seconds everyone has the new version and clients can keep or start doing co-resolution !
