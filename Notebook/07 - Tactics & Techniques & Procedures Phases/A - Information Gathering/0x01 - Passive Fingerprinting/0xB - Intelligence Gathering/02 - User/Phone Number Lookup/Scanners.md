---
author(s):
  - Userware
tags:
  - information-gathering
  - passive-fingerprinting
---
# Scanners

## 01 - PhoneInfoga

### 1.1 - Setup

#### 1.1.1 - Download Pre-compiled binary.

```
$ wget https://github.com/sundowndev/phoneinfoga/releases/download/v2.11.0/phoneinfoga_Linux_x86_64.tar.gz && \
tar xzf phoneinfoga_Linux_x86_64.tar.gz && \
sudo mv phoneinfoga /usr/local/bin/
```

### 1.2 - Help Menu

```
$ phoneinfoga 
PhoneInfoga is one of the most advanced tools to scan phone numbers using only free resources.

Usage:
  phoneinfoga [command]

Examples:
phoneinfoga scan -n <number>

Available Commands:
  help        Help about any command
  scan        Scan a phone number
  scanners    Display list of loaded scanners
  serve       Serve web client
  version     Print current version of the tool

Flags:
  -h, --help   help for phoneinfoga

Use "phoneinfoga [command] --help" for more information about a command.
```

### 1.3 - Usage

TODO: Fill in this info

```
$ phoneinfoga scanners
```

---
## References

### Github

- [PhoneInfoga](https://sundowndev.github.io/phoneinfoga/)

### OH SHINT

- [OH SHINT: Phone Numbers](https://ohshint.gitbook.io/oh-shint-its-a-blog/osint-web-resources/phone-numbers)

### OSINT Team

- [OSINT Team: How to find information on anyone](https://osintteam.blog/osint-how-to-find-information-on-anyone-5029a3c7fd56)