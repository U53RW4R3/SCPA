# Metasploitable3

## Setup Virtual Machines

I recommend installing [[00 - Getting Started/C - Hypervisors/VirtualBox|VirtualBox]].

### Pre-bundled

```
$ aria2c https://github.com/brimstone/metasploitable3/releases/download/0.1.4/Metasploitable3-0.1.4.ova
```

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

### Build Manually

#### Dependencies

Install the dependencies according to your package manager.

```
$ sudo apt install -y packer vagrant

$ sudo pacman -S --noconfirm packer && yay -S --noconfirm vagrant
```

Install `vagrant` plugins.

```
$ vagrant plugin install vagrant-reload vagrant-vbguest winrm winrm-fs
```

Install `packer` plugins.

```
$ packer plugins install -force github.com/hashicorp/virtualbox
packer plugins install -force github.com/hashicorp/vagrant
packer plugins install -force github.com/hashicorp/chef
```

Ensure the kernel modules for **VirtualBox** are loaded.

```
$ sudo modprobe vboxdrv vboxnetadp vboxnetflt
```

Prevent `E_ACCESSDENIED` errors on **VirtualBox** networking.

```
$ sudo mkdir -p /etc/vbox
echo "* 0.0.0.0/0 ::/0" | sudo tee /etc/vbox/networks.conf
sudo modprobe -r vboxnetadp vboxnetflt
sudo modprobe vboxnetadp vboxnetflt
```

Clone the repository.

> [!INFO]
> Ensure you're in the current directory `metasploitable3` in order to proceed.

```
$ git clone https://github.com/rapid7/metasploitable3.git && \
cd metasploitable3
```

> [!WARNING] DO NOT INTERACT WITH THE VIRTUAL MACHINES!
> Let the installation process finish. Please be patient.

Build and run Ubuntu 14.04 Server.

```
$ packer build -only=virtualbox-iso ./packer/templates/ubuntu_1404.json
vagrant box add packer/builds/ubuntu_1404_virtualbox_0.1.12.box --name=rapid7/metasploitable3-ub1404
vagrant up ub1404
```

Build and run Windows 2008 R2 Server.

```
$ packer build -only=virtualbox-iso ./packer/templates/windows_2008_r2.json
vagrant box add packer/builds/windows_2008_r2_virtualbox_0.1.0.box --name=rapid7/metasploitable3-win2k8
vagrant up win2k8
```

Verify both virtual machines are running.

```
$ vagrant status
```

## Post Installation

### Windows License Popup Removal

Manage the software licensing in Windows Server 2008 R2.

```
C:\> slmgr.exe /rearm
```

## DNS Hosts Addresses

Map the metasploitable3 IPv4 address as a DNS reference.

```
$ sudo nano /etc/hosts
<VM_IP> metasploitable.local
```

## Troubleshooting

### Removing Vagrant VMs

```
$ vagrant destroy -f
```

---
## References

### Source Repositories

- [rapid7: metasploitable3](https://github.com/rapid7/metasploitable3)

- [brimstone: Pre-bundled Metasploitable3 OVA VMs](https://github.com/brimstone/metasploitable3/releases)

- [Metasploitable3 Windows Server 2008 R2](https://archive.org/details/metasploitable3-master_win2k8_1569441065179_55164)

- [Metasploitable3 Ubuntu 14.04](https://sourceforge.net/projects/metasploitable3-ub1404upgraded/files/)