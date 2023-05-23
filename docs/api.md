---
sidebar_position: 9
---

# API reference

Every node of the dappy network exposes endpoints, allowing programs to query the data of the dappy name system, mainly records from zones. **Users or clients of .d domains are supposed to do co-resolution**, and should not trust a single answer given by a node, this is why [dappy-lookup](https://github.com/fabcotech/dappy-tools/tree/master/packages/dappy-lookup) library (it can be a CLI or SDK) exists, [dhttps](https://github.com/fabcotech/dhttps) is also based on dappy-lookup and does co-resolution under the hood.

Although nodes often expose their API through the DNS+CA system, you are supposed to query them directly though IP + self signed certificate. [dappy-lookup knows](https://github.com/fabcotech/dappy-tools/blob/master/packages/dappy-lookup/src/dappyNetworks.ts) the IP addresses and TLS certificates for each node, and does co-resolution.

## DNS-over-HTTPS endpoint

A node of the dappy network will expose a DoH compatible endpoint, `/dns-query`, with `Content-Type: application/dns-message` (see [RFC8484](https://www.rfc-editor.org/rfc/rfc8484)). Nevertheless, since DoH imposes limitation on the size of the responses, we can't really rely on it for CERT records, we decided to add simple JSON endpoints.

## JSON endpoints

[domain] is to be replaced by the domain you want to resolve

### Retrieve A records

```bash
GET or POST /[domain]/A
ex: GET https://node1.d.fabco.tech/dappy.d/A
```

[node1.d.fabco.tech/dappy.d/A](https://node1.d.fabco.tech/dappy.d/A)

```json
{"records":[{"data":"134.209.84.129","name":"@","type":"A"}]}
```

### Retrieve AAAA records

```bash
GET or POST /[domain]/AAAA
ex: GET https://node1.d.fabco.tech/dappy.d/AAAA
```

[node1.d.fabco.tech/dappy.d/AAAA](https://node1.d.fabco.tech/dappy.d/AAAA)

```json
{"records":[{"data":"2001:0db8:85a3:0000:0000:8a2e:0370:7334","name":"@","type":"AAAA"}]}
```

### Retrieve CERT records

```bash
GET or POST /[domain]/CERT
ex: GET https://node1.d.fabco.tech/dappy.d/CERT
```

```json
{"records":[{"data":"LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUROakNDQWg2Z0F3SUJBZ0lVWDhPZDEwUE1jU29KRFpndnAzZXVDSmtlVHVJd0RRWUpLb1pJaHZjTkFRRUwKQlFBd0dqRVlNQllHQTFVRUF3d1BaR1ZtWVhWc2RDNWtZWEJ3ZVM1a01CNFhEVEl5TVRBeU1EQTVNVEl6TUZvWApEVE14TURFd05qQTVNVEl6TUZvd0dqRVlNQllHQTFVRUF3d1BaR1ZtWVhWc2RDNWtZWEJ3ZVM1a01JSUJJakFOCkJna3Foa2lHOXcwQkFRRUZBQU9DQVE4QU1JSUJDZ0tDQVFFQXBHOW8wNGVFM0ZuYUtEOVZkcG5hZnk0dnNEZE4KcGJFWGx3cVpEeHB2Z3F1b3Z4VllQQXRIU25LSXVHTjBHdWt0TitnUE16YktNdzU3SWhyM2gvQXpsRXhtUnZpTgpkMjByQnNTNkMzVHRibTBYNDRuRUJhQ1RISVdoZ1NQYXlEYmUxM3pzeDlMT3dHUXM3QXByaW9FNjZuaENqM2szCjJHYVp5QkdtSmd5QnRLSEJhajUxWXJGTGdaMVYrR3crOGRLOGZVcWg1SEYwbXJvaUd5TG0vRVBpRXpyYUlNRzUKVUZ0WENIRjFNTWN3NkRHQmhsUk8yOXhYZGNmd1JaYjBadEVwSjh3c2VLRXp2QmJneDB1cm56b0ZGcW5iTGVQSAo2NGhhL1ZDWFR2Qk5JeFFQcmU2empFWktwdEh5RU9Ma1k3MVgrU2Fud1M1a1pLTm9KZk1QTWxKTE5RSURBUUFCCm8zUXdjakJSQmdOVkhSRUVTakJJZ2c5a1pXWmhkV3gwTG1SaGNIQjVMbVNDQjJSaGNIQjVMbVNDREhSbGMzUXUKWkdGd2NIa3VaSUlOZEdWemRESXVaR0Z3Y0hrdVpJSVBaWGhoYlhCc1pTNWtZWEJ3ZVM1a01CMEdBMVVkRGdRVwpCQlJJdzdXQUdjTTRDV3V1WDgrUExDcW9Uc3VPeWpBTkJna3Foa2lHOXcwQkFRc0ZBQU9DQVFFQW1vc01sVHA4CmxjbUhnYlBKTkFxUDFRTUZmdTJkSVVHWFFodkZLSThTN3JxVUIyeE56VktUZXlqMXgzRnk1M3Jma3M3ZTNIbCsKVm1zMS9lUDZ0QU5aZ1VkM0NsZ2ZEb0dVZmFtSFlRQUQyRHlBTkJPbktoZlFWbzd3aENWcG9VR1VNS2dGWjlwVworTFhHRFZRSE5mTVF2SElISmJ2MHpCSDU0NE9FWTNPL1AySFI1dkF2VGZzcTE1L2FjMXN1bjN6UWp4NHM5L052ClF5bmJ6K0NOemFRZUNLRXdFNGE4VDRBaG5BZnlQNDdvUnJ2THZCcXN1RTE2MHBabTVnY051TnZTZlRTTStlSkEKLzlVYnhueXZPZ0pqOHAycE5CV041L1ZBblJwQmVjc1RkMm1HK0Fsajd2Vytjck56VzYwd2p0K1NhUjhQL1hjcwp1RUtvK1B6ZTBRRHg2QT09Ci0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K","name":"@","type":"CERT"}]}
```

[node1.d.fabco.tech/dappy.d/CERT](https://node1.d.fabco.tech/dappy.d/CERT)

Be careful, as CERT records are base64 encoded

### Retrieve TXT records

```bash
GET or POST /[domain]/TXT
ex: GET https://node1.d.fabco.tech/dappy.d/TXT
```

[node1.d.fabco.tech/dappy.d/TXT](https://node1.d.fabco.tech/dappy.d/TXT)

```json
{"records":[{"data":"OWNER=0427fc3b97535a022a271ceaaecf518ebc218b46d579e4058cf0830f4e56f652a04bdc93542e812b342fef0a5a6f92b11ca2ac96895e5bc6db2fd38a3341ea4f42","name":"@","type":"TXT"}]}
```
