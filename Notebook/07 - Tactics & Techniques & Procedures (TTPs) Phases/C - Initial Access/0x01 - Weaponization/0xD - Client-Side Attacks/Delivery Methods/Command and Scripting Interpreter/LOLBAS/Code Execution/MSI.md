# MSI

## Table reference

| Flag     | Description                                            |
| -------- | ------------------------------------------------------ |
| `/quiet` | Suppress any messages to the user during installation. |
| `/qn`    | No GUI                                                 |
| `/i`     | Regular (vs. administrative) installation              |

```
C:\> msiexec /quiet /qn /i implant.msi "C:\path\to\implant.msi"
```

---
## References

- [LOLBAS: Msiexec](https://lolbas-project.github.io/lolbas/Binaries/Msiexec/)