# Interactive Shell

Search Tag(s): #empire #command-and-control #interactive-shell #help-menu

## 01 - Help Menu

```
(Empire: agents) > interact <AGENT_NAME>
(Empire: AGENT_NAME) > help

┌Help Options────┬─────────────────────────────────────┬───────────────────────────────┐
│ Name           │ Description                         │ Usage                         │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ display        │ Display an agent property           │ display <property_name>       │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ download       │ Tasks an the specified agent to     │ download <file_name>          │
│                │ download a file.                    │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ help           │ Display the help menu for the       │ help                          │
│                │ current menu                        │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ history        │ Display last number of task results │ history [<number_tasks>]      │
│                │ received.                           │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ info           │ Display agent info.                 │ info                          │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ killdate       │ Set an agent's killdate             │ killdate <kill_date>          │
│                │ (01/01/2020)                        │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ proxy          │ Proxy management menu for           │ proxy                         │
│                │ configuring agent proxies           │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ script_command │ "Execute a function in the          │ shell_command <script_cmd>    │
│                │ currently imported PowerShell       │                               │
│                │ script."                            │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ script_import  │ Uploads a PowerShell script to the  │ script_import                 │
│                │ server and runs it in memory on the │ <local_script_location>       │
│                │ agent. Use '-p' for a file          │                               │
│                │ selection dialog.                   │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ shell          │ Tasks an the specified agent to     │ shell <shell_cmd>             │
│                │ execute a shell command.            │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ sleep          │ Tasks an the specified agent to     │ sleep <delay> <jitter>        │
│                │ update delay (s) and jitter (0.0 -  │                               │
│                │ 1.0)                                │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ update_comms   │ Update the listener for an agent.   │ update_comms <listener_name>  │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ upload         │ Tasks an the specified agent to     │ upload <local_file_directory> │
│                │ upload a file. Use '-p' for a file  │                               │
│                │ selection dialog.                   │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ view           │ View specific task and result       │ view <task_id>                │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ vnc            │ Launch a VNC server on the agent    │ vnc                           │
│                │ and spawn a VNC client              │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ vnc_client     │ Launch a VNC client to a remote     │ vnc_client <address> <port>   │
│                │ server                              │ <password>                    │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ workinghours   │ Set an agent's working hours        │ workinghours <working_hours>  │
│                │ (9:00-17:00)                        │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ whoami         │ Tasks an agent to run the shell     │ whoami                        │
│                │ command 'whoami'                    │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ ps             │ Tasks an agent to run the shell     │ ps                            │
│                │ command 'ps'                        │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ sc             │ Tasks the agent to run module       │ sc                            │
│                │ powershell/collection/screenshot.   │                               │
│                │ Default parameters include: Ratio:  │                               │
│                │ 80                                  │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ keylog         │ Tasks the agent to run module       │ keylog                        │
│                │ powershell/collection/keylogger.    │                               │
│                │ Default parameters include: Sleep:  │                               │
│                │ 1                                   │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ sherlock       │ Tasks the agent to run module       │ sherlock                      │
│                │ powershell/privesc/sherlock.        │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ mimikatz       │ Tasks the agent to run module power │ mimikatz                      │
│                │ shell/credentials/mimikatz/logonpas │                               │
│                │ swords.                             │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ psinject       │ Tasks the agent to run module       │ psinject <Listener> <ProcId>  │
│                │ powershell/management/psinject.     │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ revtoself      │ Tasks the agent to run module       │ revtoself                     │
│                │ powershell/credentials/tokens.      │                               │
│                │ Default parameters include:         │                               │
│                │ RevToSelf: True                     │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ shinject       │ Tasks the agent to run module       │ shinject <Listener> <ProcId>  │
│                │ powershell/management/shinject.     │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ spawn          │ Tasks the agent to run module       │ spawn <Listener>              │
│                │ powershell/management/spawn.        │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ steal_token    │ Tasks the agent to run module       │ steal_token <ProcessID>       │
│                │ powershell/credentials/tokens.      │                               │
│                │ Default parameters include:         │                               │
│                │ ImpersonateUser: True               │                               │
├────────────────┼─────────────────────────────────────┼───────────────────────────────┤
│ bypassuac      │ Tasks the agent to run module power │ bypassuac <Listener>          │
│                │ shell/privesc/bypassuac_eventvwr.   │                               │
└────────────────┴─────────────────────────────────────┴───────────────────────────────┘

(Empire: AGENT_NAME) >
```

## 02 - Usage

```
(Empire: AGENT_NAME) > ipconfig

(Empire: AGENT_NAME) > powershell_situational_awareness_network_arpscan
```

### Execute Shell Commands

```
(Empire: AGENT_NAME) > shell <commands>
```

---
## References

### SecurityNik

- [SecurityNik: Beginning Powershell Empire Attack](https://www.securitynik.com/2022/02/beginning-powershell-empire-attack-in.html)

### HackMag

- [HackMag: Powershell Empire Modules](https://hackmag.com/security/powershell-empire/)

### Hacking Articles

- [Hacking Articles: Empire For Pentester Active Directory Enumeration](https://www.hackingarticles.in/empire-for-pentester-active-directory-enumeration/)

- [Hacking Articles: Powershell Empire For Pentester Mimikatz Module](https://www.hackingarticles.in/powershell-empire-for-pentester-mimikatz-module/)

- [Hacking Articles: OSX Exploitation with Powershell Empire](https://www.hackingarticles.in/osx-exploitation-with-powershell-empire/)

- [Hacking Articles: Hacking with Empire Powershell Post Exploitation Agent](https://www.hackingarticles.in/hacking-with-empire-powershell-post-exploitation-agent/)

- [Hacking Articles: Data Exfiltration Using Powershell Empire](https://www.hackingarticles.in/data-exfiltration-using-powershell-empire/)

### HoldMyBeer

- [HoldMyBeer: Part 2 Intro to Threat Hunting Understanding the Attacker Mindset with Powershell Empire and the Mandiant Attack Lifecycle](https://holdmybeersecurity.com/2020/01/23/part-2-intro-to-threat-hunting-understanding-the-attacker-mindset-with-powershell-empire-and-the-mandiant-attack-lifecycle/)

### SnapLabs

- [SnapLabs: Command and Control with Powershell Empire part 1](https://www.snaplabs.io/insights/command-and-control-with-powershell-empire-pt1)

- [SnapLabs: Command and Control with Powershell Empire part 2](https://www.snaplabs.io/insights/command-and-control-with-powershell-empire-pt2)

- [SnapLabs: Command and Control with Powershell Empire part 3](https://www.snaplabs.io/insights/command-and-control-with-powershell-empire-pt3)

- [SnapLabs: Lateral Movement Methods and Good Practices](https://www.snaplabs.io/insights/lateral-movement-methods-and-good-practices)

### Infosec Matters

- [Empire Module Library](https://www.infosecmatter.com/empire-module-library/)