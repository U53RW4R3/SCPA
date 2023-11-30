# Calculate the size of the data

Search Tag(s): #command-line #use-cases #windows

```
PS C:\> Get-ChildItem -Path \\<IP>\C$\path\to\directory -Recurse -File | Measure-Object -Sum Length | Select-Object Count, Sum

PS C:\> Get-ChildItem -Path C:\path\to\directory -Recurse -File | Measure-Object -Sum Length | Select-Object Count, Sum
```

---
## References

- [[Windows Powershell Cmdlet References]]