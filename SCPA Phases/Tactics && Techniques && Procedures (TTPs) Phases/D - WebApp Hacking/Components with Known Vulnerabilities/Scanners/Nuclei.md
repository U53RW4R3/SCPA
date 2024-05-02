# Nuclei

TODO: Fill this info

Search Tag(s): #webapp #nuclei

- Find CVEs and public exploits.

`$ nuclei -u <URL> -t ~/nuclei-templates -id edb,cve`

- Detect webapp component that might have exploits.

`$ nuclei -u <URL> -t ~/nuclei-templates -id tech-detect`

- Finding metatags of a uncommon CMS (Content Management System) that might have exploits.

`$ nuclei -u <URL> -t ~/nuclei-templates -id metatag-cms`

- Old copyright symbols might indicate that the website uses old components.

`$ nuclei -u <URL> -t ~/nuclei-templates -id old-copyright`

---
## References

- [[ExploitDB]]

- [[Pompem]]