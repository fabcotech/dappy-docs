---
sidebar_position: 5
---

# Upload the zone

The zone is configured but not yet uploaded on the blockchain, nor the NFT reserved. We should have everything we need.

```bash
npx dappy-cli pushzones
```

The logs should look something like this

```
2022-07-28T12:17:38.493Z Push zones
2022-07-28T12:17:38.512Z host (read-only):  http://127.0.0.1:40403
2022-07-28T12:17:38.512Z host (validator):  http://127.0.0.1:40403
2022-07-28T12:17:38.512Z shard ID        :  dev
2022-07-28T12:17:38.512Z public key :       abcdef
2022-07-28T12:17:38.512Z Compiling !
2022-07-28T12:17:38.809Z box found
2022-07-28T12:17:39.681Z purse helloworld not found, lets SWAP it with wrapped REV
2022-07-28T12:17:39.681Z will do rchain-token.CREDIT and rchain-token.SWAP operations
2022-07-28T12:17:59.995Z will do rchain-token.UPDATE_PURSE_DATA operation
2022-07-28T12:18:08.278Z Now trying to get zone/NFT from the blockchain...
2022-07-28T12:18:08.624Z Zone successfuly deployed in name system !
2022-07-28T12:18:08.624Z masterRegistryUri :                t6agckxmjfoyf7mbkft9d81hmjajerj1ki4ro557a75uhp6nmqgcxg
2022-07-28T12:18:08.624Z contract id :                      t6adappynamesystem
2022-07-28T12:18:08.624Z zone id :                          helloworld
2022-07-28T12:18:08.625Z Box owning this zone/NFT:          t6a554283
```

If for some reason `helloworld` is already taken on the name system you are working with. Feel free to change it to anything else. The TLS certificate should work with any domain (wildcard).

You will need to generate a certificate as well, which is not the one provided by default by dappy CLI, check [certificate](certificate.md).

**Hundreds of TLDs, subdomains, one JSON file**

By looking at the `dappy.config.json` file you should understand that you can manage hundreds of zone files, TLDs and subdomains with only this JSON file. This is how simple it gets 👌👌👌 !