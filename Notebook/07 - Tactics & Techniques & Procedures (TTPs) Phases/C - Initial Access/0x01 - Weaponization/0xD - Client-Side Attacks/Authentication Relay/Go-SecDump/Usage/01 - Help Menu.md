# 01 - Help Menu

```
$ go-secdump -h

    Usage: go-secdump [options]

    options:
          --host <target>       Hostname or ip address of remote server. Must be hostname when using Kerberos
      -P, --port <port>         SMB Port (default 445)
      -d, --domain <domain>     Domain name to use for login
      -u, --user <username>     Username
      -p, --pass <pass>         Password
      -n, --no-pass             Disable password prompt and send no credentials
          --hash <NT Hash>      Hex encoded NT Hash for user password
          --local               Authenticate as a local user instead of domain user
      -k, --kerberos            Use Kerberos authentication. (KRB5CCNAME will be checked on Linux)
          --dc-ip               Optionally specify ip of KDC when using Kerberos authentication
          --target-ip           Optionally specify ip of target when using Kerberos authentication
          --aes-key             Use a hex encoded AES128/256 key for Kerberos authentication
          --dump                Saves the SAM and SECURITY hives to disk and
                                transfers them to the local machine.
          --sam                 Extract secrets from the SAM hive explicitly. Only other explicit targets are included.
          --lsa                 Extract LSA secrets explicitly. Only other explicit targets are included.
          --dcc2                Extract DCC2 caches explicitly. Only ohter explicit targets are included.
          --backup-dacl         Save original DACLs to disk before modification
          --restore-dacl        Restore DACLs using disk backup. Could be useful if automated restore fails.
          --backup-file         Filename for DACL backup (default dacl.backup)
          --relay               Start an SMB listener that will relay incoming
                                NTLM authentications to the remote server and
                                use that connection. NOTE that this forces SMB 2.1
                                without encryption.
          --relay-port <port>   Listening port for relay (default 445)
          --socks-host <target> Establish connection via a SOCKS5 proxy server
          --socks-port <port>   SOCKS5 proxy port (default 1080)
      -t, --timeout             Dial timeout in seconds (default 5)
          --noenc               Disable smb encryption
          --smb2                Force smb 2.1
          --debug               Enable debug logging
          --verbose             Enable verbose logging
      -o, --output              Filename for writing results (default is stdout). Will append to file if it exists.
      -v, --version             Show version
```