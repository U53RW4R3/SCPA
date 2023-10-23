# Spoof MAC Address

## 01 - Linux

### 1.1 - Manual

- `ip` command

```
 $ sudo ip link set dev <interface> down && \
 sudo ip link set dev <interface> address $(openssl rand -hex 6 | sed 's/../&:/g;s/:$//') && \
 sudo ip link set dev <interface> up
```

- `ifconfig` command

`$ sudo ifconfig <interface> hw ether $(openssl rand -hex 6 | sed 's/../&:/g;s/:$//')`

### 1.2 - Macchanger

#### Help Menu

```
$ macchanger -h
GNU MAC Changer
Usage: macchanger [options] device

  -h,  --help                   Print this help
  -V,  --version                Print version and exit
  -s,  --show                   Print the MAC address and exit
  -e,  --ending                 Don't change the vendor bytes
  -a,  --another                Set random vendor MAC of the same kind
  -A                            Set random vendor MAC of any kind
  -p,  --permanent              Reset to original, permanent hardware MAC
  -r,  --random                 Set fully random MAC
  -l,  --list[=keyword]         Print known vendors
  -b,  --bia                    Pretend to be a burned-in-address
  -m,  --mac=XX:XX:XX:XX:XX:XX  Set the MAC XX:XX:XX:XX:XX:XX

Report bugs to https://github.com/alobbs/macchanger/issues
```

#### Usage

- **Change the MAC Address randomly**

`$ sudo macchanger -r <interface>`

- **Set the MAC Address manually**

`$ sudo macchanger -r <interface> -m ab:cd:ef:12:34:56`

#### Use Case

- Setup a cronjob when rebooting the machine.

```
$ sudo crontab -e
@reboot macchanger -r <interface>
```

## 02 - Windows

### 2.1 - Powershell

- **Note:** run this script with administrative rights.

```powershell
PS C:\> Get-NetAdapter
PS C:\> .\New-MACaddress.ps1 -interfaceindexnumber <int>
```

---
### References

- [New-MACaddress.ps1](https://github.com/KurtDeGreeff/PlayPowershell/blob/master/New-MACaddress.ps1)