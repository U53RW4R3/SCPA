# 04 - Spawn Interactive Shell and Persistence

Search Tag(s): #command-injection #initial-foothold #persistence #webshell #dvwa

## Webshell

### Conditions

- Find writable directories in the web root directory the drop a [[Tactics && Techniques && Procedures (TTPs) Phases/Initial Access/Callback Shells/Webshells/Webshells|webshell]].

`; find /var/www/html/dvwa -writable -type d 2>/dev/null`