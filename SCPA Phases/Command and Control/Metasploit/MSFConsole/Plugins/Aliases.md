# Aliases

Allows you to create aliases to not just modules but other variables as well. Append this in the `~/.msf4/msfconsole.rc` when running `msfconsole` on startup.

```
$ sudo cat > /root/.msf4/msfconsole.rc << EOF
load alias

# Scanner

alias portscan_tcp 'use auxiliary/scanner/portscan/tcp'
alias smb_version 'use auxiliary/scanner/smb/smb_version'
alias smb_login 'use auxiliary/scanner/smb/smb_login'

# SMB

alias smb_download 'use auxiliary/admin/smb/download_file'
alias smb_upload 'use auxiliary/admin/smb/upload_file'
alias smb_delete 'use auxiliary/admin/smb/delete_file'

# PsExec

alias psexec 'use exploit/windows/smb/psexec'

# Eternalblue

alias eternalblue 'use exploit/windows/smb/ms17_010_eternalblue'
alias eternalblue_exec 'use auxiliary/admin/smb/ms17_010_command'
alias eternalblue_psexec 'use exploit/windows/smb/ms17_010_psexec'

# Enumeration

alias windows_arp_scan 'use post/windows/gather/arp_scanner'
alias ad_computers 'use post/windows/gather/enum_ad_computers'
alias ad_comments 'use post/windows/gather/enum_ad_user_comments'
alias ad_to_sqllite 'use post/windows/gather/ad_to_sqlite'
alias dll_inject 'use post/windows/manage/reflective_dll_inject'

# Credendials

alias windows_hashdump 'use post/windows/gather/hashdump'
alias cred_gpp 'use post/windows/gather/credentials/gpp'
alias ntds_util 'use post/windows/gather/file_from_raw_ntfs'
EOF
```

---
## References

- [Metasploit Documentation: Metasploit Plugins](https://docs.metasploit.com/docs/using-metasploit/intermediate/how-to-use-plugins.html)