---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - offensive-tools
  - privilege-escalation
  - moriarty
---
# Moriarty

Install a targeting pack from this [link](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481). Then compile `moriarty`.

```
C:\> git clone https://github.com/BC-SECURITY/Moriarty.git

C:\> cd Moriarty\Moriarty

C:\Moriarty\Moriarty> dotnet build -c Release -p:TargetFrameworkVersion=v4.8.1
```