# Manual

TODO: Fill this info

`$ mongosh`

## Databases

```
> show dbs

> use <database>

> show collections

> show tables
```


```python
#!/usr/bin/python
import subprocess
import sys

# Author: soggyTowel

def check_mongo(ip, port):
    try:
        cmd = f"mongo --host {ip} --port {port} --eval 'quit()'"
        subprocess.run(cmd, shell=True, check=True)
        return True
    except subprocess.CalledProcessError:
        return False

def main(input_file, output_file):
    with open(input_file, "r") as f:
        lines = f.read().splitlines()

    with open(output_file, "a") as out_f:
        for line in lines:
            parts = line.split(" ")
            ip, port = parts[-1].split(":")[0], parts[-1].split(":")[1]

            if check_mongo(ip, port):
                try:
                    mongo_cmd = f"mongo --host {ip} --port {port}"

                    result = subprocess.run(mongo_cmd, shell=True, text=True, input="show dbs\nexit\n", capture_output=True, check=True)
                    output = result.stdout.strip()

                    compromised = False
                    for line in output.split("\n"):
                        if "READ__ME_TO_RECOVER_YOUR_DATA" in line or "READ_ME_TO_RECOVER_YOUR_DATA" in line:
                            compromised = True
                            break

                    if compromised:
                        print(f"Node {ip}:{port} is compromised or ransomware detected, skipping...")
                        continue

                    if "not master" in output:
                        print(f"Node {ip}:{port} is secondary, skipping...")
                        continue

                    print(f"Node {ip}:{port} added to results.")
                    out_f.write(f"{ip}:{port}\n") 
                    out_f.flush()
                except subprocess.CalledProcessError as e:
                    print(f"Error connecting to {ip}:{port}: {e}")
            else:
                print(f"Could not connect to {ip}:{port}, skipping...")

if __name__ == "__main__":
    if len(sys.argv) != 3:
        print("Usage: %s input.txt output.txt" % (sys.argv[0]))
        sys.exit(1)

    input_file = sys.argv[1]
    output_file = sys.argv[2]
    main(input_file, output_file)
```

---
## References

- [Hacktricks: Pentesting MongoDB](https://book.hacktricks.xyz/network-services-pentesting/27017-27018-mongodb)