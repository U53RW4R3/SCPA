# Usage

Search Tag(s): #metasploit-framework #command-and-control #living-off-the-land

## 01 - Help Menu

```
help

Meta shell commands
===================

    Command     Description
    -------     -----------
    help        Help menu
    background  Backgrounds the current shell session
    sessions    Quickly switch to another session
    resource    Run a meta commands script stored in a local file
    shell       Spawn an interactive shell (*NIX Only)
    download    Download files
    upload      Upload files
    source      Run a shell script on remote machine (*NIX Only)
    irb         Open an interactive Ruby shell on the current session
    pry         Open the Pry debugger on the current session
```

## 03 - Source Script

Execute a local shell script file on remote machine. `y` represent execute the script in background, `n` represent on foreground

```
source /path/to/local/commands.sh <y | n>
```

## 04 - Upload and Download

Upload files.

```
upload /path/to/local/file /path/to/remote/file
```

Download files.

```
download /path/to/remote/file /path/to/local/file
```

## 05 - Switch Interactive Sessions

```
sessions <session_ID>
```

## 06 - Background Session

```
background
```

## 07 - Resource Script to Automate Commands

```
resource /path/to/local/resource_1.rc /path/to/local/resource_n.rc
```

## 08 - Interactive Ruby Shell

```
irb
```

## 09 - Debug Current Session

```
pry
```