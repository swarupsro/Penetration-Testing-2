###### Bypass WAFs by Shortening IP Address (by [0xInfection](https://twitter.com/0xInfection))

IP addresses can be shortened by dropping the zeroes:

```
http://1.0.0.1 → http://1.1
http://127.0.0.1 → http://127.1
http://192.168.0.1 → http://192.168.1

http://0xC0A80001 or http://3232235521 → 192.168.0.1
http://192.168.257 → 192.168.1.1
http://192.168.516 → 192.168.2.4
```
  > This bypasses WAF filters for SSRF, open-redirect, etc where any IP as input gets blacklisted.

For more information please see [How to Obscure Any URL](http://www.pc-help.org/obscure.htm) and [Magic IP Address Shortcuts](https://stuff-things.net/2014/09/25/magic-ip-address-shortcuts/).
