# Hydra

## 01 - Help Menu

```
Options:
  -R        restore a previous aborted/crashed session
  -I        ignore an existing restore file (don't wait 10 seconds)
  -S        perform an SSL connect

  -x MIN:MAX:CHARSET  password bruteforce generation, type "-x -h" to get help
  -y        disable use of symbols in bruteforce, see above
  -r        use a non-random shuffling method for option -x

  -u        loop around users, not passwords (effective! implied with -x)

  -M FILE   list of servers to attack, one entry per line, ':' to specify port

  -b FORMAT specify the format for the -o FILE: text(default), json, jsonv1
  -f / -F   exit when a login/pass pair is found (-M: -f per host, -F global)

  -w / -W TIME  wait time for a response (32) / between connects per thread (0)
  -c TIME   wait time per login attempt over all threads (enforces -t 1)
  -4 / -6   use IPv4 (default) / IPv6 addresses (put always in [] also in -M)
  -v / -V / -d  verbose mode / show login+pass for each attempt / debug mode 
  -O        use old SSL v2 and v3
  -K        do not redo failed attempts (good for -M mass scanning)
  -q        do not print messages about connection errors

  -m OPT    options specific for a module, see -U output for information

Supported services: adam6500 asterisk cisco cisco-enable cvs firebird icq memcached nntp oracle-listener oracle-sid pcanywhere pcnfs postgres radmin2 redis rexec rlogin rpcap rsh rtsp s7-300 sip smtp-enum socks5 svn teamspeak telnet[s] vmauthd vnc xmpp

Use HYDRA_PROXY_HTTP or HYDRA_PROXY environment variables for a proxy setup.
E.g. % export HYDRA_PROXY=socks5://l:p@127.0.0.1:9150 (or: socks4:// connect://)
     % export HYDRA_PROXY=connect_and_socks_proxylist.txt  (up to 64 entries)
     % export HYDRA_PROXY_HTTP=http://login:pass@proxy:8080
     % export HYDRA_PROXY_HTTP=proxylist.txt  (up to 64 entries)
```

## 02 - Usage

TODO: Provide more coverage of this tool (refer to the link)

```
$ hydra -L users.lst -e nsr -t <int> <IP> <protocol>
```

Use usernames and passwords combo list

```
$ hydra -C userpass.lst <IP> <protocol>
```