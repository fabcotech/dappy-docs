---
sidebar_position: 8
---

# Nginx and apache setup

Two commmands can help you configure the TLS endpoints on your web servers.

```bash
# Nginx configuration files
node index.js nginx --host mydomain

# Commands that you can just copy and paste
# to create nginx configuration, cert and 
# key files
node index.js nginx --host mydomain --commands

# Apache configuration files
node index.js apache --host mydomain

# Commands that you can just copy and paste
# to create apache configuration, cert and 
# key files
node index.js apache --host mydomain --commands
```