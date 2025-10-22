# Lima

## NixOS-based Distros

```
$ nix-env -i lima
```

## Arch-based Distros

Install the packages according to your package manager.

```
$ yay -S --noconfirm lima
```

## Universal Install

```bash
VERSION=$(curl -fsSL https://api.github.com/repos/lima-vm/lima/releases/latest | jq -r .tag_name)
curl -fsSL "https://github.com/lima-vm/lima/releases/download/${VERSION}/lima-${VERSION:1}-$(uname -s)-$(uname -m).tar.gz" | tar Cxzvm /usr/local
curl -fsSL "https://github.com/lima-vm/lima/releases/download/${VERSION}/lima-additional-guestagents-${VERSION:1}-$(uname -s)-$(uname -m).tar.gz" | tar Cxzvm /usr/local
```

---
## References

### Lima

- [Lima](https://lima-vm.io/)