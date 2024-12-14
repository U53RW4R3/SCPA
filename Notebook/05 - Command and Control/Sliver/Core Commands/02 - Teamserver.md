# 02 - Teamserver

Search Tag(s): #sliver #command-and-control

## 2.1 - Multiplayer

### 2.1.1 - Help Menu

```
[server] sliver > multiplayer -h

Enable multiplayer mode

Usage:
======
  multiplayer [flags]

Flags:
======
  -h, --help                 display help
  -L, --lhost      string    interface to bind server to
  -l, --lport      int       tcp listen port (default: 31337)
  -p, --persistent           make persistent across restarts
```

### 2.1.2 - Usage

 Reload and start the daemon `sliver.service`

```
$ sudo systemctl daemon-reload

$ sudo systemctl start sliver
```

Or you can manually enable multiplayer mode

```
[server] sliver > multiplayer

[server] sliver > multiplayer -L <IP> -l <PORT> [-p]
```

## 2.2 - Operators

### 2.2.1 - Add Operators

#### 2.2.1.1 - Help Menu

```
$ sudo /root/sliver-server operator -h
Generate operator configuration files

Usage:
  sliver-server operator [flags]

Flags:
  -h, --help           help for operator
  -l, --lhost string   multiplayer listener host
  -p, --lport uint16   multiplayer listener port (default 31337)
  -n, --name string    operator name
  -s, --save string    save file to ...

[server] sliver > new-operator -h

Create a new operator config file

Usage:
======
  new-operator [flags]

Flags:
======
  -h, --help            display help
  -l, --lhost string    listen host
  -p, --lport int       listen port (default: 31337)
  -n, --name  string    operator name
  -s, --save  string    directory/file to the binary to
```

#### 2.2.1.2 - Usage

Generate operator configuration file

```
$ sudo /root/sliver-server operator -l <IP> -p <PORT> -n <operator_name> -s /path/to/directory/

[server] sliver > new-operator -l <IP> -p <PORT> -n <operator_name> -s /path/to/directory/
```

Import configuration file with sliver client

```
$ sudo chown $USER:$USER file.cfg

$ sliver import file.cfg
```

### 2.2.2 - Kick Operators

#### 2.2.2.1 - Help Menu

```
[server] sliver > kick-operator -h

Kick an operator from the server

Usage:
======
  kick-operator [flags]

Flags:
======
  -h, --help           display help
  -n, --name string    operator name
```

#### 2.2.2.2 - Usage

```
[server] sliver > kick-operator -n <operator_name>
```

### 2.2.3 - List Operators

List operators to check which one is online or offline

```
sliver > operators
```