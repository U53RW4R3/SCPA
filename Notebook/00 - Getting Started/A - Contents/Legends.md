# Legends

## Parameters

| Parameter | Description                               | Examples                           |
| --------- | ----------------------------------------- | ---------------------------------- |
| `<>`      | Required parameters                       | `<IP>`, `<username>`, `<password>` |
| `[]`      | Optional contextual paramaters            | `[/flag-option]`, `[args]`         |
| `[<>]`    | Optionally contextual required parameters | `[<bind_IP>]`, `[<PORT>]`          |
| `()`      | Grouped parameter                         |                                    |

## Terminal Prompts

| Prompts                | Operating System | Description                                                | Examples                                 |
| ---------------------- | ---------------- | ---------------------------------------------------------- | ---------------------------------------- |
| `>`                    | Cross Platform   | Universal terminal prompt.                                 | `> <command>`                            |
| `$`                    | Unix-like        | Non-elevated user privileges (`$`) Unix-like shell prompt. | `user@hostname:~$ <command>`<br>         |
| `#`                    | Unix-like        | Elevated user privileges (`#`) Unix-like shell prompt.     | `root@hostname:~# <command>`<br>         |
| `PS />`                | Unix-like        | PowerShell Unix-like console prompt.<br><br>               | `PS /home/USERNAME> <command \| cmdlet>` |
| `PS <drive_letter>:\>` | Windows          | Powershell console prompt <br><br>                         | `PS C:\> <command \| cmdlet>`            |
| `<drive_letter>:\>`    | Windows          | Windows command prompt.                                    | `C:\> <command>`                         |
