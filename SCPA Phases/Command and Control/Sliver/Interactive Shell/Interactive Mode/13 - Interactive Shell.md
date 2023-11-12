# 13 - Interactive Shell

## 13.1 - Interactive Session

### 13.1.1 - Help Menu

TODO: Fill this info

```
sliver (IMPLANT_NAME) > interactive -h

Task a beacon to open an interactive session (Beacon only)

Usage:
======
  interactive [flags]

Flags:
======
  -d, --delay      string    delay opening the session (after checkin) for a given period of time (default: 0s)
  -n, --dns        string    dns connection strings
  -h, --help                 display help
  -b, --http       string    http(s) connection strings
  -m, --mtls       string    mtls connection strings
  -p, --named-pipe string    namedpipe connection strings
  -i, --tcp-pivot  string    tcppivot connection strings
  -t, --timeout    int       command timeout in seconds (default: 60)
  -g, --wg         string    wg connection strings
```

```
sliver (IMPLANT_NAME) > sessions -h

Command: sessions <options>
About: List Sliver sessions, and optionally interact or kill a session.

Usage:
======
  sessions [flags]

Flags:
======
  -C, --clean               clean out any sessions marked as [DEAD]
  -f, --filter    string    filter sessions by substring
  -e, --filter-re string    filter sessions by regular expression
  -F, --force               force session action without waiting for results
  -h, --help                display help
  -i, --interact  string    interact with a session
  -k, --kill      string    kill the designated session
  -K, --kill-all            kill all the sessions
  -t, --timeout   int       command timeout in seconds (default: 60)
```

### 13.1.2 - Usage

- Switch from beacon to interactive session.

```
sliver (IMPLANT_NAME) > interactive

sliver (IMPLANT_NAME) > session -i <session_id>
```