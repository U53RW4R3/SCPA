# 08 - Extract Metadata

TODO: Fill this info

Metadata can be used to gather against either an organization's resources of what software their operating, scrape sensitive data to craft usernames from individuals that are working in the organization.

## CeWL

```
$ cewl -u "<user_agent>" -d <int> -na --meta_file meta-file-output.txt <URL>

$ cewl -u "<user_agent>" -d <int> -na --meta-temp-dir /path/to/directory <URL>
```

## Metagoofil

```
$ metagoofil -u "<user_agent>" -d <domain.com> -t pdf,doc,docx,docm,xls,xlsx,xlsm,csv,ppt,pptx,pptm -l 1000 -w -o output_files
```

## Exiftool

`$ exiftool file`

---
## References

- [Exiftool](https://exiftool.org/)

- [[OSINT Framework]]

- [[Tactics && Techniques && Procedures (TTPs) Phases/Initial Access/Password Cracking/Online/Generate Custom Wordlist/CeWL|CeWL]]

- [How Metadata Can Reveal Sensitive Information During Pentesting.](https://medium.com/@kanhaiyapanchal7/how-metadata-can-reveal-sensitive-information-during-pentesting-164037b33486)