# Checklist

Search Tag(s): #checklist #weaponization #client-side-attacks #phishing #defense-evasion

TODO: Make a cross-reference when making a good checklist for weaponizing when delivery the attack.

## Weaponization

- [ ] Scrape metadata from images and documents. Refer to this [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/04 - Forensics/Checklist|checklist]] to narrow down your search results.
	- [[Exiftool]]
	- [[exifLooter]]
	- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x02 - Privilege Escalation/Linux/Local Privilege Escalation/Superuser/Sudo/Shell Escape Sequences/Exploits/Nmap|Nmap]]

## Phishing

### Social Engineering Pretext

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

### Code Execution

- [ ] Visit [LOLBAS](https://lolbas-project.github.io/lolbas) and [Red Team Notes](https://www.ired.team/offensive-security/code-execution) to change the execution to evade security endpoints.

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/File Attachment/Shortcut Link File/Manual|Weaponization: Manual Shortcut Link File]]