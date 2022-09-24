---
sidebar_position: 6
---

# Check the hello world website

Now let's load the "hello world !" HTTPS website. We first need to launch the web server that is provided by default by dappy CLI. The TLS key and certificate are hard-coded into the codebase, and match the one in the zone.

```bash
npx @fabcotech/dappy-cli helloworldserver --cert mydomain.crt --key mydomain.key
```

you should have the following log :

```
(helloworld) listenning on 127.0.0.1:3008
```

Now everything is setup, we can open dappy browser and load `mydomain.d:3008` or `mydomain.gamma:3008`.

**💡 Note :** By default, browsers will of course try port 443 for HTTPS connections, in order to avoid listenning to the 443 port, we arbitrarily chose port 3008.

![Hello world in dappy browser](/img/helloworld_dappybrowser.png)
