# Web Browsers

## TOR Browser

Download the TOR browser and verify the tarball file has not been tampered. If it's legitimate then you can use it.

```
$ gpg --auto-key-locate nodefault,wkd --locate-keys torbrowser@torproject.org && \
    gpg -o tor.keyring --export 0xEF6E286DDA85EA2A4BA7DE684E2C6E8793298290

$ gpg --verify --keyring tor.keyring ~/Downloads/tor-browser-linux-x86_64-13.0.1.tar.xz.asc ~/Downloads/tor-browser-linux-x86_64-13.0.1.tar.xz
gpg: Signature made Wed 25 Oct 2023 01:29:40 PM UTC
gpg:                using RSA key 613188FC5BE2176E3ED54901E53D989A9E2D47BF
gpg: Good signature from "Tor Browser Developers (signing key) <torbrowser@torproject.org>" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: EF6E 286D DA85 EA2A 4BA7  DE68 4E2C 6E87 9329 8290
     Subkey fingerprint: 6131 88FC 5BE2 176E 3ED5  4901 E53D 989A 9E2D 47BF

$ tar xJvf ~/Downloads/tor-browser-linux-x86_64-13.0.1.tar.xz -C ~/Documents/
```

---
## References

### TOR

- [TOR Project](https://www.torproject.org)

### Mullvad

- [Mullvad Browser](https://mullvad.net/en/download/browser)

### EFF

- [EFF: Cover Your Tracks](https://coveryourtracks.eff.org)