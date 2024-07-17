# TCPDump

Search Tag(s): #sniffing-and-spoofing #packet-analyzer

## Usage

- Sniff packets from a specific network interface

`$ sudo tcpdump -i <interface>`

- Capture number of packets

`$ sudo tcpdump -c <int> -i <interface>`

- Display captured packets in ASCII

`$ sudo tcpdump -A -i <interface>`

- Display captured packets in HEX and ASCII

`$ sudo tcpdump -XX -i <interface>`

- Save packets in a file

`$ sudo tcpdump -w file.pcap -i <interface>`

- Read captured packets file

`$ sudo tcpdump -r file.pcap`

- Sniff packets with a specific network protocol

`$ sudo tcpdump -i <interface> <tcp | udp | icmp | icmp6>`

- Sniff packets from source IP

`$ sudo tcpdump -i <interface> src <IP>`

- Sniff packets from destination IP

`$ sudo tcpdump -i <interface> dst <IP>`

## Use Cases

TODO: Provide use cases