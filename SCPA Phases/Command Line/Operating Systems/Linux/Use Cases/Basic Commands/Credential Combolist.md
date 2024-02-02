# Credential Combolist

Search Tags: #credential-stuffing

`$ awk 'NR==FNR {a[FNR]=$1; next} {print a[FNR] ":" $1; }' users.lst passwords.lst > combolist.lst`