# Manual

## 01 - SendEmail

Syntax usage of the program.

```
$ sendemail -t <reciever_email_address> -f <sender_email_address> -s <smtp_relay_server_IP>:<PORT> -u "<Subject>" -a file.txt
If you are manually typing in a message:
  - First line must be received within 60 seconds.
  - End manual input with a CTRL-D on its own line.
If you are manually typing in a message:
  - First line must be received within 60 seconds.
  - End manual input with a CTRL-D on its own line.

A body paragraph that is written line by line
until you press CTRL-D to end the input
```

Here's an example just to show you how it works.

```
$ sendemail -t itdept@victim.com -f techsupport@bestcomputers.com -s 192.168.8.131 -u Important Upgrade Instructions -a /tmp/BestComputers-UpgradeInstructions.pdf
Reading message body from STDIN because the '-m' option was not used.
If you are manually typing in a message:
  - First line must be received within 60 seconds.
  - End manual input with a CTRL-D on its own line.

IT Dept,

We are sending this important file to all our customers. It contains very important instructions for upgrading and securing your software. Please read and let us know if you have any problems.

Sincerely,

$ swaks --to $(cat emails | tr '\n', ',' | less) --from test@website.com --header "Subject: test" --body "Please click the link <attacker_URL>" --server <mail_server>
```

## 02 - Swaks

```
$ swaks --to <reciever_email_address> --from <sender_email_address> --header "Subject: test" --body "<body_paragraph>" --server <mail_server>
```