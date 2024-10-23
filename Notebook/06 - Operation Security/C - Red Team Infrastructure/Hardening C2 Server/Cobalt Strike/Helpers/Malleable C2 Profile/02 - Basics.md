---
author(s):
  - Userware
tags:
  - helpers
  - red-team-infrastructure
  - cobalt-strike
---
# 02 - Basics

## 2.1 - Global Options

### 2.1.1 - Auxiliary Settings

```
# Name of the C2 profile
set sample_name "<profile_name>";

# User Agent
set useragent "<user_agent>";

# Staging payloads (part of metasploit shellcode compatibility).
# Disabling it loses the ability to generate staging payloads.
set host_stage "<true | false>";

# Each pound (#) is replaced with a random hex value.

# Default name of pipe to use SMB Beacon's P2P communication.
set pipename "<namepipe>_##";

# Using staging payload for SMB Beacon's P2P communication.
set pipename_stager "<namepipe>_##";

# SSH client banner
set ssh_banner "Welcome to Ubuntu 20.04.01 (GNU/Linux 5.15.0-91-generic x86_64)";

# Pipe name for ssh sessions.
set ssh_pipename "<namepipe>_ssh_####";

# Sleep and Jitter (uses seconds).
set sleeptime "15";
set jitter    "30"; # Default jitter factor (0 - 99%)
```

### 2.1.2 - Code Signing Certificate

- Refer to [[01 - Generate TLS Keystore|generate TLS keystore]].

```
code-signer {
    set keystore "keystore.jks"; 
    set password "<password>";
    set alias    "<alias>";
    set timestamp "false";
    set timestamp "http://timestamp.digicert.com";
}
```