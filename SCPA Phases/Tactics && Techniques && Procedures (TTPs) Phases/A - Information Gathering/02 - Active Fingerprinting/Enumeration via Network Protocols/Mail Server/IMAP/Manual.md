# Manual

## 01 - Banner Grab

`$ nc -nv <IP> 143`

`$ openssl s_client -connect <IP>:993 -quiet`

## 02 - Information Disclosure

```
$ telnet <IP> 143
* OK The Microsoft Exchange IMAP4 service is ready.
>> a1 AUTHENTICATE NTLM
+
>> TlRMTVNTUAABAAAAB4IIAAAAAAAAAAAAAAAAAAAAAAA=
+ TlRMTVNTUAACAAAACgAKADgAAAAFgooCBqqVKFrKPCMAAAAAAAAAAEgASABCAAAABgOAJQAAAA9JAEkAUwAwADEAAgAKAEkASQBTADAAMQABAAoASQBJAFMAMAAxAAQACgBJAEkAUwAwADEAAwAKAEkASQBTADAAMQAHAAgAHwMI0VPy1QEAAAAA
```

## 03 cURL

### 3.1 - Listing Mailboxes

- Listing mailboxes with an imap command `LIST "" "*"`.

`$ curl -k 'imaps://<IP>/' --user <username>:<password>`

### 3.2 - Listing Messages in Inboxes

- Listing messages in a Inbox (imap command `SELECT INBOX` and then `SEARCH ALL`).

`$ curl -k 'imaps://<IP>/INBOX?ALL' --user <username>:<password>`

### 3.3 - Credentials

- Searching keywords related to sensitive credentials in the `Drafts` or other `Mailboxes`.

`$ curl -k 'imaps://<IP>/Drafts?TEXT password' --user <username>:<password>`

### 3.4 - Download Messages

#### 3.4.1 - Drafts

- Downloading a message (imap command `SELECT Drafts` and then `FETCH 1 BODY[]`).

`$ curl -k 'imaps://<IP>/Drafts;MAILINDEX=1' --user <username>:<password>`

##### 3.4.1.1 - SQL Format Like

- We can use the `UID` (unique id) to obtain the messages, yet this one needed to be manually formatted like a SQL Query

`$ curl -k 'imaps://<IP>/INBOX' -X 'UID SEARCH ALL' --user <username>:<password>`

`$ curl -k 'imaps://<IP>/INBOX;UID=1' --user <username>:<password>`

##### 3.4.1.2 -  Automated

- Another method that can work is by sending parts of messages like subject and sender for the first 5 messages

`$ curl -k 'imaps://<IP>/INBOX' -X 'FETCH 1:5 BODY[HEADER.FIELDS (SUBJECT FROM)]' --user <username>:<password> -v 2>&1 | grep '^<'`

`$ cat imap-retrieve-messages.sh`

---

```bash
#!/bin/sh  
for m in {1..5}; do  
    echo $m  
    curl "imap://$1/INBOX;MAILINDEX=$m;SECTION=HEADER.FIELDS%20(SUBJECT%20FROM)" --user $2:$3  
done
```

`$ ./imap-retrieve-messages.sh <IP> <username> <password>`

---
## References

- [Hacktricks: Pentesting IMAP](https://book.hacktricks.xyz/pentesting/pentesting-imap)