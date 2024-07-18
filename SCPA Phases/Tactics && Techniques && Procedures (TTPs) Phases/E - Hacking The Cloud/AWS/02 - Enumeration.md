# Enumeration

TODO: Provide steps for enumeration to escalate for initial foothold with the permissions

- Read - List and view all files
- Write - Write files to bucket
- Read ACP - Read all Access Control Policies attached to bucket
- Write ACP - Write Access Control Policies to bucket
- Full Control - All above permissions

`$ aws s3 --no-sign-request --recursive ls s3://<s3_bucket_IP>`

`$ aws s3 --no-sign-request --recursive ls s3://<s3_bucket_IP>`


```
$ aws s3api get-bucket-acl --bucket <s3_bucket_IP>

$ aws s3api get-bucket-policy --bucket <s3_bucket_IP>
```

---
## References

https://docs.aws.amazon.com/cli/latest/reference/s3/ls.html

https://docs.aws.amazon.com/AmazonS3/latest/userguide/managing-acls.html

https://www.virtuesecurity.com/aws-penetration-testing-part-1-s3-buckets/

https://www.virtuesecurity.com/aws-penetration-testing-part-2-s3-iam-ec2/

https://sysdig.com/blog/scarleteel-2-0/