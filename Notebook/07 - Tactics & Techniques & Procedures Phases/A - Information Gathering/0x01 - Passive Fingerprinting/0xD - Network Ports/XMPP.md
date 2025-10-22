# XMPP

## 01 - Check Remote Certificates

```
$ openssl s_client -showcerts -starttls xmpp -connect <IP>:5222
```

## 02 - Debug Mode

Using `pidgin` with debug mode that allows further enumeration such as, an active directory environment that leads to ASREPRoast attack.

```
$ pidgin -d
```

---
## References

### BishopFox

- [BishopFox: XMPP - An Under-appreciated Attack Surface](https://bishopfox.com/blog/xmpp-underappreciated-attack-surface)

### H3llKa1ser

- [H3llKa1ser: XMPP Jabber Pentesting](https://h3ll-ka1ser.gitbook.io/boot2root/network-penetration-testing/xmpp-jabber-pentesting)