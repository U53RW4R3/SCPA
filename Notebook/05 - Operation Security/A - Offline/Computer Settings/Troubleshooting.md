# Troubleshooting

## Diagnose Power Efficiency

```
C:\> powercfg.exe /energy
```

## Check Boot Configuration

```
C:\> bcedit.exe /enum
```

## System Cleanup

```
C:\> Dism.exe /Online /Cleanup-Image /Restorehealth
```

Checks if there's something wrong with the disk(s).

```
C:\> chdsk.exe <drive_letter>: /f /r /x
```

Repair files and remove unwanted programs (i.e. malware).

```
C:\> sfc.exe /scannow
```