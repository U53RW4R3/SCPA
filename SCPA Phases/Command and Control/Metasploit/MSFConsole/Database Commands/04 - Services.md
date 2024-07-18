# 04 - Services

Search Tag(s): #metasploit-framework #command-and-control

## 4.1 - Help Menu

```
msf > services -h
Usage: services [-h] [-u] [-a] [-r <proto>] [-p <port1,port2>] [-s <name1,name2>] [-o <filename>] [addr1 addr2 ...]


OPTIONS:

    -a, --add                  Add the services instead of searching.
    -c, --column <col1,col2>   Only show the given columns.
    -d, --delete               Delete the services instead of searching.
    -h, --help                 Show this help information.
    -O, --order <column id>    Order rows by specified column number.
    -o, --output <filename>    Send output to a file in csv format.
    -p, --port <ports>         Search for a list of ports.
    -r, --protocol <protocol>  Protocol type of the service being added [tcp|udp].
    -R, --rhosts               Set RHOSTS from the results of the search.
    -s, --name <name>          Name of the service to add.
    -S, --search <filter>      Search string to filter by.
    -u, --up                   Only show services which are up.
    -U, --update               Update data for existing service.

Available columns: created_at, info, name, port, proto, state, updated_at
```

## 4.2 - Usage

```
msf > services
Services
========

host       port  proto  name  state  info
----       ----  -----  ----  -----  ----
10.0.2.15  445   tcp    smb   open
```