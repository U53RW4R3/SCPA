---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - angry-ip-scanner
---
# Angry IP Scanner

## 01 - Setup

### 1.1 - Linux

#### 1.1.1 - Install Dependencies

```
$ sudo apt install default-jdk default-jre rpm fakeroot
```

#### 1.1.2 - Install Angry IP Scanner

Clone the repository then compile the source into an executable `.jar` file.

```
$ git clone https://github.com/angryip/ipscan.git && cd ipscan && \
sudo make linux && \
sudo mkdir -p /opt/intelligence-gathering/AngryIPScanner/ && \
sudo cp build/libs/ipscan-linux64-3.9.1-2-g7950484a.jar /opt/intelligence-gathering/AngryIPScanner/ipscan.jar
```

Bash script to execute arguments. Run the commands as root (without `sudo`).

```
cat << EOF > /usr/local/bin/ipscan
#!/bin/sh
pushd /opt/intelligence-gathering/AngryIPScanner/ > /dev/null
java -nowarn -jar ipscan.jar \$*
popd > /dev/null
EOF
chmod 755 /usr/local/bin/ipscan
```

Install a debian package after compiling.

```
$ sudo dpkg -i build/libs/ipscan_3.9.1-2-g7950484a_amd64.deb
```

### 1.2 - Windows

Clone the repository then compile the source into an executable `.jar` file.

```
C:\> git clone https://github.com/angryip/ipscan.git && .\gradle win64
```

## 02 - Help Menu

```
$ ipscan -h        
Pass the following arguments:
[options] <feeder> <exporter>

Where <feeder> is one of:
-f:range <Start IP> <End IP>
-f:random <Base IP> <IP Mask> <Count>
-f:file <File>

<exporter> is one of:
-o filename.txt         Text file (txt)
-o filename.csv         Comma-separated file (csv)
-o filename.xml         XML file (xml)
-o filename.lst         IP:Port list (lst)
-o filename.sql         SQL file (sql)

And possible [options] are (grouping allowed):
-s      start scanning automatically
-q      quit after exporting the results
-a      append to the file, do not overwrite
```

## 03 - Usage

> [!NOTE]
> Angry IP Scanner will probe SMB ports then label them as file servers.

Scan IP range.

```
$ ipscan -sq -f:range <start_IP_range> <end_IP_range> -o live-hosts-output.txt
```

Scan from IP target lists.

```
$ ipscan -sq -f:file ip_targets.txt -o live-hosts-output.txt
```

---
## References

- [Angry IP Scanner](https://angryip.org/)

- [Aldeid: Angry IP Scanner](https://www.aldeid.com/wiki/Angry-IPScan)