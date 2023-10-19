# Angry IP Scanner

TODO: Fill this info

## Setup

### Linux

#### Install Dependencies

```
$ sudo apt install default-jdk default-jre rpm fakeroot
```

#### Install Angry IP Scanner

- Compile

```
$ git clone https://github.com/angryip/ipscan.git && \
make linux && sudo mkdir -p /opt/intelligence-gathering/AngryIPScanner/ \
sudo cp build/libs/ipscan-linux64-3.9.1-2-g7950484a.jar /opt/intelligence-gathering/AngryIPScanner/ipscan.jar
```

- Bash script to execute arguments. Run the commands as root (without `sudo`)

```
cat << EOF > /usr/local/bin/ipscan
#!/bin/sh
cd /opt/intelligence-gathering/AngryIPScanner/
java -nowarn -jar ipscan.jar \$*
EOF
chmod 755 /usr/local/bin/ipscan
```

- Install a debian package after compiling

`$ sudo dpkg -i build/libs/ipscan_3.9.1-2-g7950484a_amd64.deb`

### Windows

- Compile

```
C:\> git clone https://github.com/angryip/ipscan.git && .\gradle win64
```

## Help Menu

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

## Usage

You can find windows file sharing servers

`$ ipscan -f:<IP_range> -o scan-output.txt`

---
## References

- [Angry IP Scanner](https://angryip.org/)