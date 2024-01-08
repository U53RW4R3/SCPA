# 01 - Workspace

Search Tag(s): #metasploit-framework #command-and-control 

## 1.1 - Help Menu

```
msf > workspace -h
Usage:
    workspace          List workspaces
    workspace [name]   Switch workspace

OPTIONS:

    -a, --add <name>          Add a workspace.
    -d, --delete <name>       Delete a workspace.
    -D, --delete-all          Delete all workspaces.
    -h, --help                Help banner.
    -l, --list                List workspaces.
    -r, --rename <old> <new>  Rename a workspace.
    -S, --search <name>       Search for a workspace.
    -v, --list-verbose        List workspaces verbosely.
```

## 1.2 - Usage

TODO: Fill this info - Userware

- Add new workspace

```
msf > workspace -a new_workspace
[*] Added workspace: new_workspace
[*] Workspace: new_workspace
```

- Rename workspace

```
msf > workspace -r default renamed_workspace
[*] Renamed workspace 'default' to 'renamed_workspace'
```

- List workspace

```
msf > workspace [-l]
default
new_workspace
renamed_workspace
```

---
## References

- [Metasploit for Pentester Database Workspace](https://www.hackingarticles.in/metasploit-for-pentester-database-workspace/)