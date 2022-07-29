---
sidebar_position: 3
---

# Blockchain and the dappy name system

If you are already familiar with managing the DNS of your company or personal domain names, you will be very comfortable managing domain names in the dappy name system. Dappy zones follow the JSON format specified in [this RFC](https://tools.ietf.org/id/draft-bortzmeyer-dns-json-01.html) by IETF / AFNIC.

## Few concepts

There are concepts you may want to understand out first (but you can also skip).

#### What is a domain name in the dappy name system ?

A domain name is an entry into a NFT smart contract on the blockchain. This NFT smart contract is the dappy name system contract. You are probably familiar with images as NFT, in reality you can associate any data you want with a NFT. The core property of a NFT is in reality it's unique address. NFTs in the dappy name system have a unique ID, they are identified by a string with only a-z0-9 characters.

#### How should I pay for a domain name ? And how much ?

There is a fixed price, same for everyone for having a TLD in the dappy name system. Nevertheless it may vary over time, the companies that secure the dappy network can decide to change it based on insights or strategic choices.

A smart contract runs the name system, therefore we must **pay with cryptocurrency**. If can also use [app.dappy.tech](https://app.dappy.tech) (website owned and secured by FABCO), pay with credit card and have proper invoice.

#### If I have a TLD why is there a .d at the end ?

It does not matter that much if we call `hello.d` a TLD or second level domain. The `.d` at the end of domain names in dappy is a visual indicator that we are dealing with no-DNS dappy domain names. In dappy there is no corporation that manages or stored the domain (like Verisign for .com for example), therefore we can call `hello.d` a TLD.

#### How do you deal with famous brands like apple and amazon ?

There is a list of reserved domain names based on 10.000+ top level domains, top second level domains and top brands. The dappy network will make sure that only legitimate owners purchase those reserved lists.

[github.com/fabcotech/dappy-reserved-domains](https://github.com/fabcotech/dappy-reserved-domains)
