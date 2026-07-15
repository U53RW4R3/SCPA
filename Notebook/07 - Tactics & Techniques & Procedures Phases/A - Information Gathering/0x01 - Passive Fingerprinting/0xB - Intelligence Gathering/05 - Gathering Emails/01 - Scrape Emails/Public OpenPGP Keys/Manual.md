# Manual

## OpenPGP Keyservers

```
https://keyserver.pgp.com
https://keys.openpgp.org
https://keys.mailvelope.com/manage.html
https://pgp.mit.edu
https://keyring.debian.org
https://keyserver.ubuntu.com
https://pgp.surf.nl
```

Receive the keys without importing it.

```
$ gpg --batch --keyserver hkps://<keyserver_IP>[:443] --search-keys <fingerprint>

$ gpg --batch --keyserver hkp://<keyserver_IP>[:80] --search-keys <fingerprint>
```

## Keybase

```
$ curl -s https://keybase.io/<username>/pgp_keys.asc | gpg -q

$ wget -qO- https://keybase.io/<username>/pgp_keys.asc | gpg -q
```

---
## References

### Keybase

- [Keybase](https://keybase.io/)

- [Keybase Documentation: API](https://keybase.io/docs/api/1.0/call/user/pgp_keys.asc)