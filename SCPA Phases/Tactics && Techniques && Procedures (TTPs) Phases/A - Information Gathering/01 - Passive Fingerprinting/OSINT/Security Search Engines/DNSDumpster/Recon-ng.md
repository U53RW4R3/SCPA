# Recon-ng

- `hackertarget` recon-ng module

```
[recon-ng][default] > marketplace install recon/domains-hosts/hackertarget

[recon-ng][default] > modules load recon/domains-hosts/hackertarget

[recon-ng][default][hackertarget] > options set SOURCE <domain.com>

[recon-ng][default][hackertarget] > options set SOURCE query SELECT DISTINCT host FROM hosts WHERE host IS NOT NULL

[recon-ng][default][hackertarget] > run

[recon-ng][default][hackertarget] > back
```