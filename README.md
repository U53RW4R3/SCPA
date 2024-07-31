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

## `> whoami && cat about_SCPA_project.txt`

I'm Userware and I've started this project due to my experience that contains tactics, techniques and procedures (TTP) and I've collected a lot of information just to summarize it all in one. I find it a waste that nobody would go through this effort especially for beginners who are still starting out. This knowledge will serve you well in your journey.

## Download digital notebook

Grab a copy to specify a directory using `git` then use [obsidian](https://obsidian.md/) to open the directory.

```
$ git clone --depth=1 https://github.com/ghostsec420/SCPA.git && cd SCPA \
git sparse-checkout set Notebook
```

## Legends indicators in digital notebook

### Parameters

- `<>` -> Required paramaters (e.g. `<IP>`, `<username>`, `<password>`)
- `[]` -> Optional contextual paramaters (e.g. `[/flag-option]`, `[args]`)
- `[<>]` -> Optionally contextual required parameters (e.g. `[<bind_IP>]`, `[<PORT>]`)
- `()` -> Grouped parameter

### Terminal Prompts

- `>` -> Universal terminal prompt (i.e. `> <command>`)
- `$` -> Non-elevated user privileges unix-like shell prompt (i.e. `user@hostname:~$ <command>`)
- `#` -> Elevated user privileges unix-like shell prompt (i.e. `root@hostname:~# <command>`)
- `PS />` -> PowerShell Linux console prompt (i.e. `PS /home/USERNAME> <command>`)
- `<drive_letter>:\>` -> Windows command prompt (i.e. `C:\> <command>`)
- `PS <drive_letter>:\>` -> Powershell console prompt (i.e. `PS C:\> <cmdlet>`)

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
