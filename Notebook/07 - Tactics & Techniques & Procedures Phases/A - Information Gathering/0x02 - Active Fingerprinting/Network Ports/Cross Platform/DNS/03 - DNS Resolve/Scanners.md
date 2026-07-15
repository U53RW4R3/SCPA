# Scanners

## #gobuster 

TODO: Fill this info

```
$ gobuster dns -r resolvers.txt
```

## #sn0int 

## Recon-ng

TODO: Convert it to `sn0int`

### Resolve URLs with IPs

- `resolve` recon-ng module

```
[recon-ng][default] > modules load recon/hosts-hosts/resolve

[recon-ng][default][resolve] > run
```

### Reverse resolve netblocks

- `reverse_resolve` recon-ng module

```
[recon-ng][default] > modules load recon/netblocks-hosts/reverse_resolve

[recon-ng][default][reverse_resolve] > run
```