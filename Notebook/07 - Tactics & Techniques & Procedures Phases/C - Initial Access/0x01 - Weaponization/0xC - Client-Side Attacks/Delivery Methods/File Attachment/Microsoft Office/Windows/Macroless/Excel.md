# Excel

## 01 - CSV

TODO: Fill this info

## 02 - SLK

## 03 - XLL

```cpp
#include <windows.h>

// Excel will call this on Add-in load
extern "C" __declspec(dllexport) int WINAPI xlAutoOpen(void) {
    // add payload here

    return 1;            // Return success to Excel
}
```

Compile the payload as a `.xll` file.

```
$ x86_64-w64-mingw32-g++ -std=c++11 payload.cpp -o payload.xll -shared -static-libgcc -static-libstdc++ -s
```

---
## References

### Source Repositories

- [XLL Phishing](https://github.com/Octoberfest7/XLL_Phishing)

- [Xyrella](https://github.com/zimnyaa/xyrella)

### Red Team Notes

- [Red Team Notes: .SLK Excel](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/phishing-.slk-excel)

- [Red Team Notes: XLM / Macro 4.0](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/phishing-xlm-macro-4.0)

### RedSiege

- [RedSiege: EXCELntDonut](https://github.com/RedSiege/EXCELntDonut)

### FortyNorth

- [FortyNorth: XLM (Excel 4.0) Macro Generator for Phishing Campaigns](https://fortynorthsecurity.com/blog/excelntdonut/)

### XPNSec

- [XPNSec: From CSV to Meterpreter](https://blog.xpnsec.com/from-csv-to-meterpreter/)

### Bank Security

- [Bank Security: MS Excel Weaponization Techniques](https://bank-security.medium.com/ms-excel-weaponization-techniques-79ac51610bf5)

### WithSecure

- [WithSecure: Add-In Opportunities for Office Persistence](https://labs.withsecure.com/publications/add-in-opportunities-for-office-persistence/)