# FScan

## 01 - Setup

### Download pre-compiled binary

#### Linux

```
$ wget [--https-only] https://github.com/shadow1ng/fscan/releases/download/1.8.4/fscan && chmod 755 fscan

$ curl -ko fscan https://github.com/shadow1ng/fscan/releases/download/1.8.4/fscan && chmod 755 fscan
```

Download pre-compiled `fscan` binary in embedded devices.

```
$ wget --no-check-certificate -O fscan https://github.com/shadow1ng/fscan/releases/download/1.8.4/fscan_mipsle && chmod 755 fscan
```

#### Windows

Download it via command prompt.

```
C:\> certutil -urlcache -split -f https://github.com/shadow1ng/fscan/releases/download/1.8.4/fscan.exe fscan.exe

C:\> curl -o fscan.exe https://github.com/shadow1ng/fscan/releases/download/1.8.4/fscan.exe
```

Download it via cmdlet.

```
PS C:\> Invoke-WebRequest https://github.com/shadow1ng/fscan/releases/download/1.8.4/fscan.exe -OutFile fscan.exe
```

### Cross Compile

#### Linux

```
$ git clone https://github.com/shadow1ng/fscan && \
cd fscan && go build -ldflags="-s -w " -trimpath -o fscan main.go && \
sudo cp fscan /usr/local/bin/ && sudo chmod 755 /usr/local/bin/fscan
```

For embedded devices.

```
$ GOOS=windows GOARCH=mipsle go build -ldflags="-s -w " -trimpath -o fscan main.go
```

#### Windows

```
$ GOOS=windows GOARCH=amd64 go build -ldflags="-s -w " -trimpath -o fscan.exe main.go
```

## 02 - Help Menu

```
$ fscan

   ___                              _    
  / _ \     ___  ___ _ __ __ _  ___| | __ 
 / /_\/____/ __|/ __| '__/ _` |/ __| |/ /
/ /_\\_____\__ \ (__| | | (_| | (__|   <    
\____/     |___/\___|_|  \__,_|\___|_|\_\   
                     fscan version: 1.8.4
Host is none
Usage of fscan:
  -br int
    	Brute threads (default 1)
  -c string
    	exec command (ssh|wmiexec)
  -cookie string
    	set poc cookie,-cookie rememberMe=login
  -debug int
    	every time to LogErr (default 60)
  -dns
    	using dnslog poc
  -domain string
    	smb domain
  -full
    	poc full scan,as: shiro 100 key
  -h string
    	IP address of the host you want to scan,for example: 192.168.11.11 | 192.168.11.11-255 | 192.168.11.11,192.168.11.12
  -hash string
    	hash
  -hf string
    	host file, -hf ip.txt
  -hn string
    	the hosts no scan,as: -hn 192.168.1.1/24
  -json
    	json output
  -m string
    	Select scan type ,as: -m ssh (default "all")
  -no
    	not to save output log
  -nobr
    	not to Brute password
  -nocolor
    	no color
  -nopoc
    	not to scan web vul
  -noredis
    	no redis sec test
  -np
    	not to ping
  -num int
    	poc rate (default 20)
  -o string
    	Outputfile (default "result.txt")
  -p string
    	Select a port,for example: 22 | 1-65535 | 22,80,3306 (default "21,22,80,81,135,139,443,445,1433,1521,3306,5432,6379,7001,8000,8080,8089,9000,9200,11211,27017")
  -pa string
    	add port base DefaultPorts,-pa 3389
  -path string
    	fcgi、smb romote file path
  -ping
    	using ping replace icmp
  -pn string
    	the ports no scan,as: -pn 445
  -pocname string
    	use the pocs these contain pocname, -pocname weblogic
  -pocpath string
    	poc file path
  -portf string
    	Port File
  -proxy string
    	set poc proxy, -proxy http://127.0.0.1:8080
  -pwd string
    	password
  -pwda string
    	add a password base DefaultPasses,-pwda password
  -pwdf string
    	password file
  -rf string
    	redis file to write sshkey file (as: -rf id_rsa.pub)
  -rs string
    	redis shell to write cron file (as: -rs 192.168.1.1:6666)
  -sc string
    	ms17 shellcode,as -sc add
  -silent
    	silent scan
  -socks5 string
    	set socks5 proxy, will be used in tcp connection, timeout setting will not work
  -sshkey string
    	sshkey file (id_rsa)
  -t int
    	Thread nums (default 600)
  -time int
    	Set timeout (default 3)
  -top int
    	show live len top (default 10)
  -u string
    	url
  -uf string
    	urlfile
  -user string
    	username
  -usera string
    	add a user base DefaultUsers,-usera user
  -userf string
    	username file
  -wmi
    	start wmi
  -wt int
    	Set web timeout (default 5)
```

## 03 - Usage

TODO: Fill in the info

```
$ fscan -h <IP>
```

---
## References

- [FScan](https://github.com/shadow1ng/fscan)