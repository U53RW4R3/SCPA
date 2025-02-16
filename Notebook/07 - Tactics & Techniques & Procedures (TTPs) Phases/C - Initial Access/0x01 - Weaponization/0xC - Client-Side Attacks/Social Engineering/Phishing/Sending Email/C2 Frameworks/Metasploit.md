# Metasploit

```
msf > use auxiliary/client/smtp/emailer

msf auxiliary(client/smtp/emailer) > options

Module options (auxiliary/client/smtp/emailer):

   Name         Current Setting                                           Required  Description
   ----         ---------------                                           --------  -----------
   DATE                                                                   no        Override the DATE: field with this value
   DOMAIN                                                                 no        SMTP Domain to EHLO to
   MAILFROM     random@example.com                                        yes       The FROM address of the e-mail
   PASSWORD                                                               no        SMTP Password for sending email
   RHOST        127.0.0.1                                                 yes       SMTP server address
   RHOSTS       127.0.0.1                                                 yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT        25                                                        yes       SMTP server port (TCP)
   USERNAME                                                               no        SMTP Username for sending email
   VERBOSE                                                                no        Display verbose information
   YAML_CONFIG  /usr/share/metasploit-framework/data/emailer_config.yaml  yes       Full path to YAML Configuration file

msf auxiliary(client/smtp/emailer) > set rhost <attacker_mailserver_IP>

msf auxiliary(client/smtp/emailer) > set rhosts <target_mailserver_IP>

msf auxiliary(client/smtp/emailer) > set mailfrom no-reply@attacker.com

msf auxiliary(client/smtp/emailer) > set yaml_config /path/to/emailer_config.yaml

msf auxiliary(client/smtp/emailer) > run
```