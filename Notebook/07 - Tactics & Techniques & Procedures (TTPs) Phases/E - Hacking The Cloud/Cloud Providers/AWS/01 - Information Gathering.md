# Information Gathering

- Install the native AWS tool to perform enumeration later on.

```
$ sudo apt install -y awscli
```

- Use `httpx` to detect the AWS S3 technologies with `-server` to find it

```
$ httpx -l urls.txt -mr 'AmazonS3' -o live-aws-s3-buckets.txt

$ awk -F "/" '{print "s3://"$3}' live-aws-s3-buckets.txt | sort -uo s3-buckets.txt
```

## Nuclei Scanner

```
$ nuclei -l live-aws-s3-buckets.txt -t ~/nuclei-templates -id aws-bucket-takeover -o accessible-aws-s3-buckets-output.txt
```

## Automation Script

`$ cat sweep-s3-buckets.sh`

---

```bash
#!/bin/bash

# Check if the AWS CLI is installed
if ! which aws &> /dev/null
then
    echo "AWS CLI is not installed. Please install it and configure your credentials."
    exit 1
fi

# Check if the input file exists
if [[] ! -f "$1" ]]
then
    echo "The input file '$1' does not exist."
    exit 1
fi

# Create an output directory if it doesn't exist
OUTPUT_DIR="output"
mkdir -p "$OUTPUT_DIR"

# TODO: Add an if statement if the attacker does have permissions to enumerate and upload files
# Loop through each line in the input file and check S3 bucket accessibility
while IFS= read -r s3
do
    # Use 'aws s3 ls' to check if the bucket is accessible without credentials
    if aws s3 --no-sign-request ls "$s3" &> /dev/null
    then
        echo "Bucket $s3 is accessible without AWS credentials."

        # Save the result to the output directory
        echo "$s3" >> "$OUTPUT_DIR/accessible-targets.txt"
    else
        # Save the result to the output directory
        echo "$s3" >> "$OUTPUT_DIR/require_credentials.txt"
    fi
done < "$1"
```

```
$ ./sweep-s3-buckets.sh s3-buckets.txt
```

---
## References

https://buckets.grayhatwarfare.com/

https://hackingthe.cloud/aws/general-knowledge/aws_organizations_defaults/

https://github.com/nahamsec/lazys3

https://github.com/sa7mon/S3Scanner

https://github.com/jordanpotti/cloudscraper (huge TODO)