# Setup Malleable C2 Profile

Search Tag: #red-team-infrastructure #cobalt-strike

## 01 - Generate TLS Keystore

^24b8cf

- Modify in `teamserver` bash script.

```
keytool -keystore ./cobaltstrike.store -storepass <password> -keypass <password> -genkey -keyalg RSA -alias <alias_name> -dname "CN=www.website.com, OU=Company Inc., O=Company Name, L=San Francisco, S=California, C=US"

./TeamServerImage -Dcobaltstrike.server_port=50050 -Dcobaltstrike.server_bindto=0.0.0.0 -Djavax.net.ssl.keyStore=./cobalts
trike.store -Djavax.net.ssl.keyStorePassword=<password> teamserver $*
```

## 02 - Malleable C2 Profile

### 2.1 - Basics

#### 2.1.1 - Global Options

##### 2.1.1.1 - Auxiliary Settings

```
# Name of the C2 profile
set sample_name "<profile_name>";

# User Agent
set useragent "<user_agent>";

# Staging payloads (part of metasploit shellcode compatibility).
# Disabling it loses the ability to generate staging payloads.
set host_stage "<true | false>";

# Each pound (#) is replaced with a random hex value.

# Default name of pipe to use SMB Beacon's P2P communication.
set pipename "<namepipe>_##";

# Using staging payload for SMB Beacon's P2P communication.
set pipename_stager "<namepipe>_##";

# SSH client banner
set ssh_banner "OpenSSH 9.5";

# Pipe name for ssh sessions.
set ssh_pipename "<namepipe>_ssh_####";

# Sleep and Jitter (uses seconds).
set sleeptime "15";
set jitter    "30"; # Default jitter factor (0 - 99%)
```

#### 2.1.2 - Code Signing Certificate

- Refer to [[Setup Malleable C2 Profile#^24b8cf|generate TLS keystore]].

```
code-signer {
    set keystore "keystore.jks"; 
    set password "<password>";
    set alias    "<alias>";
    set timestamp "false";
    set timestamp "http://timestamp.digicert.com";
}
```

#### HTTP Block

##### HTTP Certificate

```
https-certificate {
	set C    "US"
	set CN   "www.website.com";
	set L    "San Francisco";
	set O    "Company Name";
	set OU   "Company Inc.";
	set ST   "California";
	set validity "365";
}
```

##### HTTP Config

- Just to take care of the default HTTP settings.

```
http-config {
	# Set Header names and values to make it seem like a webserver
     set headers "Date, Server, Content-Length, Keep-Alive, 
                    Connection, Content-Type";
     header "Server" "Apache";
     header "Content-Length" "";
     header "Keep-Alive" "timeout=5, max=100";
     header "Connection" "Keep-Alive”;
     
     header "Content-Type" "";
     set trust_x_forwarded_for "true";
     
     # Block specific User Agents
     set block_useragents "curl*,lynx*,wget*";
}
```

##### HTTP Staging (Metasploit compatible payloads)

TODO: Finish the rest of the HTTP code block and provide steps to append NOPs or byte encoded image file via `hexdump`.

```
http-stager {
     set uri_x86 "/filename_32.<gif | jpg | png | jpeg | woff | woff2 | tiff>"; 
     set uri_x64 "/filename_64.<gif | jpg | png | jpeg | woff | woff2 | tiff>";
     
     client {
	     parameter "id" "1234";
	     header "Cookie" "SomeValue";
	     
	 server {
	     header "Content-Type" "image/<gif | jpg | png | jpeg | woff | woff2 | tiff>"; 
	     output {
	          prepend "GIF89a"; 
	          print;
	     }
	}
}
```

##### HTTP GET Request Block

```
# Optionally you can add more http blocks by inserting variant names
# you can clearly see once you add a HTTP(S) listener
# http-get <variant_name> {

http-get {
	set verb "GET";
	set uri "";
}
```

##### HTTP POST Request Block

```
# Optionally you can add more http blocks by inserting variant names
# you can clearly see once you add a HTTP(S) listener
# http-post <variant_name> {

http-post {
	set verb "POST";
	set uri "";
}
```

##### HTTP Beacons

```
http-beacon {
    set library "winhttp";
}

http-beacon "wininet-beacon-variant" {
    set library "wininet";
}
```

#### DNS Block

```

```

### Post Exploitation Block (Evasion)

```
post-ex {
	# Spawn the beacons to default windows EXE binaries.
	set spawnto_x64 "%windir%\\sysnative\\dllhost.exe";
	set spawnto_x86 "%windir%\\syswow64\\dllhost.exe";
	
	# Obfuscate beacon strings
	set obfuscate "true";

	# smartinject
	set smartinject "true";
	
	# Disable AMSI feature. To enable it set it to "false"
    set amsi_disable "false";

	# Set a specific windows function for recording keystrokes
	set keylogger "GetAsyncKeyState";
}
```

---
## References

### HelpSystem Manual User Guide

- [HelpSystems User Guide](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/welcome_main.htm)

### Cobalt Strike Malleable C2 Profile

- [HelpSystems: Profile Language](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_profile-language.htm)

- [HelpSystems: Self-signed SSL Certificates with SSL Beacon](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_self-signed-ssl-certificates.htm)

- [HelpSystems: HTTP Server Configuration](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_http-server-config.htm)

- [HelpSystems: HTTP Beacons](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_http-beacons.htm)

- [HelpSystems: Malleable C2 DNS Beacons](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_dns-beacons.htm)

- [HelpSystems: Profile Variants](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_profile-variants.htm)

- [WhiteKnightLabs: Unleashing the Unseen: Harnessing the Power of Cobalt Strike Profiles for EDR Evasion](https://whiteknightlabs.com/2023/05/23/unleashing-the-unseen-harnessing-the-power-of-cobalt-strike-profiles-for-edr-evasion/)

- [Red Team Cobalt Strike 4.0 Malleable C2 Profile Guideline](https://infosecwriteups.com/red-team-cobalt-strike-4-0-malleable-c2-profile-guideline-eb3eeb219a7c)

- [Guide to Named Pipes and Hunting for Cobalt Strike Pipes](https://svch0st.medium.com/guide-to-named-pipes-and-hunting-for-cobalt-strike-pipes-dc46b2c5f575)

- [Cobalt Strike Malleable C2 Profile](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2-profile/)

- [Help Malleable C2](https://download.cobaltstrike.com/help-malleable-c2)

- [RedTeaming CheatSheet: Cobalt Strike](https://github.com/0xJs/RedTeaming_CheatSheet/blob/main/cobalt-strike.md)

- [A Red Teamer Plays with JARM](https://www.cobaltstrike.com/blog/a-red-teamer-plays-with-jarm/)

- [Red-Team-Infrastructure-Wiki](https://github.com/bluscreenofjeff/Red-Team-Infrastructure-Wiki)