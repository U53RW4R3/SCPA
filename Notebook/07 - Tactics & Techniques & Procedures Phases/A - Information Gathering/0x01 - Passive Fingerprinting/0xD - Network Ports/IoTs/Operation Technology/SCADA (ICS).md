# SCADA (ICS)

TODO: Fill more dorks for ICS

## Google Dorking

### Simatic

```
intitle:"Miniweb Start Page"
```

### Siemens S7

```
inurl:"Portal/Portal.mwsl"
```

### General Electric

```
inurl:"ProficyPortal/default.asp"
```

### Schneider Electric

```
intitle:"ClearSCADA Home"
```

## Shodan

### BACnet

```
port:10,530
```

### Siemens S7

```
S7
```

### Modbus

```
port:502
```

### Moxa NPort

```
port:4800 "Moxa NPort"

port:4800 "Moxa NPort" Status: Authentication enabled
```

### Schneider Electric

```
ClearSCADA
```

## Censys

### Modbus

```
protocols:"502/modbus"
```

### Moxa NPort

```
host.services.port=4800 and "Moxa NPort"

host.services.port=4800 and "Moxa NPort" Status: Authentication enabled
```