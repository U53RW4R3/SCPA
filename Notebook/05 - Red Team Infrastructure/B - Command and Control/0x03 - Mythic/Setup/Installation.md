---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - command-and-control
  - mythic
---
# Installation

## 01 - Install Mythic

```
$ sudo apt install -y make
```

```
$ git clone https://github.com/its-a-feature/Mythic
```

```
$ sudo ./install_docker_ubuntu.sh
```

Install Mythic agents

```
$ sudo ./mythic-cli install github https://github.com/MythicAgents/Apollo

sudo ./mythic-cli install github https://github.com/MythicAgents/Athena

sudo ./mythic-cli install github https://github.com/MythicAgents/Poseidon
```

Profile setup

```
sudo ./mythic-cli install github https://github.com/MythicC2Profiles/http
```

```
$ mythic-cli config get MYTHIC_ADMIN_PASSWORD
```