# SourcePoint

Search Tag(s): #red-team-infrastructure #cobalt-strike

## 01 - Help Menu

```
$ ./SourcePoint -h

	   _____                            ____        _       __ 
	  / ___/____  __  _______________  / __ \____  (_)___  / /_
	  \__ \/ __ \/ / / / ___/ ___/ _ \/ /_/ / __ \/ / __ \/ __/
	 ___/ / /_/ / /_/ / /  / /__/  __/ ____/ /_/ / / / / / /_  
	/____/\____/\__,_/_/   \___/\___/_/    \____/_/_/ /_/\__/  
  							(@Tyl0us)
															 
Usage of ./SourcePoint:
  -Allocation string
    	Minimum amount of memory to request for injected content (must be higher than 4096)
  -CDN string
    	CDN cookie name (typically used for AzureEdge profiles)
  -CDN-Value string
    	CDN cookie value (typically used for AzureEdge profiles)
  -Customuri string
    	The base URI for custom HTTP GET/POST profile - Cannot be used with CustomuriGET or CustomuriPOST
  -CustomuriGET string
    	The base URI for custom HTTP GET profile - Must be used with CustomuriPOST
  -CustomuriPOST string
    	The base URI for custom HTTP POST profile - Must be used with CustomuriGET
  -Datajitter string
    	Appends a value to HTTP-Get and HTTP-Post server output (default "50")
  -Forwarder
    	Enabled the X-forwarded-For header (Good for when your C2 is behind a redirector)
  -Host string
    	Team server domain name
  -Httplib string
    	Select the default HTTP Beacon library:
    	[*] wininet
    	[*] winhttp' (default "winhttp")
  -Injector string
    	Select the preferred method to allocate memory in the remote process:
    	[*] VirtualAllocEx (Great for cross architecture i.e x86 -> x64 and x64->x86)
    	[*] NtMapViewOfSection (A more stealthly option, however fails over to VirtualAllocEx, generating more events when it does)
  -Jitter string
    	Jitter percentage for beacon call home
  -Keylogger string
    	Select the preferred method the beacon will use to log keystrokes: 
    	[*] GetAsyncKeyState (Uses GetAsyncKeyState API (Separate DLL for x86/x64 process))
    	[*] SetWindowsHookEx (Uses SetWindowsHookEx API)
  -Keystore string
    	SSL keystore name
  -Metadata string
    	Specifies how to transform and embed metadata into the HTTP request:
    	[*] base64
    	[*] base64url
    	[*] netbios
    	[*] netbiosu (default "base64url")
  -Outfile string
    	Name of output file
  -PE_Clone string
    	PE file beacon will mimic (Use the number):
    	[1] ActivationManager.dll
    	[2] audioeng.dll
    	[3] AzureSettingSyncProvider.dll
    	[4] BingMaps.dll
    	[5] DIAGCPL.dll
    	[6] EDGEHTML.dll
    	[7] FILEMGMT.dll
    	[8] FIREWALLCONTROLPANEL.dll
    	[9] GPSVC.dll
    	[10] gpupvdev.dll
    	[11] libcrypto.dll
    	[12] srvcli.dll
    	[13] srvsvc.dll
    	[14] Windows.Storage.Search.dll
    	[15] Windows.System.Diagnostics.dll
    	[16] Windows.System.Launcher.dll
    	[17] Windows.System.SystemManagement.dll
    	[18] Windows.UI.BioFeedback.dll
    	[19] Windows.UI.BlockedShutdown.dll
    	[20] Windows.UI.Core.TextInput.DLL
    	[21] winsqlite3.dll
    	[22] WMNetMgr.DLL
    	[23] wwanapi.dll
    	[24] WWANSVC.DLL
    	[25] wow64win.dll
    	[26] wow64.dll
    	[27] ctiuser.dll (Carbon Black's DLL)
    	[28] InProcessClient.dll (SentinelOne's DLL)
    	[29] umppc.dll (CrowdStrike's DLL)
    	[30] CyMemDef64.dll (Cylance's DLL)
  -Password string
    	SSL certificate password
  -PostEX_Name string
    	File Post-Ex activities will spawn and inject into (Use the number):
    	[1] WerFault.exe
    	[2] WWAHost.exe
    	[3] choice.exe
    	[4] bootcfg.exe
    	[5] dtdump.exe
    	[6] expand.exe
    	[7] fsutil.exe
    	[8] gpupdate.exe
    	[9] gpresult.exe
    	[10] logman.exe
    	[11] mcbuilder.exe
    	[12] mtstocom.exe
    	[13] pcaui.exe
    	[14] powercfg.exe
    	[15] svchost.exe
  -Profile string
    	HTTP GET/POST profile (Use the number):
    	[1] Windowsupdate
    	[2] Slack
    	[3] Gotomeeting
    	[4] Outlook.Live
    	[5] Safebrowsing [Cloudfront Compatible]
    	[6] AzureEdge [AzureEdge Compatible]
    	[7] Field-Keyword [Cloudfront Compatible]
    	[8] Custom (Used with ProfilePath)
  -ProfilePath string
    	Path of custom HTTP GET/POST profile...
  -Sleep string
    	Initial beacon sleep time
  -Stage string
    	Disable host staging (Default: False) (default "false")
  -Syscall string
    	Defines the ability to use direct/indirect system calls instead of the standard Windows API functions calls:
    	[*] None
    	[*] Direct
    	[*] Indirect (default "None")
  -TasksDnsProxyMaxSize string
    	The maximum size (in bytes) of proxy data to transfer via the DNS communication channel at a check in
  -TasksMaxSize string
    	The maximum size (in bytes) of task(s) and proxy data that can be transferred through a communication channel at a check in
  -TasksProxyMaxSize string
    	The maximum size (in bytes) of proxy data to transfer via the communication channel at a check in
  -ThreadSpoof
    	Sets post-ex DLLs to spawn threads with a spoofed start address. These are generated randomly (default true)
  -Uri string
    	The number URIs a profile for beacons to choose from
  -Useragent string
    	UserAgent string for the beacon to use (Leave blank to randomly select one):
    	[*] Win10Chrome
    	[*] Win10Edge
    	[*] Win10IE
    	[*] Win10
    	[*] Win6.3
    	[*] Linux
    	[*] Mac
  -Yaml string
    	Path to the Yaml config file
```

## 02 - Usage

```
$ ./SourcePoint -Host <C2_IP> -Datajitter "<seconds>" -Sleep "<seconds>" -Jitter "<seconds>" && \
-Stage "<true | false>" -Syscall "<None | Direct | Indirect>" && \
-Httplib <wininet | winhttp> -Metadata <base64url | netbios | netbiosu> && \
-Injector <VirtualAllocEx | NtMapViewOfSection> -PostEX_Name <int> && \
-PE_Clone <int> -Keylogger <GetAsyncKeyState | SetWindowsHookEx> && \
-ThreadSpoof -Outfile malleable_c2.profile
```

---
## References

### Helpers

- [[Malleable C2 Profile References]]

- [WhiteKnightLabs: Unleashing the Unseen: Harnessing the Power of Cobalt Strike Profiles for EDR Evasion](https://whiteknightlabs.com/2023/05/23/unleashing-the-unseen-harnessing-the-power-of-cobalt-strike-profiles-for-edr-evasion/)

- [InfoSecWriteups: Red Team Cobalt Strike 4.0 Malleable C2 Profile Guideline](https://infosecwriteups.com/red-team-cobalt-strike-4-0-malleable-c2-profile-guideline-eb3eeb219a7c)

- [Guide to Named Pipes and Hunting for Cobalt Strike Pipes](https://svch0st.medium.com/guide-to-named-pipes-and-hunting-for-cobalt-strike-pipes-dc46b2c5f575)

- [Cobalt Strike Malleable C2 Profile](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2-profile/)

- [The DFIR Report: Cobalt Strike, a Defender's Guide](https://thedfirreport.com/2021/08/29/cobalt-strike-a-defenders-guide/)

- [The DFIR Report: Cobalt Strike, a Defender's Guide - Part 2](https://thedfirreport.com/2022/01/24/cobalt-strike-a-defenders-guide-part-2/)

### Tools

- [Tylous: SourcePoint](https://github.com/Tylous/SourcePoint)