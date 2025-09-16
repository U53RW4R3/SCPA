---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - command-and-control
  - metasploit-framework
---
# Installation

## 01 - Package Manager

Install it according to your package manager.

```
$ yay -S metasploit
```

## 02 - Universal Installation

### 2.1 - Installer

```
# curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall

# wget -qO msfinstall https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb
```

Execute the script to install Metasploit.

```
# chmod 755 msfinstall && ./msfinstall
```

### 2.2 - Container

```
$ docker pull metasploitframework/metasploit-framework

$ docker run --rm -it -p 443:443 -v $PWD:/root/.msf4/ metasploitframework/metasploit-framework
```