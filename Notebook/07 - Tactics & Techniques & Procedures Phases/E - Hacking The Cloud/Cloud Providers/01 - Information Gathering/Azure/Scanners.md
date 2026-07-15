# Scanners

https://github.com/nyxgeek/o365recon
https://github.com/dafthack/MSOLSpray
https://github.com/dafthack/MFASweep
https://github.com/nyxgeek/onedrive_user_enum

## `httpx`

```
$ httpx -silent -l urls.txt -p https:443 -server -mr 'Azure Cloud' -o live-azure.txt

$ awk -F "/" '{print "s3://"$3}' live-azure.txt | sort -uo azure-output.txt
```

---
## References

### HackingTheCloud

- [HackingTheCloud](https://hackingthe.cloud/aws/general-knowledge/aws_organizations_defaults/)

### Security Cafe

- [Security Cafe: Pentesting Azure - RECON Techniques](https://securitycafe.ro/2022/04/29/pentesting-azure-recon-techniques/)