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

List background jobs.

```
$ jobs
```

Check running background jobs.

```
$ bg [job_id_1] [job_id_n]
```

Interact with background process.

```
$ fg [job_id]
```

Terminate the latest job.

```
$ kill %1
```