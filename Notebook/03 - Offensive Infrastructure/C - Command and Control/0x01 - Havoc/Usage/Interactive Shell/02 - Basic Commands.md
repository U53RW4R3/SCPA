---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - command-and-control
  - interactive-shell
  - havoc
---
# 02 - Basic Commands

## 2.5 - Execute Shell Commands

### 2.5.1 - Help Menu

```
Demon » help shell

 - Command       :  shell
 - Description   :  executes cmd.exe commands and gets the output
 - Behavior      :  Process Creation
 - Usage         :  shell [commands]
 - Example       :  shell dir c:\windows\system32

Demon » help powershell

 - Command       :  powershell
 - Description   :  executes powershell.exe commands and gets the output
 - Usage         :  powershell [commands]
 - Example       :  powershell dir c:\windows\system32
```

### 2.5.2 - Usage

Execute any `shell` command that the demon implant spawns a child process `cmd.exe`.

```
Demon » shell <command> [arguments]
```

Spawns a child process of `powershell.exe`.

```
Demon » powershell <cmdlet> [arguments]
```

## 2.8 - Jobs Queue

List job identifiers.

```
Demon » job list
```

Suspend job.

```
Demon » job suspend <job_id>
```

Resume job after suspension.

```
Demon » job resume <job_id>
```

Terminate job.

```
Demon » job kill <job_id>
```

List tasks.

```
Demon » task list
```

Clear all commands in queue to stop the task being executed.

```
Demon » task clear
```

---
## References

### Havoc

- [Havoc Framework Documentation](https://havocframework.com/docs/welcome)