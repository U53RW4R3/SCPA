# Security Search Engines

## Anonymous Login

Shodan dorks.

```
"Anonymous login successful" ADMIN$ port:445

"SMB Status: Authentication disabled"

"Status: Authentication disabled" product:"MikrotikSMB"
```

## Legacy Operating Systems

### Workstations

#### Windows 7

Shodan dorks.

```
os:"windows 7"

port:445 os:"windows 7"
```

#### Windows XP

Shodan dorks.

```
os:"windows xp"
```

### Windows Server

#### Windows Server 2012

Shodan dorks.

```
os:"windows server 2012"

port:445 os:"windows server 2012"
```

#### Windows Server 2008

Shodan dorks.

```
os:"windows server 2008"

port:445 os:"windows server 2008"

os:"windows server 2008 r2"

port:445 os:"windows server 2008 r2"
```

#### Windows Server 2003

Shodan dorks.

```
os:"windows server 2003"

port:445 os:"windows server 2003"
```

## RCE

### EternalBlue
Shodan dorks.


```
os:"Windows 10 Home 19041"

os:"windows 7"

tags:doublepulsar

SMB Version 1 vuln:"cve-2020-0796"

vuln:ms17-010
```

### SMBGhost

Shodan dorks.

```
vuln:cve-2020-0796
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x01 - Defense Evasion/02 - Legacy Operating Systems/Windows|Defense Evasion: Legacy Windows Operating Systems]]