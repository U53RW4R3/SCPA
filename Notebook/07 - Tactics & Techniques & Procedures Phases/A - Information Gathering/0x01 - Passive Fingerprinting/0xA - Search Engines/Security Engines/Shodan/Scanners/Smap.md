# [[03 - Offensive Infrastructure/E - Setup Machine/0x03 - Offensive Tools/Reconnaissance/OSINT/Smap|Smap]]

## Scan Single Target

```
$ smap <IP>
```

## Specify Ports

```
$ smap -p 21-23,80,443 <IP>
```

## Scan Multiple Targets

```
$ smap -iL targets.txt
```

## Service Version

```
$ smap -sV <IP>
```