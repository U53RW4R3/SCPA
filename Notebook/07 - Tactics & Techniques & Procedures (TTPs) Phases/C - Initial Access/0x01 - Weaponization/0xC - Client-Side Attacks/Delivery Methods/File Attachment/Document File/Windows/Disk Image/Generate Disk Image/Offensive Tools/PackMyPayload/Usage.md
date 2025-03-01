# Usage

## 01 - Help Menu

```
$ packmypayload -h       
usage: 
+      o     +              o   +      o     +              o
    +             o     +           +             o     +         +
    o  +           +        +           o  +           +          o
-_-^-^-^-^-^-^-^-^-^-^-^-^-^-^-^-^-_-_-_-_-_-_-_,------,      o
   :: PACK MY PAYLOAD (1.3.0)       -_-_-_-_-_-_-|   /\_/\
   for all your container cravings   -_-_-_-_-_-~|__( ^ .^)  +    +
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-__-_-_-_-_-_-_-''  ''
+      o         o   +       o       +      o         o   +       o
+      o            +      o    ~   Mariusz Banach / mgeeky    o
o      ~     +           ~          <mb [at] binary-offensive.com>
    o           +                         o           +           +

Usage: PackMyPayload.py [options] <infile> <outfile>

options:
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
                        If output archive/container format supports password protection, use this password to protect output file.
  --out-format {zip,7z,iso,img,cab,pdf,vhd,vhdx}
                        Explicitely define output format disregarding output file's extension. Can be one of following: zip, 7z, iso, img, cab, pdf, vhd, vhdx
  -H HIDE, --hide HIDE  (Supported in ISO/IMG, ZIP) Set hidden attribute on file(s). Cannot be repeated, only comma-separated. Example: --hide icon.ico,evil.exe . Supports wildcards:
                        --hide icon?.*

ZIP specific options:
  --zip-noreadonly      DISABLE ZIP MOTW bypass that is used by default. By default, PackMyPayload marks Office files as Read-Only making ZIP software unable to set MOTW flag on them when
                        extracted. This option disables that behavior.

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

## 02 - Archive files

> [!INFO]
> Only `.zip` and `.7z` has password protection feature.

```
$ packmypayload [-p <password>] --out-format <zip | 7z | cab | pdf> [<drive_letter>:]\path\to\directory\ archive.<zip | 7z | cab | pdf>
```

## 03 - Pack files inside a disk file

> [!INFO]
> Both `.vhd` and `.vhdx` is done exclusively on windows.

```
$ packmypayload [--vhd-filesystem <fat | fat32 | ntfs>] --out-format <iso | img | vhd | vhdx> file.txt file.<iso | img | vhd | vhdx>
```