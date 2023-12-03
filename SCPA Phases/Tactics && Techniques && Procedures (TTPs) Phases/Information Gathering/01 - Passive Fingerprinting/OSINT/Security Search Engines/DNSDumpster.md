# DNSDumpster

## Recon-ng

- **`hackertarget` recon-ng module**

```
[recon-ng][default] > marketplace install recon/domains-hosts/hackertarget

[recon-ng][default] > modules load recon/domains-hosts/hackertarget

[recon-ng][default][hackertarget] > options set SOURCE <domain.com>

[recon-ng][default][hackertarget] > options set SOURCE query SELECT DISTINCT host FROM hosts WHERE host IS NOT NULL

[recon-ng][default][hackertarget] > run

[recon-ng][default][hackertarget] > back
```

- **`resolve` recon-ng module**

```
[recon-ng][default] > modules load recon/hosts-hosts/resolve

[recon-ng][default][resolve] > run

[recon-ng][default][resolve] > back

[recon-ng][default] > modules load recon/netblocks-hosts/reverse_resolve

[recon-ng][default][reverse_resolve] > run
```

---
## References

- [DNSDumpster](https://dnsdumpster.com)