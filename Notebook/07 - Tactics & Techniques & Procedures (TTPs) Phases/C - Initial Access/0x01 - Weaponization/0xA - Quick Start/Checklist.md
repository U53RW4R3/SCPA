# Checklist

Search Tag(s): #checklist #weaponization #client-side-attacks #phishing #defense-evasion

TODO: Make a cross-reference when making a good checklist for weaponizing when delivering the attack.

## Weaponization

- [ ] Scrape metadata from images and documents. Refer to this [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/04 - Forensics/Checklist|checklist]] to narrow down your search results.
	- [[Exiftool]]
	- [[exifLooter]]
	- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x02 - Privilege Escalation/Linux/Local Privilege Escalation/Superuser/Sudo/Shell Escape Sequences/Exploits/Nmap|Nmap]]

### Phishing Preparation

- [ ] For social engineering pretext visit this [[Social Engineering Pretext|section]] to make preparation for your campaign.
- [ ] Choose which phishing delivery method for the campaign.
	- [ ] Phishing
		- Gather emails with the following methods.
			- Passively browse the website 
				- [ ] Search for emails to scrape them.
				- [ ] Search for first and last names to parse them to perform user enumeration with the following.
					- SMTP Port
						- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/02 - Active Fingerprinting/Enumeration via Network Protocols/SMTP/Manual|Manual username enumeration]]
						- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/02 - Active Fingerprinting/Enumeration via Network Protocols/SMTP/Metasploit|Metasploit username enumeration]]
					- Web mail
			- [ ] OSINT gathering on social media
			- [ ] OSINT gathering using google dorking
				- TODO Fill in the
			- [ ] Data breaches
			- [ ] Parse and verify the emails
		- [ ] Check if the domain is spoofable.
	- [ ] Smishing (SMS Phishing)
	- [ ] Vishing (voice phishing)

### File Attachment

Note: You can be creative by combing multiple files.

- [ ] Check **LOLBAS** section to change the execution methods.
- [ ] [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/HTML Smuggling/Manual|HTML Smuggling]]
- Office
	- [ ] Macros
		- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Microsoft Office/Macros/Craft Manually with Macro Delivery|Microsoft Office]]
		- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/LibreOffice/Macros/Craft Manually with Macro Delivery|LibreOffice Macro]]
	- [ ] Macroless
		- [[Word]]
		- [[Excel]]
		- [[PowerPoint]]
- [ ] Trojan Horse
	- [ ] Executable file (`.exe`).
		- [ ] Custom Dropper
			- [ ] Disguise it with an icon.
			- [ ] Append a **RTLO (Right to Left Override)** to make the extension look legitimate.
		- [ ] Backdoor the executable file
			- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Backdoored EXEcutable Files/Manual|Manual]]
			- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Backdoored EXEcutable Files/MSFVenom|MSFVenom]]
			- [[Shellter|Shellter]]
	- [ ] HTML Application (`.hta`)
	- [ ] MSI Installer (`.msi`)
- [ ] [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Shortcut Link File/Manual|Shortcut Link]] (`.lnk`)
	- [ ] Decoy file.
- Store files to safeguard from **MOTW (Mark of the Web)**.
	- [ ] Archive Files
		- 7Zip
	- [ ] Disk container
		- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Disk Image/Generate Disk Image/Automated/PackMyPayload/Program/Usage|PackMyPayload]]
	- [ ] Password protected if using an archive program.

### Physical Penetration

#### Evil Twin

- [[Rogue Access Point]]

#### Whaling

- [ ] TODO: Fill in the info

#### BadUSB

- [ ] [[Arduino]]
- [ ] [[Hak5 Devices]]