# 05 - Process Manipulation

Search Tag(s): #command-line #linux

## 5.1 - List Process

### 5.1.1 - List Processes

```
$ ps aux

$ ps aux --forest
```

### 5.1.2 - Fetch process ID

```
$ pgrep <program>
```

## 5.2 - Terminating Process

```
$ kill -9 <pid>

$ pkill -9 <program>
```

## 5.3 - Fork Background Process

```
$ <command> [args] &
```