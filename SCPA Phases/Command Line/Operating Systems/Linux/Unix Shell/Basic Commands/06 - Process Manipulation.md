# 06 - Process Manipulation

Search Tag(s): #command-line #linux

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

## 6.2 - Terminating Process

```
$ kill -9 <pid>

$ pkill -9 <program>
```

## 6.3 - Fork Background Process

```
$ <command> [arguments] &
```