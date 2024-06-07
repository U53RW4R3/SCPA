# SMB

## Anonymous Login

```
"Anonymous login successful" ADMIN$ port:445

"SMB Status: Authentication disabled"

"Status: Authentication disabled" product:"MikrotikSMB"
```

## Legacy Operating Systems

### Workstations

#### Windows 7

```
os:"windows 7"

port:445 os:"windows 7"
```

#### Windows XP

`os:"windows xp"`

### Windows Server

#### Windows Server 2012

```
os:"windows server 2012"

port:445 os:"windows server 2012"
```

#### Windows Server 2008

```
os:"windows server 2008"

port:445 os:"windows server 2008"

os:"windows server 2008 r2"

port:445 os:"windows server 2008 r2"
```

#### Windows Server 2003

```
os:"windows server 2003"

port:445 os:"windows server 2003"
```

## RCE

### EternalBlue

```
os:"Windows 10 Home 19041"

os:"windows 7"

tags:doublepulsar

SMB Version 1 vuln:"cve-2020-0796"

vuln:ms17-010
```

### SMBGhost

```
vuln:cve-2020-0796
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/F - Post Exploitation/Shell Is The Beginning/02 - Defense Evasion/01 - Legacy Operating Systems/Windows|Windows: Legacy Operating Systems]]