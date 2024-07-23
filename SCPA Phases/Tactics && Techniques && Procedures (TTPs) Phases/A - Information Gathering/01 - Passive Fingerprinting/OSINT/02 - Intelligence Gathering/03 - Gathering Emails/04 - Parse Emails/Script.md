# Script

```bash
#!/bin/bash
input_leaks="leaks.json"
output_leaks="results.txt"

parse=$(grep -Po '"email_address": *"[^"]*" *,"password": *"[^"]*"' $input_leaks)

while read -r line
do
  email=$(echo "$line" | sed 's/.*"email_address": *"\([^"]*\)".*/\1/')
  password=$(echo "$line" | sed 's/.*"password": *"\([^"]*\)".*/\1/')

  echo "$email:$password" >> $output_leaks
done <<< "$parse"
```

---
## References

- [Archived Hastebin: Parse email and passwords](https://archive.ph/C8tI2)