# SCADA (ICS)

## Shodan

### Modbus

```
port:502
```

### Moxa NPort

```
port:4800 "Moxa NPort"

port:4800 "Moxa NPort" Status: Authentication enabled
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