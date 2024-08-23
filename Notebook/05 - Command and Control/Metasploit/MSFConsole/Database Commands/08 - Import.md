# 08 - Import

Search Tag(s): #metasploit-framework #command-and-control

## 8.1 - Help Menu

```
msf > db_import 
Usage: db_import <filename> [file2...]

Filenames can be globs like *.xml, or **/*.xml which will search recursively
Currently supported file types include:
    Acunetix
    Amap Log
    Amap Log -m
    Appscan
    Burp Session XML
    Burp Issue XML
    CI
    Foundstone
    FusionVM XML
    Group Policy Preferences Credentials
    IP Address List
    IP360 ASPL
    IP360 XML v3
    Libpcap Packet Capture
    Masscan XML
    Metasploit PWDump Export
    Metasploit XML
    Metasploit Zip Export
    Microsoft Baseline Security Analyzer
    NeXpose Simple XML
    NeXpose XML Report
    Nessus NBE Report
    Nessus XML (v1)
    Nessus XML (v2)
    NetSparker XML
    Nikto XML
    Nmap XML
    OpenVAS Report
    OpenVAS XML
    Outpost24 XML
    Qualys Asset XML
    Qualys Scan XML
    Retina XML
    Spiceworks CSV Export
    Wapiti XML
```

## 8.2 - Usage

```
msf > db_import output.xml
```