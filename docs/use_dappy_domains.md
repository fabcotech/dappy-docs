---
sidebar_position: 8
---

# Use dappy domains

Dappy is a long term and ambitious project, right now browsers don't support .d or .gamma domains. It means that you cannot use .d domains, and benefits from co-resolution for web applications, you may only use dappy in nodeJS programs that perform HTTPS calls to APIs, or in any other environment that supports resolving .d domains.

## node JS

[dhttps](https://github.com/fabcotech/dhttps) allows you to seamlessly use .d and .gamme domains in any nodeJS program.

```ts
import dhttps from "@fabcotech/dhttps";

dhttps.get("https://dappy.d", (res) => {
  res.on("data", (c: any) => {
    console.log(c.toString("utf8"));
  });
});
```
