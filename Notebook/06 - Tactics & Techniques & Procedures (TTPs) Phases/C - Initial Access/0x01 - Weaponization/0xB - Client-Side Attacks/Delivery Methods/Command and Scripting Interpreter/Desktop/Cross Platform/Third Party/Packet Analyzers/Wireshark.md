---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - cross-platform
credits:
  - aalphass
---
# Wireshark

Personal Lua Plugins where all the `.lua` scripts will be executed or loaded when **Wireshark** is executed.

```
C:\Users\%USERNAME%\AppData\Roaming\Wireshark\plugins\
$HOME/.local/lib/wireshark/plugins/
```

**Personal Plugins** where all the binary plugins will be executed or loaded when **Wireshark** is executed.

```
C:\Users\%USERNAME%\AppData\Roaming\Wireshark\plugins\4.0\
$HOME/.local/lib/wireshark/plugins/3.6/
```

Wireshark CLI program.

```
> tshark -Xlua_script:payload.lua
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Cross Platform/Code Execution/Lua/Manual]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/One-Liners/Reverse Shells/Lua]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/File Attachment/Payloads/Desktop/Windows/One-Liners/Reverse Shells/Lua]]

### aalphaas

- [aalphaas:  Reverse Shell using Wireshark - Unleashing Wireshark's Offensive Hidden Powers ](https://www.youtube.com/watch?v=iMgIp3DVFTA)