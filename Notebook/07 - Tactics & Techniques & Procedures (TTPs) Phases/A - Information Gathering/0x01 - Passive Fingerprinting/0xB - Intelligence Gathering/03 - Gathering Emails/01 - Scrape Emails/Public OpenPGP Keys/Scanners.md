# Scanners

## sn0int

TODO: Convert this to `sn0int`

- `pgp_search` recon-ng module

```
[recon-ng][default] > marketplace install recon/domains-contacts/pgp_search

[recon-ng][default] > modules load recon/domains-contacts/pgp_search

[recon-ng][default][pgp_search] > options set SOURCE <domain.com>

[recon-ng][default][pgp_search] > run

[recon-ng][default][pgp_search] > back
```

## Spiderfoot

```
$ ./sf.py -m sfp_pgp -s <domain.com> -F "Affiliate - Email Address"
```