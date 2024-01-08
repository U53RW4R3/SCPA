# Recon-ng

## Resolve URLs with IPs

- `resolve` recon-ng module

```
[recon-ng][default] > modules load recon/hosts-hosts/resolve

[recon-ng][default][resolve] > run
```

## Reverse resolve netblocks

- `reverse_resolve` recon-ng module

```
[recon-ng][default] > modules load recon/netblocks-hosts/reverse_resolve

[recon-ng][default][reverse_resolve] > run
```

## Subdomain Bruteforce

- `brute_hosts` recon-ng module
 
```
[recon-ng][default] > marketplace install recon/domains-hosts/brute_hosts

[recon-ng][default][brute_hosts] > modules load recon/domains-hosts/brute_hosts

[recon-ng][default][brute_hosts] > options set SOURCE <domain.com>

[recon-ng][default][brute_hosts] > run
```