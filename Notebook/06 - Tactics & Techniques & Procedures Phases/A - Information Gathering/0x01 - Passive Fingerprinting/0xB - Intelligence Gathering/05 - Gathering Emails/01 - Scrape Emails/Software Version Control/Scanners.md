# Scanners

## [[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xB - Intelligence Gathering/01 - Organization/Scanners/theHarvester|theHarvester]]

```
$ theHarvester -l 1500 -d <domain.com | organization_name> -b github-code -f output.json
```

## Zen

### Setup

Install the dependencies according to your package manager.

```
$ sudo apt install -y python3-requests
```

Clone and the repository and run these commands as root (without `sudo`).

```bash
git clone https://github.com/s0md3v/Zen.git /opt/intelligence-gathering/Zen/

cat << EOF > /usr/local/bin/zen
#!/bin/bash
pushd /opt/intelligence-gathering/Zen/ > /dev/null
python3 zen.py \$*
popd > /dev/null
EOF
chmod 755 /usr/local/bin/zen
```

### Help Menu

```
$ zen -h
usage: zen.py [-h] [-o OUTPUT] [-u UNAME] [-t THREADS] [--org] [--breach] target

positional arguments:
  target      target

options:
  -h, --help  show this help message and exit
  -o OUTPUT   output file
  -u UNAME    your username
  -t THREADS  number of threads
  --org       organization
  --breach    check emails for breach
```

### Usage

Specify your github username without an token authorization.

```
$ zen -u <your_username> <target>
```

Speed up the scan using multiple threads.

```
$ zen -t 10 <target>
```

Gather breached emails of a specific username.

```
$ zen --breach <target_username> -o emails.txt
```

Gather breached emails from the commits in the current repository.

```
$ zen --breach https://github.com/<username>/<repository> -o emails.txt
```

Gather breached emails from an organization's name.

```
$ zen <organization_name> --org -o emails.txt
```

---
## References

- [s0md3v: Zen](https://github.com/s0md3v/Zen)