# Field Codes

https://support.microsoft.com/en-us/office/list-of-field-codes-in-word-1ad6d91a-55a7-4a8d-b535-cf7888659a51

```
$ nano document.xml
..[omitted]..
  <w:fldChar w:fldCharType="begin" w:dirty="true"/>
```

## DocVariable

https://support.microsoft.com/en-us/office/field-codes-docvariable-field-32a81e22-c5c1-4b16-8097-f0de851db67c

```
{ DOCVARIABLE "<document_name>" }
```

## Quote

https://support.microsoft.com/en-us/office/field-codes-quote-field-26f0d723-07a8-4076-9097-a71459f3d44c

```
{ QUOTE { IF { DATE \@ "M" } = 1 "12" "{= { DATE \@ "M" } -1 }/1/03" \@ "MMMM"} }
```

```
{ QUOTE 65 }
```

## Set

https://support.microsoft.com/en-us/office/field-codes-set-field-1fdfbcf9-4d7b-41e2-a1cb-4384a1f516e6

```
{SET c "{QUOTE 65 65 65 65}"}
{SET d "{QUOTE 71 71 71 71}"}
{DDE {REF c} {REF d}}
```

This effectively becomes:

```
{DDE "AAAA" "GGGG"}
```

## Symbol

https://support.microsoft.com/en-us/office/field-codes-symbol-field-3f4fbf16-e592-4c27-92e0-676b1c5dd50e

```
{ SYMBOL 163 }

{ SYMBOL 0xA }
```

### Font Name

```
{ SYMBOL 211 \f "<font_name>" \s <font_size> }
```

This will print the copyright (©) symbol.

```
{ SYMBOL 211 \f "Symbol" \s 12 }
```

```
{ SYMBOL 0xA \h }

{ SYMBOL 0xA \u }
```

## Arithmetic Expressions

### Eq

https://support.microsoft.com/en-us/office/field-codes-eq-equation-field-27300091-3780-4b88-836f-ae49ecde4692

```

```

### Formula

https://support.microsoft.com/en-us/office/field-codes-formula-field-32d5c9de-3516-4ec3-80ed-d1fc2b5bc21d

```

```

## Files

### FileName

https://support.microsoft.com/en-us/office/field-codes-filename-field-a2946f1b-d822-47dc-ba32-4482aece26bc

Print the path of the filename.

```
{ FILE NAME \p }

Filename Path: { FILE NAME \p }
```

### Referenced Document

https://support.microsoft.com/en-us/office/field-codes-rd-referenced-document-field-1730f463-ea41-4736-8061-499e778dd806

Specify a path of the binary.

```
{ TOC }
{ RD C:\\Manual\\Chapters\\Chapter1.doc }
{ RD C:\\Manual\\Chapters\\Chapter2.doc }
{ RD C:\\Manual\\Chapters\\Chapter3.doc }
```

## Ref

https://support.microsoft.com/en-us/office/field-codes-ref-field-b2531c23-05d6-4e3b-b54f-aee24447ceb2

```

```

## IncludeText

https://support.microsoft.com/en-us/office/field-codes-includetext-field-1c34d6d6-0de3-4b5c-916a-2ff950fb629e

Specify a path of the binary.

```
{ INCLUDETEXT "C:\\path\\to\\binary.exe" }
```

## IncludePicture

https://support.microsoft.com/en-us/office/field-codes-includepicture-field-a3aac6dc-4e08-4d62-9aac-794279d02de9

Specify a path of the binary.

```

```

## Document Properties

### Author

```
{ AUTHOR "<author_name>" }
```

Print the author's name.

```
{ AUTHOR }
```

### Title

Set a new title name.

```
{ TITLE "<new_title>" }
```

Print the title name.

```
{ TITLE }
```

This will print the title name. Use this to include a program to execute.

```
{ INCLUDE { DOCPROPERTY "Title" } }
```

### Subject

Set a new subject name.

```
{ SUBJECT "<subject_name>" }
```

Print the subject's name.

```
{ AUTHOR }
```

### Tags

> [!TIP]
> Tags can be used to pass arguments.

```
{INCLUDE { DOCPROPERTY "Tags" }}
```

### Comments

```
{INCLUDE { DOCPROPERTY "Comments" }}
```

### Keywords

> [!INFO]
> The characters limit is 255 maximum for the `KEYWORDS` field code.
> > [!TIP]
> > You can specify a binary path.

Set the keywords. 

```
{ KEYWORDS "<keywords>" }
```

Print the keywords.

```
{ KEYWORDS }
```

### UserName

Specify the username.

```
{ USERNAME "<new_username>" }
```

Print the username.

```
{ USERNAME }
```

### UserAddress

Set the user's address.

```
{ USERADDRESS "<new_address>" }
```

Print the user's address.

```
{ USERADDRESS }
```

### InfoType

```
{[INFO] InfoType ["<value>"]}
```

```
{[INFO] Author ["<author_name>"]}
```

## Hyperlink

https://support.microsoft.com/en-us/office/field-codes-hyperlink-field-864f8577-eb2a-4e55-8c90-40631748ef53

```

```

## If Statements

### If

https://support.microsoft.com/en-us/office/field-codes-if-field-9f79e82f-e53b-4ff5-9d2c-ae3b22b7eb5e

```

```

### Next

https://support.microsoft.com/en-us/office/field-codes-next-field-3862fad6-0297-411a-a4e7-6ff5bcf178fd

```

```

### NextIf

https://support.microsoft.com/en-us/office/field-codes-nextif-field-5dd7bd9c-29b1-4ef2-aba8-4f0387e8b417

```

```

### SkipIf

https://support.microsoft.com/en-us/office/field-codes-skipif-field-d3ff3970-31f3-43a3-be7f-f5fa1704a512

```

```

### Compare

https://support.microsoft.com/en-us/office/field-codes-compare-field-60bfb300-c58d-4f2f-8255-f1a9707390c8

```
{ COMPARE <expression_1> <operator> <expression_2> }
```

## Document View

### NumChars

https://support.microsoft.com/en-us/office/field-codes-numchars-field-7847c34c-e4f9-4637-9f72-e7c34317b393

Retrieves total number of characters in the document.

```
{ NUMCHARS }
```

### Page

Prints the current page number.

```
{ PAGE }
```

### NumPages

Retrieves total number of pages in the document.

```
{ NUMPAGES }
```

### NumWords

Retrieves total number of words in the document.

```
{ NUMWORDS }
```

---
## References

### Staaldraad

- [Staaldraad: MSWord - Obfuscation with Field Codes](https://staaldraad.github.io/2017/10/23/msword-field-codes/)