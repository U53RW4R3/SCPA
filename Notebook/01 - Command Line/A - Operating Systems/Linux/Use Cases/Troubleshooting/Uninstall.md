# Uninstall

## Remove Windows Programs

Display installed programs.

```
$ winetricks -q [prefix=/path/to/wine_env/directory/] list-installed

$ WINEDEBUG=-all WINEARCH=<win64 | win32> [WINEPREFIX=/path/to/wine_env/directory/] wine uninstaller --list
```

Uninstall the software.

```
$ WINEDEBUG=-all WINEARCH=<win64 | win32> [WINEPREFIX=/path/to/wine_env/directory/] wine uninstaller --remove {<GUID>}
```

## Remove Python Packages

Search for a specific package that causes conflict or software breakage.

```
$HOME/.local/lib/python3.*
/usr/local/lib/python3.*
```