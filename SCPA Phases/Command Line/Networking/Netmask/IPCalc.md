# IPCalc

## 01 - Setup

- Ubuntu/Debian based distros

`$ sudo apt install -y ipcalc-ng`

- Arch based distros

`$ sudo apt install -y ipcalc-ng`

## 02 - Help Menu

```
$ ipcalc-ng --help
Usage: ipcalc-ng [OPTION...]
  -c, --check                     Validate IP address
  -r, --random-private=PREFIX     Generate a random private IP network using
                                  the supplied prefix or mask.
  -S, --split=PREFIX              Split the provided network using the
                                  provided prefix/netmask
  -d, --deaggregate=IP1-IP2       Deaggregate the provided address range
  -i, --info                      Print information on the provided IP address
                                  (default)
      --all-info                  Print verbose information on the provided IP
                                  address

Specific info options:
      --reverse-dns               Print network in a the reverse DNS format
  -a, --address                   Display IP address
  -b, --broadcast                 Display calculated broadcast address
  -m, --netmask                   Display netmask for IP
  -n, --network                   Display network address
  -p, --prefix                    Display network prefix
      --minaddr                   Display the minimum address in the network
      --maxaddr                   Display the maximum address in the network
      --addresses                 Display the maximum number of addresses in
                                  the network
      --addrspace                 Display the address space the network
                                  resides on
  -h, --hostname                  Show hostname determined via DNS
  -o, --lookup-host=STRING        Show IP as determined via DNS
  -g, --geoinfo                   Show Geographic information about the
                                  provided IP

Other options:
  -4, --ipv4                      Explicitly specify the IPv4 address family
  -6, --ipv6                      Explicitly specify the IPv6 address family
      --class-prefix              When specified the default prefix will be determined
                                  by the IPv4 address class
      --no-decorate               Print only the requested information
  -j, --json                      JSON output
  -s, --silent                    Don't ever display error messages
  -v, --version                   Display program version
  -?, --help                      Show this help message
      --usage                     Display brief usage message
```

## 03 - Usage

TODO: Fill this info

---
## References

- [IPCalc Source Repository](https://gitlab.com/ipcalc/ipcalc)

- [IPCalc Website](https://jodies.de/ipcalc)

- [Subnet Cheatsheet Subnet Mask](https://www.freecodecamp.org/news/subnet-cheat-sheet-24-subnet-mask-30-26-27-29-and-other-ip-address-cidr-network-references/)