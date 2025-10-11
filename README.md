# Description

```
> cat banner.txt
   ____ _               _   ____
  / ___| |__   ___  ___| |_/ ___|  ___  ___
 | |  _| '_ \ / _ \/ __| __\___ \ / _ \/ __|
 | |_| | | | | (_) \__ \ |_ ___) |  __/ (__
  \____|_| |_|\___/|___/\__|____/ \___|\___|
```

## `> cat introduction.txt`

The **SCPA (Sophicated Cyber Penetration Attacks)** is for hackers wanting a straight guidance with many sections involves in offensive operations. It outlines in a systematic approach, because there are so many resources that are being broadcast on the internet. I've compiled it together which contains sources have been re-applied providing use cases and scenarios in many ways.

## `> whoarewe && cat about_SCPA_project.txt`

Sebastian Dante Alexander: I'm Sebastian

Userware: and I'm Userware

We've started this project due to our experiences that contains tactics, techniques and procedures (TTP) and we've collected a lot of information just to summarize it all in one. We find it a waste that nobody would go through this effort especially for beginners who barely started. This knowledge will serve you well in your journey.

## Download digital notebook

Sebastian Dante Alexander: Grab a copy to specify a directory using `git` then use [obsidian](https://obsidian.md/) to open the directory.

```
$ git clone --depth=1 https://github.com/ghostsec420/SCPA.git && cd SCPA \
git sparse-checkout set Notebook
```

Userware: Do you want the latest updates? Grab mine instead since most of them is still work in progress continuously.

```
$ git clone --depth=1 https://github.com/U53RW4R3/SCPA.git && cd SCPA \
git sparse-checkout set Notebook
```

## Legends indicators in digital notebook

### Parameters

- `<>` -> Required paramaters (e.g. `<IP>`, `<username>`, `<password>`)
- `[]` -> Optional contextual paramaters (e.g. `[/flag-option]`, `[args]`)
- `[<>]` -> Optionally contextual required parameters (e.g. `[<bind_IP>]`, `[<PORT>]`)
- `()` -> Grouped parameter

### Terminal Prompts

#### Cross Platform

`>` -> Universal terminal prompt (i.e. `> <command>`)

#### Unix Shell

- `$` -> Non-elevated user privileges unix-like shell prompt (i.e. `user@hostname:~$ <command>`)
- `#` -> Elevated user privileges unix-like shell prompt (i.e. `root@hostname:~# <command>`)

#### PowerShell

- `PS />` -> PowerShell Linux console prompt (i.e. `PS /home/USERNAME> <command>`)
- `PS <drive_letter>:\>` -> Powershell console prompt (i.e. `PS C:\> <cmdlet>`)

#### Windows

`<drive_letter>:\>` -> Windows command prompt (i.e. `C:\> <command>`)

# WORK TO DO

- [ ] Add tags
- [ ] Left a lot of TODO labels so go check it out users
- [ ] Add Active Directory Lab in the **Lab Simulation Setup**
- [ ] Include references and remove some duplicates
- [ ] Fill in the information of **Hacking The Cloud**
- [ ] Provide a mindmap to some sections if necessary

# Roadmap

- [ ] **Cryptography** section
- [ ] **Container (docker, kubernetes, LXC)** section
- [ ] **Malware Development** section
- [ ] **Exploit development** section
- [ ] **Writing Reports** section (maybe)
- [ ] Include MITRE ATT&CK techniques References

---
## References

- [Hacktricks](https://book.hacktricks.xyz/)

- [Payloads All The Things](https://swisskyrepo.github.io/PayloadsAllTheThings/)

- [Internal All The Things](https://swisskyrepo.github.io/InternalAllTheThings/)

- [Red Team Notes](https://www.ired.team)

- [The Hacker Recipes: The Hacker Tools](https://tools.thehacker.recipes/)

- [DMCXBlue: Red Team Notes](https://dmcxblue.gitbook.io/red-team-notes)

- [N7W Era Infrastructure Penetration Testing Notes](https://infra.newerasec.com)

- [Persistence Info](https://persistence-info.github.io/)
