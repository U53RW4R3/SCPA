# Setup

## Dependencies

First you need a hypervisor. I recommend installing [[00 - Getting Started/C - Hypervisors/VirtualBox|VirtualBox]] then install dependencies according to your package manager.

```
$ sudo apt install -y packer vagrant

$ sudo pacman -S --noconfirm packer vagrant
```

## Setup Metasploitable3

TODO: Include images to import it.

Download the [torrent](https://archive.org/details/metasploitable3-master_win2k8_1569441065179_55164) to download **Windows Server 2008 R2**.

```
$ aria2c https://archive.org/download/metasploitable3-master_win2k8_1569441065179_55164/metasploitable3-master_win2k8_1569441065179_55164_archive.torrent

$ aria2c -T metasploitable3-master_win2k8_1569441065179_55164_archive.torrent
```

TODO: configure the specs https://www.youtube.com/watch?v=3_GIeegR0fY

Download `Metasploitable3-ub1404.ova`

```
$ aria2c "https://cyfuture.dl.sourceforge.net/project/metasploitable3-ub1404upgraded/Metasploitable3-ub1404.ova?viasf=1"
```

## Post Installation

Manage the software licensing in Windows Server 2008 R2.

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

### Source Repositories

- [Metasploitable3 Windows Server 2008 R2](https://archive.org/details/metasploitable3-master_win2k8_1569441065179_55164)

- [Metasploitable3 Ubuntu 14.04](https://sourceforge.net/projects/metasploitable3-ub1404upgraded/files/)