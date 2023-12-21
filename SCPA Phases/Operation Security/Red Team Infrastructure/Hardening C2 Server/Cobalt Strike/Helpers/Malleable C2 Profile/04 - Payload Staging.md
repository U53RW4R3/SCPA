# 04 - Payload Staging

Search Tag(s): #red-team-infrastructure #cobalt-strike #helpers

## 4.1 - Stage Block

```
stage {

	# Using the peclone will make a nice format for the malleable c2 profile
	# $ ./peclone file.dll

	# $ ./peclone dump file.dll
    set checksum       "123456";
    set compile_time   "27 Apr 2019 13:24:28";
    set entry_point    "32308";
    set image_size_x86 "1798144";
    set image_size_x64 "1798144";
    set name           "Dll6.dll";

    set userwx          "false";
    set cleanup         "true";
    set sleep_mask      "true";
    set stomppe         "true";
    set obfuscate       "true";

	# $ hexdump -C file.dll
	# $ hexdump -v -e '"\\\x" 1/1 "%02x"' file.dll
    set rich_header     "\x1d\x67\x43\x53\x59\x06\x2d\x00\x59\x06\x2d\x00\x59\x06\x2d\x00\x3c\x60\x29\x01\x4c\x06\x2d\x00\x3c\x60\x2e\x01\x49\x06\x2d\x00\x>

    #set allocator "HeapAlloc";
    set magic_mz_x86 "MZRE";
    set magic_mz_x64 "##A#";
    set magic_pe "##";

    set sleep_mask "true";

    set smartinject "true";

	set syscall_method "<None | Direct | Indirect>";

    #set module_x86 "wwanmm.dll";
    #set module_x64 "wwanmm.dll";

    transform-x86 {
        prepend "\x90\x90\x90";
        strrep "ReflectiveLoader" "";
        strrep "beacon.dll" "";
        }

    transform-x64 {
        prepend "\x90\x90\x90";
        strrep "ReflectiveLoader" "";
        strrep "beacon.x64.dll" "";
        }

	string "BAD BYTES";
	string "{48 FF}";
}
```

---
## References

- [HelpSystems: PE and Memory Indicators](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2-extend_pe-memory-indicators.htm)