---
sidebar_position: 1
---

# Introduction

## Welcome

![Cool banner](/img/banner.jpg)

Hey there you are on the offical dappy docs, welcome ! 🚀😉.

Dappy is a public open source name system that uses the blockchain, and provides a zero-trust co-resolution system. It has been engineered specifically for **🏢 critical web applications**, **🔒 protection of sensitive data** and **🚤 lean + rapid monitoring and management**. It is therefore a good fit for enterprises web applications, cryptocurrency, B2B or any other web application (or API) that needs high security and privacy.

Dappy clients (browser or programs) do co-resolution, many public resolvers are queried (DNS over HTTPS) for IP addresses or certificates, instead of a single resolver. It removes many attack vectors and allows companies to easily and securely expand digital services.

Dappy provides these instantaneous benefits :
- **Easy and direct management of zones (through API)** : No need to manually connect and update DNS, it can all be automated, there are no DNS registrars, DNS registries, or any other private service.
- No need to work with a Certificate Authority to get a certificate.
- **No need to renew certificates** because dappy does not rely on certificate authorities provided by browsers or operating systems.
- You can easily manage **hundreds of endpoints**, subdomains and TLS configurations with **one JSON file** and simple CLI commands.
- Data exchange is **100x more secure and confidential**, because under a dappy context, browsers do co-resolution for service discovery, your web services are protected against many MITM and cache poisoning scenarios.

We're going to walk you through creating your first domain name in dappy. If you know already a bit about DNS, we're going to create a zone file.

You should get to a working **mydomain.d** website in few minutes only.

## Getting Started

Dappy works a simple blockchain protocol that is specifically designed for names management,  ultra-scalability and efficiency. Dappy is nevertheless expected to migrate mid/long term to a stable and cheap layer 1 blockchain.

Dappy CLI is the only javascript library that we need to use here.

[@fabcotech/dappy-cli on NPM](https://www.npmjs.com/package/@fabcotech/dappy-cli)

```bash
mkdir dappydomain
cd dappydomain
npm init
npm i @fabcotech/dappy-cli@latest --save-dev
```

## Development

You can skip the two following sections as we will take many sortcuts to start playing with the dappy name system. Private keys are directly created for each new account on [gamma.dappy.tech](https://gamma.dappy.tech).

## Knowing or creating a private key (production)

Private key is the critical string that you need to create to manage domain names in dappy, you can use a private key that you already use for Ethereum or any EVM blockchain platform (`secp256k1` algorithm).

If you don't have any, you can create it with one command

```sh
npx @fabcotech/dappy-cli generateprivatekey
```

### Setting up config file (production)

`dappy.config.json` is the only file we'll need to setup. 

You must know only two things to start working:
- A dappy network ID `.options.dappyNetworkId`, you will likely use either `gamma` (the test network with free domain names) or `d` (the production network).
- A private key `.options.privateKey`.

```json title="dappy.config.json"
{
  ...,
  "options": {
    "privateKey": "abcdef",
    "dappyNetworkId": "d"
  }
}
```

We are now set up 😼😼😼. 

Before going further you want want to get familiar with some concepts, checkout [Blockchain and the dappy name system](blockchain_and_the_dappy_name_system.md).

We can also go straight to [creating a zone](create_a_zone.md).

