# LaZagne

## 01 - Compile

### 1.1 - Nuitka

Refer to this [[01 - Command Line/E - Compilers/Cross Platform/Python|section]] to install `python` in a `wine` environment.

```
$ git clone https://github.com/AlessandroZ/LaZagne.git

$ cd LaZagne/Windows/lazagne/

$ wine python -m nuitka [--follow-imports] --standalone --onefile --include-package=lazagne laZagne.py
```

### 1.2 - Pyinstaller

```
$ wine pyinstaller --additional-hooks-dir=. -F laZagne.py
```

---
## References

### Source Repositories

- [LaZagne](https://github.com/AlessandroZ/LaZagne)

### Assume Breach

- [Assume Breach: Let’s Evade AV And Run Lazagne](https://assume-breach.medium.com/homegrown-red-team-lets-evade-av-and-run-lazagne-af97e035de22)