---
author(s):
  - Userware
tags:
  - offensive-infrastructure
---
# Software Packaging

## MSI

^4ab6c2

### `msitools`

Install the packages according to your package manager.

```
$ sudo apt install -y msitools wixl

$ sudo dnf install -y msitools wixl

$ sudo pacman -S --noconfirm msitools
```

### .NET

Install the package.

```
$ dotnet tool install -g wix
```

Append the `PATH` variable.

```
$ echo "export PATH=\"\$PATH:\$HOME/.dotnet/tools\"" >> ~/.bashrc

$ echo "export PATH=\"\$PATH:\$HOME/.dotnet/tools\"" >> ~/.zshrc
```

Refresh the shell prompt by importing the resource file.

```
$ source ~/.bashrc

$ source ~/.zshrc
```

---
## References

### Source Repositories

- [GNOME `msitools`](https://gitlab.gnome.org/GNOME/msitools)

### GNOME

- [GNOME: `msitools`](https://wiki.gnome.org/msitools)