# 04 - DNSSEC

Query the **Key ID** of the **Key Signing Key (KSK)** of the domain **(DNSKEY)**.

```
$ dig DNSKEY <domain.com> +multiline @<DNS_IP>
```

The **RRSIG A** record of the domain

```
$ dig A <domain.com> +multiline @<DNS_IP> +noadditional +dnssec +multiline
```

Retrieve information of the **Salt** used for the hash calculation for **NSEC3 (NSEC3PARAM)**

```
$ dig NSEC3PARAM <domain.com> @<DNS_IP>
```

Lookup **RRSIG** records that exists for the organization's domain

```
$ dig RRSIG <domain.com> +short @<DNS_IP>
```

---
## References

### Backlinks

- [[References DNS Records]]

### Hacktricks

- [Hacktricks: Pentesting DNS](https://book.hacktricks.xyz/pentesting/pentesting-dns)