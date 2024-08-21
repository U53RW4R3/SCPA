# Checklist

Search Tag(s): #checklist #weaponization #client-side-attacks #phishing #defense-evasion

TODO: Make a cross-reference when making a good checklist for weaponizing when delivering the attack.

## Passive Client Information Gathering

- [ ] Scrape metadata from images and documents. Refer to this [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/04 - Forensics/Checklist|checklist]] to narrow down your search results.
	- [[Exiftool]]
	- [[exifLooter]]
	- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x02 - Privilege Escalation/Linux/Local Privilege Escalation/Superuser/Sudo/Shell Escape Sequences/Exploits/Nmap|Nmap]]

## Active Client Information Gathering

- [ ] Interact with the targets through communications to gather information.
	- [ ] Communication via a phone call.
	- [ ] Communication via a person.

## Phishing Preparation

- [ ] For social engineering pretext visit this [[Social Engineering Pretext|section]] to make preparation for your campaign.
- [ ] Choose which phishing delivery method for the campaign.
	- [ ] Phishing via Email
		- Gather emails with the following methods.
			- Passively browse the website 
				- [ ] Search for emails to scrape them.
				- [ ] Search for first and last names to parse them to perform user enumeration with the following.
					- SMTP Port
						- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Enumeration/Mail Server/SMTP/Manual|Manual username enumeration]]
						- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Enumeration/Mail Server/SMTP/Metasploit|Metasploit username enumeration]]
					- Web mail
			- [ ] OSINT gathering on social media
			- [ ] OSINT gathering using google dorking
				- TODO Fill in the
			- [ ] Data breaches
			- [ ] Parse and verify the emails
		- [ ] Check if the domain is spoofable.
	- [ ] Phishing via Service
		- Social Media
	- [ ] Smishing (SMS Phishing)
	- [ ] Vishing (voice phishing)

## File Attachment

Note: You can be creative by combing multiple files.

- [ ] Check **Command and Scripting Interpreter** section to change the execution methods.
- [ ] [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/HTML Smuggling/Manual|HTML Smuggling]]
- [ ] Macros
	- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Microsoft Office/Macros/Craft Manually with Macro Delivery|Microsoft Office]]
	- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/LibreOffice/Macros/Craft Manually with Macro Delivery|LibreOffice Macro]]
- [ ] Macroless
	- [[Word|Word OLE Object]]
	- [[Excel]]
	- [[PowerPoint]]
- [ ] Deploy Implant (Trojan Horse).
	- [ ] Executable file (`.exe`).
		- [ ] Custom Dropper
			- [ ] Disguise it with an icon.
			- [ ] Append a **RTLO (Right to Left Override)** to make the extension look legitimate.
		- [ ] Backdoor the executable file
			- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Backdoor EXEcutable Files/Manual|Manual]]
			- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Backdoor EXEcutable Files/MSFVenom|MSFVenom]]
			- [[Shellter|Shellter]]
	- [ ] HTML Application (`.hta`)
	- [ ] Installer
		- [ ] MSI
		- [ ] ClickOnce
- [ ] [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Shortcut Link File/Manual|Shortcut Link]] (`.lnk`)
	- [ ] Decoy file.

### Bypass MOTW (Mark of the Web)

Note: You can be creative by combing multiple files.

- [ ] Archive Files
	- 7Zip
		- [ ] Password protected
	- CAB
- [ ] Disk container
	- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Disk Image/Generate Disk Image/Automated/PackMyPayload/Usage|PackMyPayload]]
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
	- [ ] Using [[Word|Word OLE Object]] to embed inside a file.
	- [ ] Using **OneNote** to embed inside a file.
	- [ ] Using **Adobe Reader** or **Foxit** to embed inside a file.
	- [ ] Shortcut `.lnk` file.
		- [ ] Shell Scripting
			- Batch (`.bat` or `.cmd`)
			- VBScript (`.vbs`)
	- [ ] HTML Application (`.hta`) with macros inside using [[Macros Template|DCOM]] method.
- [ ] Using [[Word|Word OLE Object]] to embed inside a file.
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

## Physical Penetration

### Evil Twin

- [[Rogue Access Point]]

### Whaling

- [ ] TODO: Fill in the info

### BadUSB

- [ ] [[Arduino]]
- [ ] [[Hak5 Devices]]