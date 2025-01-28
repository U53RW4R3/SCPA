# PCOM

Search Tag(s): #information-gathering #network-protocols #network-mapper

Download the NSE script and update the local database.

```
$ sudo wget -qO /usr/share/nmap/scripts/pcom-discover.nse https://raw.githubusercontent.com/selmux/ICS-Security/refs/heads/main/Nmap%20ICS-OT%20Scripts/cldrn/pcom-discover.nse
sudo nmap --script-updatedb
```

Perform recon.

```
$ nmap --script pcom-discovery [--script-args='pcom-discover.aggressive=true'] -p 20256 <IP>
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xD - Network Enumeration/IoTs/Operation Technology/Unitronic PLC|OSINT: Unitronic PLC]]

- [selmux: ICS-Security - PCOM Discovery NSE Script](https://github.com/selmux/ICS-Security/blob/main/Nmap%20ICS-OT%20Scripts/cldrn/pcom-discover.nse)