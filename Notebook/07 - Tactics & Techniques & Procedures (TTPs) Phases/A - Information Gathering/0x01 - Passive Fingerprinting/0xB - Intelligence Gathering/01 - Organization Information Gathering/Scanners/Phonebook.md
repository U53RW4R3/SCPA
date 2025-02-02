# Phonebook

## 01 - Setup

### 1.1 - Dependencies

```
$ sudo apt install -y python3-requests python3-json python3-argparse
```

### 1.2 - Install Phonebook Script

```bash
git clone https://github.com/sm00v/Phonebook_CZ /opt/intelligence-gathering/Phonebook_CZ

cat << EOF > /usr/local/bin/phonebook
#!/bin/bash
pushd /opt/intelligence-gathering/Phonebook_CZ > /dev/null
python3 phonebook.py \$*
popd > /dev/null
EOF
chmod 755 /usr/local/bin/phonebook
```

## 02 - Help Menu

```
$ phonebook -h
[+] Running phonebook.cz scraper!

usage: phonebook.py [-h] [-e EMAIL] [-d DOMAIN] [-l LINKS] [-o [PHONEBOOK_CZ]]

Phonebook.cz scraper

options:
  -h, --help            show this help message and exit
  -e EMAIL, --email EMAIL
                        Search all emails for this domain.
  -d DOMAIN, --domain DOMAIN
                        Search all subdomains for this domain.
  -l LINKS, --links LINKS
                        Search all links for this domain.
  -o [PHONEBOOK_CZ]     Stores all items in file *_cz.txt

```

## 03 - Usage

```
$ phonebook -l <domain>.<tld> -o urls.txt
```

---
## References

- [Phonebook.cz](https://phonebook.cz)

- [sm00v: Phonebook_CZ](https://github.com/sm00v/Phonebook_CZ)