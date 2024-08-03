# Checklist

TODO: Make a cross-reference when making a good checklist for weaponizing when delivery the attack.

## Phishing

- [ ] Scrape metadata from images and documents. Refer to this [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/04 - Forensics/Checklist|checklist]] to narrow down your search results.
	- [[Exiftool]]
	- [[exifLooter]]
	- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x02 - Privilege Escalation/Linux/Local Privilege Escalation/Superuser/Sudo/Shell Escape Sequences/Exploits/Nmap|Nmap]]

### Social Engineering Pretext

- Gather emails with the following methods.
	- Passively browse the website 
		- [ ] Search for emails to scrape them.
		- [ ] Search for first and last names to parse them to perform user enumeration with the following.
			- SMTP Network Protocol
				- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/02 - Active Fingerprinting/Enumeration via Network Protocols/SMTP/Manual|Manual username enumeration]]
				- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/02 - Active Fingerprinting/Enumeration via Network Protocols/SMTP/Metasploit|Metasploit username enumeration]]
			- Web mail
	- [ ] OSINT gathering on social media
	- [ ] OSINT gathering using google dorking
		- TODO Fill in the
	- [ ] Data breaches
	- [ ] Parse and verify the emails
- [ ] Check if the domain is spoofable.