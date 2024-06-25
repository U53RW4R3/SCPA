# 04 - Payload Staging

Search Tag(s): #red-team-infrastructure #cobalt-strike #helpers

## 4.1 - Stage Block

```
stage {
	# Using the peclone will make a nice format for the malleable c2 profile
	# $ ./peclone file.dll

	# Run the dump argument to find
	# $ ./peclone dump file.dll
    set checksum       "123456";                # Find "Checksum:"
    set compile_time   "27 Apr 2019 13:24:28";  # Find "TimeDateStamp" with a placeholder "<DD> <month> <YYYY> HH:MM:SS"
    set entry_point    "32308";                 # Find "AddressOfEntryPoint"
    set image_size_x86 "1798144";               # Find "SizeOfImage"
    set image_size_x64 "1798144";               # Find "SizeOfImage"
    set name           "filename.dll";          # Find "Export.Name" in peclone or a DLL filename

    # Find "Import.0.RVAModuleName.X" in peclone or look for C:\Windows\System32\
	#set module_x86 "wwanmm.dll";
    #set module_x64 "wwanmm.dll";

    set userwx          "false";
    set cleanup         "true";
    set sleep_mask      "true";

	# For stomppe is part of Reflective DLL. To stomp MZ, PE and e_ifanew values 
	# set it to "true" (this is part of obfuscation). If you want to seem like a
	# real DLL that can be injected to memory then set it to "false" without
	# stomping the PE headers.
    set stomppe         "true";
    set obfuscate       "true";
    set smartinject     "true";

	# View the hexdump to take strings in order to mimic the DLL file
	# $ hexdump -C file.dll
	# $ hexdump -ve '"\\\x" 1/1 "%02x"' file.dll
    set rich_header     "\x1d\x67\x43\x53\x59\x06\x2d\x00\x59\x06\x2d\x00\x59\x06\x2d\x00\x3c\x60\x29\x01\x4c\x06\x2d\x00\x3c\x60\x2e\x01\x49\x06\x2d\x00\x>

	# Setting the memory allocator either it's gonna be VirtualAlloc or HeapAlloc
    #set allocator "HeapAlloc";

	# PE (Portable Executable) magic bytes
    set magic_mz_x86 "MZRE";
    set magic_mz_x64 "##A#";
    set magic_pe "##";

	set syscall_method "<None | Direct | Indirect>";

    transform-x86 {
        strrep "ReflectiveLoader" "";                        # Find "Export.Name" (optional)
        strrep "This program cannot be run in DOS mode" "";
        strrep "beacon.dll" "";
        prepend "\x90\x90\x90";
    }

    transform-x64 {
        strrep "ReflectiveLoader" "";                        # Find "Export.Name" (optional)
        strrep "This program cannot be run in DOS mode" "";
        strrep "beacon.x64.dll" "";
        prepend "\x90\x90\x90";
    }

	# Append strings (useful to emulate from a program or adversary's own malware)
	string "BAD BYTES";
	string "{48 FF}";
}
```

---
## References

- [HelpSystems: PE and Memory Indicators](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2-extend_pe-memory-indicators.htm)