# Dorks

## Google

```
(site:*.s3.amazonaws.com OR site:*.s3-external-1.amazonaws.com OR site:*.s3.dualstack.us-east-1.amazonaws.com OR site:*.s3.ap-south-1.amazonaws.com) "domain.tld"
```

Passwords.

```
site:s3.amazonaws.com filetype:xls password
```

## Github

```
path:.env AWS_KEY /(AKIA[A-Z0-9]{12,})/
"AWSSecretKey"
"amazonaws"
"aws_access"
"aws_access_key_id"
"aws_key"
"aws_secret"
"aws_token"
filename:credentials aws_access_key_id
org:<organization> "AWS_ACCESS_KEY_ID"
org:<organization> "list_aws_accounts"
org:<organization> "aws_access_key"
org:<organization> "aws_secret_key"
org:<organization> "bucket_name"
org:<organization> "S3_ACCESS_KEY_ID"
org:<organization> "S3_BUCKET"
org:<organization> "S3_ENDPOINT"
org:<organization> "S3_SECRET_ACCESS_KEY"
AWS SECRET
AWS_SECRET_ACCESS_KEY
```

---
## References

### Amazon

- [Amazon: EC2 Reachability Test](http://ec2-reachability.amazonaws.com/)

- [lord-alfred: ipranges](https://github.com/lord-alfred/ipranges) ^2cb0fa

### Gray Hat Warefare

- [Gray Hat Warefare](https://buckets.grayhatwarfare.com)

### kaeferjaeger

- [kaeferjaeger: SNI IP Ranges](https://kaeferjaeger.gay/?dir=sni-ip-ranges)