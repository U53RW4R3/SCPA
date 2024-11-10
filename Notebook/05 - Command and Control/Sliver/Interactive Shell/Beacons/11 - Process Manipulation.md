# 11 - Process Manipulation

Search Tag(s): #sliver #command-and-control #interactive-shell

## Dump Memory From Process Identifier (PID)

### Help Menu

```
sliver (IMPLANT_NAME) > procdump -h

Command: procdump [pid]
About: Dumps the process memory given a process identifier (pid)

Usage:
======
  procdump [flags]

Flags:
======
  -h, --help                display help
  -X, --loot                save output as loot
  -N, --loot-name string    name to assign when adding the memory dump to the loot store (optional)
  -n, --name      string    target process name
  -p, --pid       int       target pid (default: -1)
  -s, --save      string    save to file (will overwrite if exists)
  -t, --timeout   int       command timeout in seconds (default: 60)
```

```
sliver (IMPLANT_NAME) > procdump -p <pid>
```

---
## References

- [DominicBreuker: Learning Sliver C2 (10) - Sideload](https://dominicbreuker.com/post/learning_sliver_c2_10_sideload/)