# Setup

## Dependencies

Install dependencies according to your package manager.

```
$ sudo apt install -y virtualbox virtualbox-guest-additions-iso packer vagrant

$ sudo pacman -S virtualbox virtualbox-host-modules-arch dkms packer vagrant
```

## Setup VirtualBox

Load virtualbox modules.

```
$ sudo modprobe vboxdrv
```

Add `vboxusers` group.

```
$ sudo usermod -aG vboxusers $USER
```

Install vagrant plugin.

```
$ VAGRANT_DISABLE_STRICT_DEPENDENCY_ENFORCEMENT=1 vagrant plugin install vagrant-reload
```

If you're using virtualbox run this. Otherwise skip to the next line for virt-manager.

```
$ VAGRANT_DISABLE_STRICT_DEPENDENCY_ENFORCEMENT=1 vagrant plugin install vagrant-vbguest
```

For virt-manager.

```
$ VAGRANT_DISABLE_STRICT_DEPENDENCY_ENFORCEMENT=1 vagrant plugin install vagrant-libvirt
```

## Setup Metasploitable3

Clone the repository.

```
$ git clone https://github.com/rapid7/metasploitable3.git
```

Run the script to build the virtual machines.

```
$ cd metasploitable3 && ./build.sh ubuntu1404 && ./build.sh windows2008
```

## Post Installation

```
C:\> slmgr.exe /rearm
```

TODO: insert image of installing virtualbox guest addition ISO.

## DNS Hosts Addresses

Map the metasploitable3 IPv4 address as a DNS reference.

```
$ sudo nano /etc/hosts
<VM_IP> metasploitable.local
```

---
## References

- [Rapid7: Metasploitable3](https://github.com/rapid7/metasploitable3)

- [Metasploitable3 ISO Image](https://sourceforge.net/projects/metasploitable3-ub1404upgraded/)

- [Liberty Shell: Metasploitable 3 Install](https://liberty-shell.com/sec/2018/07/08/install-ms3/)