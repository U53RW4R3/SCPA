# 08 - Beacon Session

Search Tag(s): #sliver #command-and-control #interactive-shell

## 8.1 - Interact Beacon

### 8.1.1 - Help Menu

```
sliver > use -h

Command: use [sliver name/session]
About: Switch the active Sliver, a valid name must be provided (see sessions).

Usage:
======
  use [flags] [id]

Args:
=====
  id  string    beacon or session ID

Flags:
======
  -h, --help           display help
  -t, --timeout int    command timeout in seconds (default: 60)

Sub Commands:
=============
  beacons   Switch the active beacon
  sessions  Switch the active session
```

### 8.1.2 - Usage

Interact a long beacon or session ID string.

```
sliver > use <beacon_or_session_ID>
```

## 8.2 - Reconfigure Sleep and Jitter

### 8.2.1 - Help Menu

```
sliver (IMPLANT_NAME) > reconfig -h

Reconfigure the active beacon/session

Usage:
======
  reconfig [flags]

Flags:
======
  -i, --beacon-interval    string    beacon callback interval
  -j, --beacon-jitter      string    beacon callback jitter (random up to)
  -h, --help                         display help
  -r, --reconnect-interval string    reconnect interval for implant
  -t, --timeout            int       command timeout in seconds (default: 60)
```

### 8.2.2 - Usage

> [!NOTE] Seconds Unit
> `s` are measuring units that represents as seconds.

```
sliver (IMPLANT_NAME) > reconfig -i <sleep_seconds>s -j <integer>s
```