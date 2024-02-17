# Kerbrute

## 01 - Setup

```
$ wget -O kerbrute https://github.com/ropnop/kerbrute/releases/download/v1.0.3/kerbrute_linux_amd64 && \
chmod 755 kerbrute && \
sudo mv kerbrute /usr/local/bin/
```

## 02 - Help Menu

```
$ kerbrute -h

    __             __               __
   / /_____  _____/ /_  _______  __/ /____
  / //_/ _ \/ ___/ __ \/ ___/ / / / __/ _ \
 / ,< /  __/ /  / /_/ / /  / /_/ / /_/  __/
/_/|_|\___/_/  /_.___/_/   \__,_/\__/\___/

Version: v1.0.3 (9dad6e1) - 01/20/24 - Ronnie Flathers @ropnop

This tool is designed to assist in quickly bruteforcing valid Active Directory accounts through Kerberos Pre-Authentication.
It is designed to be used on an internal Windows domain with access to one of the Domain Controllers.
Warning: failed Kerberos Pre-Auth counts as a failed login and WILL lock out accounts

Usage:
  kerbrute [command]

Available Commands:
  bruteforce    Bruteforce username:password combos, from a file or stdin
  bruteuser     Bruteforce a single user's password from a wordlist
  help          Help about any command
  passwordspray Test a single password against a list of users
  userenum      Enumerate valid domain usernames via Kerberos
  version       Display version info and quit

Flags:
      --dc string       The location of the Domain Controller (KDC) to target. If blank, will lookup via DNS
      --delay int       Delay in millisecond between each attempt. Will always use single thread if set
  -d, --domain string   The full domain to use (e.g. contoso.com)
  -h, --help            help for kerbrute
  -o, --output string   File to write logs to. Optional.
      --safe            Safe mode. Will abort if any user comes back as locked out. Default: FALSE
  -t, --threads int     Threads to use (default 10)
  -v, --verbose         Log failures and errors

Use "kerbrute [command] --help" for more information about a command.
```

## 03 - Usage

- Password Spray each domain username accounts from an active directory

`$ kerbrute passwordspray [--dc <IP>] -d <domain_name> users.lst <password>`

- Brute force a username with a password dictionary (not recommended unless it has no lockout policy!)

`$ kerbrute bruteuser [--dc <IP>] -d <domain_name> passwords.lst <username>`

- Brute force with a combo list of usernames and passwords against a domain controller

`$ cat combolist.lst | kerbrute [--dc <IP>] -d <domain_name> bruteforce -`

---
## References

- [Kerbrute](https://github.com/ropnop/kerbrute)

- [Hacktricks: Pentesting Kerberos](https://book.hacktricks.xyz/pentesting/pentesting-kerberos-88)

- [Hacking Articles: A Detailed Guide on Kerbrute](https://www.hackingarticles.in/a-detailed-guide-on-kerbrute/)