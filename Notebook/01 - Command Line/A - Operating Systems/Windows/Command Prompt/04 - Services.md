# 04 - Services

Search Tag(s): #command-line #windows

## 4.1 - Start Service

### 4.1.1 - Net

```
C:\> net.exe start <service_name>
```

### 4.1.2 - SCM (Service Control Management)

```
C:\> sc.exe [\\<IP>] start <servicesvc>
```

### 4.1.3 - WMIC (Windows Management Instrumentation Command Line)

```
C:\> wmic.exe [/node:<IP>] [/user:<username> /password:<password>] service <service_name> call startservice
```

## 4.2 - Stop Service

### 4.2.1 - Net

```
C:\> net.exe stop <service_name>
```

### 4.2.1 - SCM (Service Control Management)

```
C:\> sc.exe [\\<IP>] stop <servicesvc>
```

---
## References

- [[Windows Command Prompt References]]

- [LOFLCAB: WMIC](https://lofl-project.github.io/loflcab/Binaries/wmic/)