# Red Team Methodology

## Information Gathering

1. Passive Fingerprint
    + OSINT
        - [OSINTFramework](https://osintframework.com)
        - https://cipher387.github.io/osint_stuff_tool_collection/
        - https://github.com/nayanamana/et_tu_brute_thewebconf_22
2. Active Fingerprint
    + Port Scanning
        - https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Network%20Discovery.md
    + Enumeration
        - HTTP Enumeration
            - https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Subdomains%20Enumeration.md
        - SMB Enumeration
            - [A Little Guide to SMB Enumeration](https://www.hackingarticles.in/a-little-guide-to-smb-enumeration/)

## Password Attacks

1. Offline Attacks
    - https://github.com/J3rryBl4nks/PasswordCrackingMethodology
    - https://www.infosecmatter.com/cisco-password-cracking-and-decrypting-guide/
2. Online Attacks
    -  https://securitytutorials.co.uk/brute-forcing-passwords-with-thc-hydra/
    -  https://hackertarget.com/brute-forcing-passwords-with-ncrack-hydra-and-medusa/

## Wireless Attacks

1. Overview
    - https://github.com/morrownr/USB-WiFi

## Sniffing and Spoofing

- 

## Forensics

- https://itsfoss.com/recover-deleted-files-linux/

## Cryptography

- https://github.com/sobolevn/awesome-cryptography

## WebApp Hacking

1. Overview
    - https://github.com/R0B1NL1N/WebHacking101
2. OWASP
    - https://shahrukhathar.info/local-file-inclusion-lfi-cheat-sheet/
3. Pentest-Ground
    - https://pentest-ground.com/

## Post Exploitation

1. Overview
    - https://github.com/yeyintminthuhtut/Awesome-Red-Teaming
    - https://github.com/RoseSecurity/Red-Teaming-TTPs
    - https://pentestwiki.org/post-exploitation/
    - https://blog.certcube.com/osep-preparation-methodology-learning-track/
    - https://github.com/0xOverflow/RedTeam-Physical-Tools
    - https://github.com/marcosValle/awesome-windows-red-team
    - http://pwnwiki.io
    - https://www.ired.team && https://github.com/mantvydasb/RedTeam-Tactics-and-Techniques
    - https://github.com/TheParmak/conti-leaks-englished
    - https://luemmelsec.github.io/Circumventing-Countermeasures-In-AD/
    - https://lots-project.com/
    - https://www.expireddomains.net/expired-domains/
    - https://henpeebin.com/kevin/blog/bypassing-firewalls.html
2. Setup Active Directory
    - https://chryzsh.gitbooks.io/darthsidious/content/ && https://github.com/chryzsh/DarthSidious
    - https://blog.certcube.com/local-active-directory-implementation-1/
    - https://blog.certcube.com/local-active-directory-implementation-2/
    - https://redteamtechniques.github.io/Windows%20&%20AD%20Hacking/
3. Post Exploitation
    + Overview
        * Linux
            - 
        * Windows
            - https://github.com/emilyanncr/Windows-Post-Exploitation
        * https://github.com/center-for-threat-informed-defense/adversary_emulation_library
    + MindMap
        * https://www.xmind.net/m/QsNUEz/
        * https://github.com/umuttosun/OSCP-MindMap/
    + Initial Foothold
        * Windows
            - https://1337red.wordpress.com/using-a-scf-file-to-gather-hashes
            - https://redteamzone.com/EternalBlue/
        * https://filesec.io/
    + Privilege Escalation
        * https://pentestwiki.org/privilege-escalation-in-windows-and-linux/
        * Linux
            - https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/
            - https://blog.certcube.com/linux-privilege-escalation-part-tools-techniques/
            - https://payatu.com/guide-linux-privilege-escalation
            - https://int0x33.medium.com/day-44-linux-capabilities-privilege-escalation-via-openssl-with-selinux-enabled-and-enforced-74d2bec02099
        * Windows
            - https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_windows.html
            - https://github.com/geeksniper/windows-privilege-escalation
            - https://blog.certcube.com/windows-privilege-escalation-methods/
            - https://blog.certcube.com/windows-privilege-escalation-part-2/
            - https://blog.certcube.com/windows-privilege-escalation-part-3/
            - https://blog.certcube.com/windows-kernel-exploitation-part-4/
            - https://blog.certcube.com/step-by-step-guide-to-learn-the-windows-privilege-escalation/
            -  [Abusing DNSAdmins](https://www.labofapenetrationtester.com/2017/05/abusing-dnsadmins-privilege-for-escalation-in-active-directory.html)
            - https://juggernaut-sec.com/uac-bypass/
        *  [Linux and Windows Privesc](https://pentestwiki.org/privilege-escalation-in-windows-and-linux/)
    + Lateral Movement
        * https://blog.certcube.com/pivoting-port-forwarding/
        * [SSH & Meterpreter Pivoting Techniques](https://web.archive.org/web/20220605072526/https://highon.coffee/blog/ssh-meterpreter-pivoting-techniques)
        * Pivoting
            - https://pentestwiki.org/pivoting
            - https://github.com/opsdisk/the_cyber_plumbers_handbook
            - Linux
                1. SSH Tunneling
                    - https://blog.certcube.com/pivoting-and-ssh-port-forwarding-basics/
                    - https://gist.github.com/rfairley/41f4a8e8b4c13f19d748ba4b0e600cc5
            - Windows
                - https://rastamouse.me/ntlm-relaying-via-cobalt-strike/
                - https://posts.specterops.io/offensive-lateral-movement-1744ae62b14f
    + Exfiltration
        * Linux
            -
        * Windows
            -
        * WebApps
            - https://serverpilot.io/docs/where-to-find-your-database-credentials-in-joomla/
4. Living off the Land (LotL)
    + Linux
        * [GTFOBins](https://gtfobins.github.io)
    + Windows
        * [LOLBAS](https://lolbas-project.github.io/)
5. Bring Your Own Island (BYOL)
    + Mandiant
        * https://www.mandiant.com/resources/blog/live-off-the-land-an-overview-of-unc1945
6. Defense Evasion
    + Metasploit
        * SSL Impersonation
            - https://github.com/blumirabrian/endpoint-detection-methology
            - https://cyberstruggle.org/symantec-end-point-protection-bypass-meterpreter-pivoting/
    + Empire
        * https://flikk.blog/2022/01/25/modifying-empire-payloads-to-avoid-detection/
    + Anti-Forensics
        * https://pentestwiki.org/covering-tracks/