# Hh

Install [[Pascal|pascal]] compiler according to your distribution package manager first then download the script in your system.

```
$ sudo wget -qO /usr/bin/local/get-chm https://raw.githubusercontent.com/infosecn1nja/red-team-scripts/main/gen-chm.py && \
sudo chmod 755 /usr/bin/local/get-chm
```

Insert commands to create a `.chm` implant.

```
$ get-chm -c "<commands>" -o implant.chm
```

---
## References

- [LOLBAS: Hh](https://lolbas-project.github.io/lolbas/Binaries/Hh/#execute)

- [infosecn1nja: get-chm](https://github.com/infosecn1nja/red-team-scripts/blob/main/gen-chm.py)