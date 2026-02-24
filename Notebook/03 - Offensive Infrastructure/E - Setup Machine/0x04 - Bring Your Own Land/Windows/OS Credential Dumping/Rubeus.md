---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - bring-your-own-land
  - os-credential-dumping
  - rubeus
---
# Rubeus

## 01 - Compile

Install a targeting pack from this [link](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481). Then compile `Rubeus`.

```
C:\> git clone https://github.com/GhostPack/Rubeus.git
cd Rubeus
dotnet build -c Release -p:TargetFrameworkVersion=v4.8.1
```