# Haiti (HAsh IdenTifIer)

## 01 - Setup

### 1.1 - Dependencies

`$ sudo apt install -y fzf`

`$ gem install haiti-hash`

## 02 - Help Menu

```
$ haiti -h
HAITI (HAsh IdenTifIer) v2.1.0

Usage:
  haiti [options] list
  haiti samples (<ref> | <name>)
  haiti [options] <hash>
  haiti --ascii-art
  haiti -h | --help
  haiti --version

Commands:
  samples         Display hash samples for the given type
  list            Display a list of all the available hash types

Parameters:
  <hash>          Hash string to identify, read from STDIN if equal to "-"
  <ref>           hashcat or john the ripper reference
  <name>          Hash type name

Options:
  --no-color      Disable colorized output (NO_COLOR environment variable is respected too)
  -e, --extended  List all possible hash algorithms including ones using salt
  --short         Display in a short format: do not display hashcat and john the ripper references
  --hashcat-only  Show only hashcat references
  --john-only     Show only john the ripper references
  --ascii-art       Display the logo in colored ascii-art
  --debug         Display arguments
  -h, --help      Show this screen
  --version       Show version

Examples:
  haiti -e d41d8cd98f00b204e9800998ecf8427e
  haiti --no-color --short d41d8cd98f00b204e9800998ecf8427e
  b2sum /etc/os-release | awk '{print $1}' | haiti -
  haiti samples crc32

Project:
  author (https://pwn.by/noraj / https://twitter.com/noraj_rawsec)
  source (https://github.com/noraj/haiti)
  documentation (https://noraj.github.io/haiti)
```

## 03 - Usage

TODO: Fill this info

`$ haiti <hash>`

- Provide hash format output that corresponds [[Tactics && Techniques && Procedures (TTPs) Phases/C - Initial Access/04 - Password Cracking/Offline/JTR|JohnTheRipper]].

`$ haiti --john-only <hash>`

- Provide hash format output that corresponds [[Hashcat]].

`$ haiti --hashcat-only <hash>`

---
## References

- [Haiti (HAsh IdenTifIer)](https://github.com/noraj/haiti)