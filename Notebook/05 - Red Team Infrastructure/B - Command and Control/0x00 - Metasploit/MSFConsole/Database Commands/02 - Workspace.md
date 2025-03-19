# 02 - Workspace

Search Tag(s): #metasploit-framework #command-and-control 

Add new workspace.

```
msf > workspace -a new_workspace
[*] Added workspace: new_workspace
[*] Workspace: new_workspace
```

Rename workspace.

```
msf > workspace -r default renamed_workspace
[*] Renamed workspace 'default' to 'renamed_workspace'
```

List available workspaces.

```
msf > workspace [-l]
default
new_workspace
renamed_workspace
```

Search a specific workspace names.

```
msf > workspace -s <workspace>
```

Delete a specific workspace.

```
msf > workspace -d <workspace>
```

Delete all workspaces.

```
msf > workspace -D <workspace>
```

---
## References

### Hacking Articles

- [Hacking Articles: Metasploit for Pentester Database Workspace](https://www.hackingarticles.in/metasploit-for-pentester-database-workspace/)