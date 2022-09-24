---
sidebar_position: 3
---

# Get a domain

## Enrivonments

Two environments are actively maintained, one for production one for testing.

`d` network (production) : [https://app.dappy.tech](https://app.dappy.tech)

`gamma` network (for testing) : [https://gamma.dappy.tech](https://gamma.dappy.tech)

## Get domain names for free (development)

Just visit [gamma.dappy.tech/now/](https://gamma.dappy.tech/now/) and wait for 5 seconds, you'll have an account and domain name after 5 seconds. You'll probably have to wait around 5 minutes for the domain name to get the "transfered" status.

You can also choose your domain name by going through the regular interface [gamma.dappy.tech](https://gamma.dappy.tech). 

You should be able to download the entire **dappy.config.json** file and copy it in your repo. It includes the private key that has been created for you.

## Purchase domain name (production)

If you work with the `d` network (mainnet) you'll need to go through credit card payment.

Once you have purchased a domain name, input your public key in the `Orders` tab and wait few minutes to get the status `Transfered to public key`.

```bash
npx @fabcotech/dappy-cli printpublickey
```

![Transfered to public key](/img/transfered_to_public_key.png)

You should be able to download the entire **dappy.config.json** file and copy it in your repo. Be careful, in production environment, private key is never sent to the website, once you have downloaded it you'll have to add your private key in the JSON file manually.
