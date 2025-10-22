# SSH Keys

```
"-----BEGIN OPENSSH PRIVATE KEY-----" inurl:id_rsa

"-----BEGIN RSA PRIVATE KEY-----" inurl:id_rsa

intitle:"index of /" ssh

intitle:"index of" id_rsa -id_rsa.pub

filetype:pem intext:private

intitle:"index of" ".ssh" OR "ssh_config" OR "ssh_known_hosts" OR "authorized_keys" OR "id_rsa" OR "id_dsa"

filetype:reg reg HKEY_CURRENT_USER SSHHOSTKEYS

filetype:log "username putty"
```