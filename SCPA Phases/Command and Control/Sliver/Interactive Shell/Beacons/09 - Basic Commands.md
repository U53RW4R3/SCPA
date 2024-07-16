# 09 - Basic Commands

Search Tag(s): #sliver #command-and-control #interactive-shell

## Navigation

* Change Directory

```
sliver (IMPLANT_NAME) > cd <directory>
```

* Get current working directory

```
sliver (IMPLANT_NAME) > pwd
```

## List Contents

### Help Menu

```
sliver (IMPLANT_NAME) > ls -h

Command: ls <remote path>
About: List remote files in current directory, or path if provided.

Sorting
Directory and file listings are sorted by name in ascending order by default.  Listings can also be sorted by size (-s) and modified time (-m).  All sorts can be reversed with -r.

Filters
Filters are a way to limit search results to directory and file names matching given criteria.

Filters are specified after the path.  A blank path will filter on names in the current directory.  For example:
/etc/passwd will display the listing for /etc/passwd.  "/etc/" is the path, and "passwd" is the filter.

Directory and file listings can be filtered using the following patterns:
'*': Wildcard, matches any sequence of non-path separators (slashes)
        Example: n*.txt will match all file and directory names starting with n and ending with .txt

'?': Single character wildcard, matches a single non-path separator (slashes)
        Example: s?iver will match all file and directory names starting with s followed by any non-separator character and ending with iver.

'[{range}]': Match a range of characters.  Ranges are specified with '-'. This is usually combined with other patterns. Ranges can be negated with '^'.
        Example: [a-c] will match the characters a, b, and c.  [a-c]* will match all directory and file names that start with a, b, or c.
                ^[r-u] will match all characters except r, s, t, and u.

If you need to match a special character (*, ?, '-', '[', ']', '\\'), place '\\' in front of it (example: \\?).
On Windows, escaping is disabled. Instead, '\\' is treated as path separator.


Usage:
======
  ls [flags] [path]

Args:
=====
  path  string    path to enumerate (default: .)

Flags:
======
  -h, --help            display help
  -m, --modified        sort by modified time
  -r, --reverse         reverse sort order
  -s, --size            sort by size
  -t, --timeout  int    command timeout in seconds (default: 60)
```

### Usage

```
sliver (IMPLANT_NAME) > ls [drive_letter:/]path/to/remote/directory/
```

## File Manipulation

```
sliver (IMPLANT_NAME) > cp
```

```
sliver (IMPLANT_NAME) > mv
```

```
sliver (IMPLANT_NAME) > cat
```

```
sliver (IMPLANT_NAME) > mkdir
```

chown
chmod

```
sliver (IMPLANT_NAME) > rm [-F] [drive_letter:/]path/to/remote/file

sliver (IMPLANT_NAME) > rm [-F] -r [drive_letter:/]path/to/remote/directory
```

## Load Extension

## Upload and Download

### Help Menu

```
sliver (IMPLANT_NAME) > download -h

Command: download [remote src] <local dst>
About: Download a file or directory from the remote system. Directories will be downloaded as a gzipped TAR file.
Filters
Filters are a way to limit downloads to file names matching given criteria. Filters DO NOT apply to directory names.

Filters are specified after the path.  A blank path will filter on names in the current directory.  For example:
download /etc/*.conf will download all files from /etc whose names end in .conf. /etc/ is the path, *.conf is the filter.

Downloads can be filtered using the following patterns:
'*': Wildcard, matches any sequence of non-path separators (slashes)
        Example: n*.txt will match all file names starting with n and ending with .txt

'?': Single character wildcard, matches a single non-path separator (slashes)
        Example: s?iver will match all file names starting with s followed by any non-separator character and ending with iver.

'[{range}]': Match a range of characters.  Ranges are specified with '-'. This is usually combined with other patterns. Ranges can be negated with '^'.
        Example: [a-c] will match the characters a, b, and c.  [a-c]* will match all file names that start with a, b, or c.
                ^[r-u] will match all characters except r, s, t, and u.

If you need to match a special character (*, ?, '-', '[', ']', '\\'), place '\\' in front of it (example: \\?).
On Windows, escaping is disabled. Instead, '\\' is treated as path separator.

Usage:
======
  download [flags] remote-path [local-path]

Args:
=====
  remote-path  string    path to the file or directory to download
  local-path   string    local path where the downloaded file will be saved (default: .)

Flags:
======
  -F, --file-type string    force a specific file type (binary/text) if looting
  -h, --help                display help
  -X, --loot                save output as loot
  -n, --name      string    name to assign the download if looting
  -r, --recurse             recursively download all files in a directory
  -t, --timeout   int       command timeout in seconds (default: 60)
  -T, --type      string    force a specific loot type (file/cred) if looting
```

```
sliver (IMPLANT_NAME) > upload -h

Command: upload [local src] <remote dst>
About: Upload a file to the remote system.

Usage:
======
  upload [flags] local-path [remote-path]

Args:
=====
  local-path   string    local path to the file to upload
  remote-path  string    path to the file or directory to upload to

Flags:
======
  -h, --help           display help
  -i, --ioc            track uploaded file as an ioc
  -t, --timeout int    command timeout in seconds (default: 60)
```

## Background