---
author(s):
  - Userware
tags:
  - checklist
  - initial-access
  - weaponization
  - client-side-attacks
  - phishing
  - defense-evasion
---
# Checklist

TODO: Make a cross-reference when making a good checklist for weaponizing when delivering the attack.

## Passive Client Information Gathering

- [ ] Scrape metadata from images and documents. Refer to this [[06 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x04 - Forensics/Checklist|checklist]] to narrow down your search results.
	- [[Exiftool]]
	- [[exifLooter]]
	- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x02 - Privilege Escalation/Linux/Local Privilege Escalation/Superuser/Sudo/Shell Escape Sequences/Exploits/Network Scanners/Network Mapper|Network Mapper]]
- [ ] Look for job requirements of what technology that the target(s) using that can be weaponized.

## Active Client Information Gathering

- [ ] Interact with the targets through communications to gather information.
	- [ ] Communication via a phone call.
	- [ ] Communication via a person.

## Phishing Preparation

- [ ] For social engineering pretext visit this [[Social Engineering Pretext|section]] to make preparation for the campaign.
- Choose which phishing delivery method for the campaign.
	- [ ] Phishing via Email
		- Gather emails with the following methods.
			- Passively browse the website 
				- [ ] Search for emails to scrape them.
				- [ ] Search for first and last names to parse them to perform user enumeration with the following.
					- SMTP Port
						- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/Mail Server/SMTP|Username enumeration]]
					- Web mail
			- [ ] OSINT gathering on social media
			- [ ] OSINT gathering using google dorking
				- TODO: Fill in the bullet points/checkboxes
			- [ ] Data breaches
			- [ ] Parse and verify the emails
		- [ ] Check if the domain is spoofable.
	- [ ] Phishing via Service
		- Social Media
	- [ ] Smishing (SMS Phishing)
	- [ ] Vishing (voice phishing)

## File Attachment

> [!NOTE]
> You can be creative by combining multiple files.

- [ ] Check **Command and Scripting Interpreter** section to change the execution methods.
- [ ] [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Cross Platform/HTML Smuggling/Manual|HTML Smuggling]]
- [ ] Macros
	- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Microsoft Office/Windows/Macros/Manual|Microsoft Office]]
	- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Cross Platform/LibreOffice/Manual|LibreOffice Macro]]
- [ ] Macroless
	- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Microsoft Office/Windows/Macroless/Word/Manual|Word OLE Object]]
	- [[Excel]]
- [ ] Deploy Payload (Trojan Horse).
	- [ ] Disguise it with an icon.
	- [[Spoof Payloads|Double File Extension]]
	- [ ] Append a [[Spoof Payloads|RTLO (Right to Left Override)]] to make the extension look legitimate.
	- [ ] Mac OSX application (`.app`) or [[AppleScript|applescript]].
		- [ ] [[Spoof Payloads|Space After Filename]]
	- [ ] Windows Executable file (`.exe`).
		- [ ] Backdoor the executable file
			- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Payloads/Desktop/Windows/Backdoor EXEcutable Files/Manual|Manual]]
			- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Payloads/Desktop/Windows/Backdoor EXEcutable Files/MSFVenom|MSFVenom]]
			- [[Shellter|Shellter]]
	- [ ] HTML Application (`.hta`)
	- [ ] Installer
		- [ ] MSI
		- [ ] ClickOnce
- [ ] [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Shortcut File/Windows/Offensive Tools|Shortcut Link]] (`.lnk`)
	- [ ] Decoy file.

### Bypass MOTW (Mark of the Web)

> [!NOTE]
> You can be creative by combing multiple files. Use polyglot to your advantage.

- [ ] Archive Files
	- 7Zip
		- [ ] Password protected
	- CAB
- [ ] Disk container
	- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Windows/Disk Image/Generate Disk Image/Offensive Tools/PackMyPayload/Usage|PackMyPayload]]
		- [ ] Add archive file.
			- 7zip
				- [ ] Password protected.
			- Zip
				- [ ] Password protected.
			- CAB
			- Tarball
		- [ ] Spoof file attachment inside the container.
			- [ ] [[01 - Format NTFS Disk Image|Format NTFS Disk Image]]
			- [ ] [[02 - Alternate Data Stream|Alternate data stream]] inside Linux.
			- [ ] [[03 - Spoof ZoneTransfer (MOTW Bypass)|Append fake zonetransfer]] inside linux.
		- [ ] Archive all files inside a disk container image.
			- ISO
			- IMG
			- VHD
			- VHDX
- [ ] Enable and execute VBA macros
	- [ ] Add archive file.
		- 7zip
			- [ ] Password protected.
		- CAB
		- Tarball
	- [ ] Using [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Microsoft Office/Windows/Macroless/Word/Manual|Word OLE Object]] to embed inside a file.
	- [ ] Using **OneNote** to embed inside a file.
	- [ ] Using **Adobe Reader** or **Foxit** to embed inside a file.
	- [ ] Shortcut `.lnk` file.
		- [ ] Shell Scripting
			- Batch (`.bat` or `.cmd`)
			- VBScript (`.vbs`)
	- [ ] HTML Application (`.hta`) with macros inside using [[Microsoft Office Macros|DCOM]] method.
- [ ] Using [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Microsoft Office/Windows/Macroless/Word/Manual|Word OLE Object]] to embed inside a file.
	- [ ] Add archive file.
		- 7zip
			- [ ] Password protected.
		- Zip
			- [ ] Password protected.
		- CAB
		- Tarball
	- [ ] Shortcut `.lnk` file.
	- [ ] HTML Application (`.hta`)
	- [ ] Installer
		- [ ] MSI
		- [ ] ClickOnce
	- [ ] Shell Scripting
		- Batch (`.bat` or `.cmd`)
		- VBScript (`.vbs`)
- [ ] Using **OneNote** to embed inside a file.
	- [ ] Add archive file.
		- 7zip
			- [ ] Password protected.
		- Zip
			- [ ] Password protected.
		- CAB
		- Tarball
	- [ ] Shortcut `.lnk` file.
	- [ ] HTML Application (`.hta`)
	- [ ] Installer
		- [ ] MSI
		- [ ] ClickOnce
	- [ ] Shell Scripting
		- Batch (`.bat` or `.cmd`)
		- VBScript (`.vbs`)
- [ ] Using **Adobe Reader** or **Foxit** to embed inside a file.
	- [ ] Add archive file.
		- 7zip
			- [ ] Password protected.
		- Zip
			- [ ] Password protected.
		- CAB
		- Tarball
	- [ ] Shortcut `.lnk` file.
	- [ ] HTML Application (`.hta`)
	- [ ] Installer
		- [ ] MSI
		- [ ] ClickOnce
	- [ ] Shell Scripting
		- Batch (`.bat` or `.cmd`)
		- VBScript (`.vbs`)

### Package Manager

- [ ] Trojanize [[Package File Templates|software package]] in Linux.

## Physical Penetration

### Evil Twin

- [ ] [[Evil Twin]]

### Whaling

- [ ] TODO: Fill in the info

### BadUSB

- [ ] [[02 - BadUSB]]
- [ ] [[03 - Bash Bunny]]