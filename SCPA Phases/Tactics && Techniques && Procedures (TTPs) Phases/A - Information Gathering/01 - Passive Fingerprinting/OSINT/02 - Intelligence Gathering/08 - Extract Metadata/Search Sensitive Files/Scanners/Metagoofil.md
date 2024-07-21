# Metagoofil

## 01 - Help Menu

```
$ metagoofil -h
usage: metagoofil.py [-h] -d DOMAIN [-e DELAY] [-f [SAVE_FILE]] [-i URL_TIMEOUT] [-l SEARCH_MAX] [-n DOWNLOAD_FILE_LIMIT] [-o SAVE_DIRECTORY] [-r NUMBER_OF_THREADS] -t FILE_TYPES
                     [-u [USER_AGENT]] [-w]

Metagoofil v1.2.0 - Search Google and download specific file types.

options:
  -h, --help            show this help message and exit
  -d DOMAIN             Domain to search.
  -e DELAY              Delay (in seconds) between searches. If it's too small Google may block your IP, too big and your search may take a while. Default: 30.0
  -f [SAVE_FILE]        Save the html links to a file.
                        no -f = Do not save links
                        -f = Save links to html_links_<TIMESTAMP>.txt
                        -f SAVE_FILE = Save links to SAVE_FILE
  -i URL_TIMEOUT        Number of seconds to wait before timeout for unreachable/stale pages. Default: 15
  -l SEARCH_MAX         Maximum results to search. Default: 100
  -n DOWNLOAD_FILE_LIMIT
                        Maximum number of files to download per filetype. Default: 100
  -o SAVE_DIRECTORY     Directory to save downloaded files. Default is current working directory, "."
  -r NUMBER_OF_THREADS  Number of downloader threads. Default: 8
  -t FILE_TYPES         file_types to download (pdf,doc,xls,ppt,odp,ods,docx,xlsx,pptx). To search all 17,576 three-letter file extensions, type "ALL"
  -u [USER_AGENT]       User-Agent for file retrieval against -d domain.
                        no -u = "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
                        -u = Randomize User-Agent
                        -u "My custom user agent 2.0" = Your customized User-Agent
  -w                    Download the files, instead of just viewing search results.

```

## 02 - Usage

Search for files

```
$ metagoofil -u "<user_agent>" -d <domain.com> -t pdf,doc,docx,docm,xls,xlsx,xlsm,csv,ppt,pptx,pptm -l 25 -f file_links.txt
```

Download the files

```
$ metagoofil -u "<user_agent>" -d <domain.com> -t pdf,doc,docx,docm,xls,xlsx,xlsm,csv,ppt,pptx,pptm -l 25 -w -o output_files
```

---
## References

- [Metagoofil](https://github.com/laramies/metagoofil)

- [[OSINT Framework]]