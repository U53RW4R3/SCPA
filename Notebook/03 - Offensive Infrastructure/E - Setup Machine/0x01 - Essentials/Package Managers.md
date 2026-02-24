---
author(s):
  - Userware
tags:
  - offensive-infrastructure
---
# Package Managers

## #winetricks

List the packages

```
$ winetricks apps list

$ winetricks dlls list

$ winetricks fonts list
```

Install the package. Optionally specify the `WINEPREFIX` that's been configured and ensure to pass the architecture to avoid errors.

```
$ winetricks -f -q [prefix=/path/to/wine_env/directory/] [arch=<32 | 64>] <package>
```

## Uninstall

### Remove Windows Programs

Display installed programs.

```
$ winetricks -q [prefix=/path/to/wine_env/directory/] list-installed

$ WINEDEBUG=-all WINEARCH=<win64 | win32> [WINEPREFIX=/path/to/wine_env/directory/] wine uninstaller --list
```

Uninstall the software.

```
$ WINEDEBUG=-all WINEARCH=<win64 | win32> [WINEPREFIX=/path/to/wine_env/directory/] wine uninstaller --remove {<GUID>}
```