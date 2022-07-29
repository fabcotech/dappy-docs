---
sidebar_position: 1
---

# Introduction

Hey there welcome on the offical dappy docs 🚀😉.

Dappy is a public open source name system that uses the blockchain, and a zero-trust co-resolution system. It has been engineered specifically for high value usecases, therefore it is a good fit for enterprises web applications, cryptocurrency, B2B or any web application (or API) that needs high security and confidentiality.

Dappy clients (browser or programs) do co-resolution, many public resolvers are queried (DNS over HTTPS) for IP addresses or certificates, instead of a single resolver. It removes many attack vectors and allows companies to deploy ultra-secure and confidential internet facing web services, very easily and cheaply.

Dappy provides these instantaneous benefits :
- **No DNS registrar, DNS registry** or any other private service to connect to.
- No need to work with a Certificate Authority to get a certificate.
- **No need to renew certificates** (not always true though).
- You can easily manage **hundreds of endpoints**, subdomains and TLS configurations with **one JSON file**.
- People accessing your service will do co-resolution for service discovery, your web services are therefore protected against many MITM and cache poisoning scenarios.

We're going to walk you through creating your first decentralized domain name (zone file basically) with the blockchain and dappy tools.

You should get to a working **helloworld.d** website in few minutes only.

## Getting Started

Dappy works with [RChain](https://rchain.coop), a non-EVM, POS blockchain that uses concurrency for cheaper transaction costs and very high throughput.

We advise you to work with the testnet first, but you can also any other RChain network, obviously mainnet if you want to purchase a true TLD, or local dev blockchain [see this page to run a local blockchain](https://rchain.coop/developer.html). In any case, start by creating a repo.

Right now the tooling is built on nodeJS and javascript. We hope that someday CLI and programs will also be available in other languages, feel free to [reach out to us](https://discord.gg/8Cu5UFV) (or not) if you want to build anything in Rust, Go or any other language.

[@fabcotech/dappy-cli on NPM](https://www.npmjs.com/package/@fabcotech/dappy-cli)

```bash
mkdir dappydomain
cd dappydomain
npm init
npm i @fabcotech/dappy-cli@latest --save-dev
```

## Setting up config file

Checkout [environments](environments.md) if you want to know up to date variables for testnet, mainnet and maybe other networks.

`dappy.config.json` is the only file we'll need to setup. 

In addition to the environments variables, you must know :
- A private key `privateKey` that has (testnet)REV
- (optional) A box ID `boxId` that starts with the same 3 letters as master registry URI. If you don't set up one it will be automatically created 😉.

```json title="dappy.config.json"
{
  "options": {
    "platform": "rchain",
    "readOnly": "https://...",
    "validator": "https://...",
    "shardId": "testnetx",
    "masterRegistryUri": "abddefghij",
    "nameSystemContractId": "abddappynamesystem",
    "privateKey": "abcdef",
    "boxId": ""
  }
}
```

We should already be able to run the command to push zones to the blockchain 😼😼😼. 

```bash
npx dappy-cli pushzones
```

Since we have not configured any zone, we should have an error, the logs should look something like this, it means we're ok 💪.

```
2022-07-28T10:05:11.138Z Push zones
2022-07-28T10:05:11.161Z host (read-only):  http://127.0.0.1:40403
2022-07-28T10:05:11.161Z host (validator):  http://127.0.0.1:40403
2022-07-28T10:05:11.161Z shard ID        :  dev
2022-07-28T10:05:11.161Z public key :       04be064356846e36e485408df50b877dd99ba406d87208add4c92b3c7d4e4c663c2fbc6a1e6534c7e5c0aec00b26486fad1daf20079423b7c8ebffbbdff3682b58
2022-07-28T10:05:11.161Z Compiling !
2022-07-28T10:05:11.483Z box found
Error: No zone to deploy, cannot find config.zone, or zero zones
```

First you may want to know a bit more about dappy, checkout [Blockchain and the dappy name system](blockchain_and_the_dappy_name_system.md) before going further.

