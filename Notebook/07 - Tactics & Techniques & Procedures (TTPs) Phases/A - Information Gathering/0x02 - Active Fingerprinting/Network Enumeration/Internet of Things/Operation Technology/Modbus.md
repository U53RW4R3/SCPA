# Modbus

## 01 - Banner Grab

```
msf > use auxiliary/scanner/scada/modbus_banner_grabbing

msf auxiliary(scanner/scada/modbus_banner_grabbing) > options

msf auxiliary(scanner/scada/modbus_banner_grabbing) > set rhosts <IP>

msf auxiliary(scanner/scada/modbus_banner_grabbing) > run
```

## Network Mapper

```
$ nmap --script modbus-discover.nse [--script-args='modbus-discover.aggressive=true'] -p 502 <IP>
```

## Metasploit

```
msf > use auxiliary/scanner/scada/modbusdetect

msf auxiliary(scanner/scada/modbusdetect) > options

msf auxiliary(scanner/scada/modbusdetect) > set rhosts <IP>

msf auxiliary(scanner/scada/modbusdetect) > run
```

```
msf > use auxiliary/scanner/scada/modbus_findunitid

msf auxiliary(scanner/scada/modbus_findunitid) > options

msf auxiliary(scanner/scada/modbus_findunitid) > set rhosts <IP>

msf auxiliary(scanner/scada/modbus_findunitid) > run
```