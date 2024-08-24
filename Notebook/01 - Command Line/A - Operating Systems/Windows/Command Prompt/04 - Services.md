# 04 - Services

Search Tag(s): #command-line #windows

## 4.1 - Start Service

### 4.1.1 - Net

```
C:\> net start <service_name>
```

### 4.1.2 - SCM (Service Control Management)

```
C:\> sc [\\<IP>] start <servicesvc>
```

### 4.1.3 - WMIC (Windows Management Instrumentation Command Line)

```
C:\> wmic [/node:<IP>] [/user:<username> /password:<password>] service <service_name> call startservice
```

## 4.2 - Stop Service

### 4.2.1 - Net

```
C:\> net stop <service_name>
```

### 4.2.1 - SCM (Service Control Management)

```
C:\> sc [\\<IP>] stop <servicesvc>
```

---
## References

- [[Windows Command Prompt References]]

- [LOFLCAB: WMIC](https://lofl-project.github.io/loflcab/Binaries/wmic/)