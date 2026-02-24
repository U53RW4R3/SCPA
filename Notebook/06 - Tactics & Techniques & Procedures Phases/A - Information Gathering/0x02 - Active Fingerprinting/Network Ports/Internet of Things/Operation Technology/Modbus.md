# Modbus

## 01 - Banner Grab

### #network-mapper 

```
$ sudo nmap -p 502,20000,44818 -Pn -sV <IP>
```

### #metasploit

TODO: Fill in this info

```
msf > use auxiliary/scanner/scada/modbus_banner_grabbing

msf auxiliary(scanner/scada/modbus_banner_grabbing) > options

msf auxiliary(scanner/scada/modbus_banner_grabbing) > set threads 4

msf auxiliary(scanner/scada/modbus_banner_grabbing) > run rhosts=<IP>
```

## 02 - Discovery

### #network-mapper 

```
$ nmap --script modbus-discover.nse [--script-args='modbus-discover.aggressive=true'] -p 502 <IP>
```

### #metasploit

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