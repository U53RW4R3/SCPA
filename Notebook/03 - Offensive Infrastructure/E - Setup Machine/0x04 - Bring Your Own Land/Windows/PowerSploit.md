# PowerSploit

## PowerUp

Import `PowerUp` Module

```
PS C:\> Import-Module .\PowerUp.ps1
```

List the `cmdlets` from the module.

```
PS C:\> Get-Command -Module PowerUp
```

Audit the system.

```
PS C:\> Invoke-PrivescAudit

PS C:\> Invoke-AllChecks
```

---
## References

### Source Repositories

- [PowerSploit](https://github.com/PowerShellMafia/PowerSploit)