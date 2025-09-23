# SharpHound

## 01 - Compile

```
C:\> git clone https://github.com/BloodHoundAD/SharpHound

C:\> cd Sharphound

C:\Sharphound> dotnet build -c Release -p:TargetFrameworkVersion=v4.8.1
```

## 02 - Help Menu

```
C:\> SharpHound.exe --help
2023-06-26T15:29:59.9659992-07:00|INFORMATION|This version of SharpHound is compatible with the 4.3.1 Release of BloodHound
SharpHound 1.1.1
Copyright (C) 2023 SpecterOps

  -c, --collectionmethods      (Default: Default) Collection Methods: Group, LocalGroup, LocalAdmin, RDP, DCOM,
                               PSRemote, Session, Trusts, ACL, Container, ComputerOnly, GPOLocalGroup, LoggedOn,
                               ObjectProps, SPNTargets, Default, DCOnly, All

  -d, --domain                 Specify domain to enumerate

  -s, --searchforest           (Default: false) Search all available domains in the forest

  --stealth                    Stealth Collection (Prefer DCOnly whenever possible!)

  -f                           Add an LDAP filter to the pregenerated filter.

  --distinguishedname          Base DistinguishedName to start the LDAP search at

  --computerfile               Path to file containing computer names to enumerate

  --outputdirectory            (Default: .) Directory to output file too

  --outputprefix               String to prepend to output file names

  --cachename                  Filename for cache (Defaults to a machine specific identifier)

  --memcache                   Keep cache in memory and don't write to disk

  --rebuildcache               (Default: false) Rebuild cache and remove all entries

  --randomfilenames            (Default: false) Use random filenames for output

  --zipfilename                Filename for the zip

  --nozip                      (Default: false) Don't zip files

  --zippassword                Password protects the zip with the specified password

  --trackcomputercalls         (Default: false) Adds a CSV tracking requests to computers

  --prettyprint                (Default: false) Pretty print JSON

  --ldapusername               Username for LDAP

  --ldappassword               Password for LDAP

  --domaincontroller           Override domain controller to pull LDAP from. This option can result in data loss

  --ldapport                   (Default: 0) Override port for LDAP

  --secureldap                 (Default: false) Connect to LDAP SSL instead of regular LDAP

  --disablecertverification    (Default: false) Disables certificate verification when using LDAPS

  --disablesigning             (Default: false) Disables Kerberos Signing/Sealing

  --skipportcheck              (Default: false) Skip checking if 445 is open

  --portchecktimeout           (Default: 500) Timeout for port checks in milliseconds

  --skippasswordcheck          (Default: false) Skip check for PwdLastSet when enumerating computers

  --excludedcs                 (Default: false) Exclude domain controllers from session/localgroup enumeration (mostly
                               for ATA/ATP)

  --throttle                   Add a delay after computer requests in milliseconds

  --jitter                     Add jitter to throttle (percent)

  --threads                    (Default: 50) Number of threads to run enumeration with

  --skipregistryloggedon       Skip registry session enumeration

  --overrideusername           Override the username to filter for NetSessionEnum

  --realdnsname                Override DNS suffix for API calls

  --collectallproperties       Collect all LDAP properties from objects

  -l, --Loop                   Loop computer collection

  --loopduration               Loop duration (hh:mm:ss - 05:00:00 is 5 hours, default: 2 hrs)

  --loopinterval               Add delay between loops (hh:mm:ss - 00:03:00 is 3 minutes)

  --statusinterval             (Default: 30000) Interval in which to display status in milliseconds

  -v                           (Default: 2) Enable verbose output

  --help                       Display this help screen.

  --version                    Display version information.
```

## 03 - Usage

TODO: Provide more usage examples

```
C:\> SharpHound.exe -c Default -d <domain> --zipfilename ad-output.zip
```

```
C:\> SharpHound.exe --excludedomaincontrollers --stealth --nosavecache
```

```
C:\> SharpHound.exe --excludedomaincontrollers -c ACL --nosavecache
```

---
## References

### Source Repositories

- [SharpHound](https://github.com/BloodHoundAD/SharpHound)

- [Bloodhound](https://bloodhound.readthedocs.io/)