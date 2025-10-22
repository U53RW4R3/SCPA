---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - network-mapper
---
# 02 - Output File Formats

## 2.1 - Normal Format

```
$ sudo nmap -oN initial.nmap <IP>
```

## 2.2 - Leet Speak Format

```
$ sudo nmap -oS initial.nmap <IP>
```

## 2.3 - XML Format

```
$ sudo nmap -oX initial.xml <IP>
```

## 2.4 - Grepable Format

```
$ sudo nmap -oG initial.gnmap <IP>
```

## 2.5 - Output All Formats

```
$ sudo nmap -oA initial <IP>
```