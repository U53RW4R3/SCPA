# Manual

## 01 - Usage

### 1.1 - Banner Grab

```
$ nc -nv <IP> 21

$ telnet -n <IP> 21
```

Retrieve a certificate if any

`$ openssl s_client -connect <IP>:21 -starttls ftp`

### 1.2 - Authenticate FTP server

#### 1.2.1 - Basic

```
$ ftp <IP> [-P <PORT>]

$ ftp -u ftp://<username>:<password>@<IP>[:PORT]
```

- Web browser connection

`ftp://<username>:<password>@<IP>`

#### 1.2.2 - Login using startTLS

Install a sophisticated cli based FTP client in Debian-based distros

`$ sudo apt install lftp`

Install a sophisticated cli based FTP client in Arch Linux-based distros

`$ sudo pacman -S lftp`

```
$ lftp
lftp :~> set ftp:ssl-force true
lftp :~> set ssl:verify-certificate no
lftp :~> connect <IP>
lftp <IP>:~> login
Usage: login <user|URL> [<pass>]
```

### 1.3 - Basic Commands

List files and directories including hidden ones

`ftp> ls -a`

Set file transfers mode as binary

`ftp> binary`

Set file transfers mode as ascii

`ftp> ascii`

Disconnect FTP server

`ftp> <exit | quit | bye>`

---
## References

- [Hacktricks: Pentesting FTP](https://book.hacktricks.xyz/pentesting/pentesting-ftp)

- [Hacktricks: Pentesting FTP Bounce Attack](https://book.hacktricks.xyz/pentesting/pentesting-ftp/ftp-bounce-attack)

- [Hacktricks: Pentesting FTP Download 2OFTP File](https://book.hacktricks.xyz/pentesting/pentesting-ftp/ftp-bounce-download-2oftp-file)