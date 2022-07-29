---
sidebar_position: 6
---

# Check the hello world website

Now let's load the "hello world !" website. We first need to launch the web server that is provided by default by dappy CLI. The TLS key and certificate are hard-coded into the codebase, and match the one in the zone.

```bash
npx dappy-cli helloworldserver
```

you should have the following log :

```
2022-07-28T13:57:12.001Z Running helloworld TLS server
(helloworld) listenning on 127.0.0.1:3008
```

Now everything is setup, we can open dappy browser and load `helloworld.d:3008`.

**💡 Note :** By default, browsers will of course try port 443 for HTTPS connections, in order to avoid listenning to the 443 port, we arbitrarily chose port 3008.

![Hello world in dappy browser](/img/helloworld_dappybrowser.png)