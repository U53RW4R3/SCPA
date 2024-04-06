# Credential Combolist

Search Tags: #credential-stuffing

- Combine usernames and passwords.

`$ awk 'NR==FNR {a[FNR]=$1; next} {print a[FNR] ":" $1; }' users.lst passwords.lst > combolist.lst`

- Combine usernames and NTLM hashes.

`$ awk 'NR==FNR {a[FNR]=$1; next} {print a[FNR] ":" $1; }' users.lst hashes.lst > combolist.lst`