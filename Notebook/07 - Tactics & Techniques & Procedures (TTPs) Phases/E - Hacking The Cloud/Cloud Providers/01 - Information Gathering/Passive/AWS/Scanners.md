# Scanners

## `katana`

```
$ katana -u <URL> -d 5 -jc | grep '\.js$' | tee alljs.txt

$ cat alljs.txt | xargs -I {} curl -s {} | grep -Eo 'http[s]?://[^"]*.s3.amazonaws.com' | sort -uo live-s3-buckets.txt
```

---
## References

### Source Repositories

- [nahamsec: lazys3](https://github.com/nahamsec/lazys3)

- [sa7mon: S3Scanner](https://github.com/sa7mon/S3Scanner)

- [jordanpotti: cloudscraper](https://github.com/jordanpotti/cloudscraper)

### HackingTheCloud

- [HackingTheCloud](https://hackingthe.cloud/aws/general-knowledge/aws_organizations_defaults/)