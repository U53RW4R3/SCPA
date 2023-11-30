# 02 - Hosts

Search Tag(s): #metasploit-framework #command-and-control

## 2.1 - Help Menu

```
msf > hosts -h
Usage: hosts [ options ] [addr1 addr2 ...]


OPTIONS:

    -a, --add <host>                       Add the hosts instead of searching
    -c, --columns <columns>                Only show the given columns (see list below)
    -C, --columns-until-restart <columns>  Only show the given columns until the next restart (see list below)
    -d, --delete <hosts>                   Delete the hosts instead of searching
    -h, --help                             Show this help information
    -i, --info <info>                      Change the info of a host
    -m, --comment <comment>                Change the comment of a host
    -n, --name <name>                      Change the name of a host
    -O, --order <column id>                Order rows by specified column number
    -o, --output <filename>                Send output to a file in csv format
    -R, --rhosts                           Set RHOSTS from the results of the search
    -S, --search <filter>                  Search string to filter by
    -t, --tag                              Add or specify a tag to a range of hosts
    -u, --up                               Only show hosts which are up

Available columns: address, arch, comm, comments, created_at, cred_count, detected_arch, exploit_attempt_count, host_detail_count, info, mac, name, note_count, os_family, os_flavor, os_lang, os_name, os_sp, purpose, scope, service_count, state, updated_at, virtual_host, vuln_count, tags
```

## 2.2 - Usage

```
msf > hosts

Hosts
=====

address    mac  name    os_name     os_flavor  os_sp  purpose  info  comments
-------    ---  ----    -------     ---------  -----  -------  ----  --------
10.0.2.15       DEFALT  Windows 10                    client

msf > hosts -c address,virtual_host,purpose,comm,state,scope,cred_count,exploit_attempt_count,host_detail_count,vuln_count,service_count --up -R
```