# README

```
$ httpx -silent -l urls.txt -p https:443 -server -mr 'Terraform' -o live-terraform.txt

$ awk -F "/" '{print "s3://"$3}' live-terraform.txt | sort -uo terraform-output.txt
```

---
## References

### HackingTheCloud

- [HackingTheCloud](https://hackingthe.cloud/aws/general-knowledge/aws_organizations_defaults/)