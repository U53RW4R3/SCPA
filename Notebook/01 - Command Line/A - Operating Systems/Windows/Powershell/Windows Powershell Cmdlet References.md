# Windows Powershell Cmdlet Table References

Search Tag(s): #command-line #windows

| Commands                         | Aliases                                               |
| -------------------------------- | ----------------------------------------------------- |
| `Set-Location`                   | [`cd` \| `chdir` \| `sl`]                             |
| `Get-ChildItem`                  | [`dir` \| `gci` \| `ls`]                              |
| `Get-Content`                    | [`cat` \| `gc` \| `type` \| `more`]                   |
| `New-Item`                       | (equivalent to `type nul` in CMD)                     |
| `Copy-Item`                      | [`copy` \| `cp` \| `cpi`]                             |
| `Move-Item`                      | [`mv` \| `mi` \| `move`]                              |
| `Rename-Item`                    | [`ren` \| `rni`]                                      |
| `Remove-Item`                    | [`del` \| `erase` \| `rd` \| `ri` \| `rm` \| `rmdir`] |
| `Get-Location`                   | [`gl` \| `pwd`]                                       |
| `Get-Acl`                        | (equivalent to `icacls` in CMD)                       |
| `Invoke-Command`                 | `icm`                                                 |
| `Invoke-WmiMethod`               | `iwmi`                                                |
| `Invoke-Expression`              | `iex`                                                 |
| `Invoke-WebRequest`              | [`curl` \| `iwr` \| `wget`]                           |
| `Clear-host`                     | [`clear` \| `cls`]                                    |
| `Get-History`                    | [`ghy` \| `h` \| `history`]                           |
| `Clear-History`                  | `clhy`                                                |
| `Write-Host`                     |                                                       |
| `Write-Output`                   | [`echo` \| `write`]                                   |
| `Get-Process`                    | [`gps` \| `ps`]                                       |
| `Start-Process`                  | [`saps` \| `start`]                                   |
| `Stop-Process`                   | [`kill` \| `spps`]                                    |
| `Get-Service`                    | `gsv`                                                 |
| `Start-Service`                  | `sasv`                                                |
| `Stop-Service`                   | `spsv`                                                |
| `Select-Object`                  | `select`                                              |
| `Select-String`                  | `sls` (equivalent to `findstr` in CMD)                |
| `Get-CimInstance`                | `gcim`                                                |
| `Get-ComputerInfo`               | `gin` (equivalent to "systeminfo" in CMD)             |
| `Import-Module`                  | `ipmo`                                                |
| `Get-Module`                     | `gmo`                                                 |
| `New-Module`                     | `nmo`                                                 |
| `Remove-Module`                  | `rmo`                                                 |
| `Tee-Object`                     | `tee`                                                 |
| `Get-NetIPConfiguration`         | `gip` (equivalent to `ipconfig` in CMD)               |
| `Get-NetIPAddress`               |                                                       |
| `Get-NetRoute`                   | (equivalent to `route print` in CMD)                  |
| `Test-Connection -Count <int>`   | (equivalent to `ping -c <int>` in CMD)                |
| `Test-NetConnection -TraceRoute` | (equivalent to `tracert` in CMD)                      |
| `Resolve-Dnsname`                | (equivalent to `nslookup` in CMD)                     |
| `Get-PSDrive`                    | `gdr`                                                 |
| `New-PSDrive`                    | [`ndr` \| `mount`]                                    |
| `Remove-PSDrive`                 | `rdr`                                                 |
| `New-SmbMapping`                 | (equivalent to `net use` in CMD)                      |
| `Get-SmbMapping`                 |                                                       |
| `Remove-SmbMapping`              | (equivalent to `net use /delete` in CMD)              |
| `Get-SmbConnection`              | (equivalent to `net share` in CMD)                    |
