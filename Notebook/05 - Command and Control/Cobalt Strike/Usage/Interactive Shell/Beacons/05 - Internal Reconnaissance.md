# 05 - Internal Reconnaissance

Search Tag(s): #command-and-control #post-exploitation #enumeration-and-discovery #cobalt-strike

TODO: Fill this info

## 5.1 - Port Scanning

### 5.1.1 - Help Menu

```
beacon> help portscan
Use: portscan [pid] [arch] [targets] [ports] [arp|icmp|none] [max connections]
     portscan [targets] [ports] [arp|icmp|none] [max connections]

Inject into the specified process to run a port scan against the specified hosts.

Use portscan with no [pid] and [arch] arguments to spawn a temporary
process to run a port scan against the specified hosts.

[targets] is a comma separated list of hosts to scan. You may also specify
IPv4 address ranges (e.g., 192.168.1.128-192.168.2.240, 192.168.1.0/24)

[ports] is a comma separated list or ports to scan. You may specify port
ranges as well (e.g., 1-65535)

The [arp|icmp|none] options dictate how the port scanning tool will determine
if a host is alive. The ARP option uses ARP to see if a system responds to the
specified address. The ICMP option sends an ICMP echo request. The none option 
tells the portscan tool to assume all hosts are alive.

The [max connections] option limits how many connections the port scan tool
will attempt at any one time. The portscan tool uses asynchronous I/O and
it's able to handle a large number of connections at one time. A higher value
will make the portscan go much faster. The default is 1024.
```

## 5.1.2 - Usage

```
beacon> portscan <pid> <x86 | x64> <IP>/<CIDR> <PORTS> <arp | icmp | none> <max_connections>
```

## 5.2 - Copy Clipboard

```
beacon> clipboard
```

## 5.3 - List Drives

```
beacon> drives
```

## 5.4 - Enumerate Registry Keys

### 5.4.1 - Help Menu

```
beacon> help reg
Use: reg query  [x86|x64] [root\path]
     reg queryv [x86|x64] [root\path] [subkey]

Use 'query' to query a key within the registry. Lists all subkeys and values.

Use 'queryv' to query a subkey within the registry. Lits only the subkey and 
its value.

Use HKLM, HKCR, HKCC, HKCU, or HKU for the root.

Specify x86|x64 to force a specific view of the registry.
```

### 5.4.2 - Usage

Query the registry keys.

```
beacon> reg query <x86 | x64> <HKLM | HKCR | HKCU | HKU>\path\to\registry_key\
```

Query the sub key registries.

```
beacon> reg queryv <x86 | x64> <HKLM | HKCR | HKCU | HKU>\path\to\registry registry_subkey
```