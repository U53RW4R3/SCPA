# 03 - Grep

Search Tag(s): #metasploit-framework #command-and-control

TODO: Show usage examples of using grep in MSF

```
msf > grep -h
Usage: grep [OPTIONS] [--] PATTERN CMD...
Grep the results of a console command (similar to Linux grep command)

    -m, --max-count num              Stop after num matches.
    -A, --after-context num          Show num lines of output after a match.
    -B, --before-context num         Show num lines of output before a match.
    -C, --context num                Show num lines of output around a match.
    -v, --[no-]invert-match          Invert match.
    -i, --[no-]ignore-case           Ignore case.
    -c, --count                      Only print a count of matching lines.
    -k, --keep-header num            Keep (include) num lines at start of output
    -s, --skip-header num            Skip num lines of output before attempting match.
    -h, --help                       Help banner.
```

Match the string `psexec` while `search` for `smb` modules.

```
msf > grep psexec search smb
```

Exclude matches of `DoS` and `local` while `search` for `tomcat` then filter `exploit` modules.

```
msf > grep -v DoS grep -v local search type:exploit name:tomcat
```