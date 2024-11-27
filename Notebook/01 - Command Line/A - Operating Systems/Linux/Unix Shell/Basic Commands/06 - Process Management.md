---
author(s):
  - Userware
tags:
  - command-line
  - linux
---
# 06 - Process Management

## 6.1 - List Process

### 6.1.1 - List Processes

```
$ ps aux

$ ps aux --forest
```

### 6.1.2 - Fetch process ID

```
$ pgrep <program>
```

## 6.2 - Fork Background Process

```
$ <command> [arguments] &
```