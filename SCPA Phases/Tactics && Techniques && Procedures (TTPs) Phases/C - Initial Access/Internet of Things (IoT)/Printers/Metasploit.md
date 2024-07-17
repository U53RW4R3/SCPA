# Metasploit

## 01 - Auxiliary

TODO: Check every MSF auxiliary module related to printers

### 1.1 - Generic

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

### 1.2 - Canon

```
msf > use auxiliary/scanner/printer/canon_iradv_pwd_extract
```

### 1.3 HP

```
auxiliary/scanner/snmp/snmp_enum_hp_laserjet

auxiliary/scanner/http/hp_sys_mgmt_login
```