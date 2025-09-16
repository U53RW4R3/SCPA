# README

## `httpx`

```
$ httpx -silent -l urls.txt -p https:443 -server -mr 'Google Cloud' -o live-gcp.txt

$ awk -F "/" '{print "s3://"$3}' live-gcp.txt | sort -uo gcp-output.txt
```

---
## References

### HackingTheCloud

- [HackingTheCloud](https://hackingthe.cloud/aws/general-knowledge/aws_organizations_defaults/)