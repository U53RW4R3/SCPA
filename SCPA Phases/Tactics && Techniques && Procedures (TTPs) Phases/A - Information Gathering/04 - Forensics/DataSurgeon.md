# DataSurgeon

## 01 - Setup

Install Rust compiler.

```
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

$ wget -qO- https://sh.rustup.rs | sh

$ source "$HOME/.cargo/env"
```

Clone the repository.

```
$ wget -O- https://raw.githubusercontent.com/Drew-Alleman/DataSurgeon/main/install/install.sh | bash
```

## 02 - Help Menu

```
$ ds -h
Note: All extraction features (e.g: -i) work on a specified file (-f) or an output stream.

Usage: ds [OPTIONS]

Options:
  -f, --file <file>            File to extract information from
  -C, --clean                  Only displays the matched result, rather than the entire line
      --directory <directory>  Process all files found in the specified directory
  -T, --thorough               Doesn't stop at first match (useful for -C if multiple unique matches are on the same line
  -D, --display                Displays the filename assoicated with the content found (https://github.com/Drew-Alleman/DataSurgeon#reading-all-files-in-a-directory)
  -S, --suppress               Suppress the 'Reading standard input' message when not providing a file
      --drop <drop>            Specify a regular expression to exclude certain patterns from the search. (e.g --drop "^.{1,10}$" will hide all matches not under 10 characters)
      --filter <filter>        Include only lines that match the specified regex. (e.g: '--filter ^error' will only include lines that start with the word 'error'
  -X, --hide                   Hides the identifier string infront of the desired content (e.g: 'hash: ', 'url: ', 'email: ' will not be displayed.
  -o, --output <output>        Output's the results of the procedure to a local file (recommended for large files)
  -t, --time                   Time how long the operation took
  -e, --email                  Extract email addresses
  -p, --phone                  Extracts phone numbers
  -H, --hash                   Extract hashes (NTLM, LM, bcrypt, Oracle, MD5, SHA-1, SHA-224, SHA-256, SHA-384, SHA-512, SHA3-224, SHA3-256, SHA3-384, SHA3-512, MD4)
  -i, --ip-addr                Extract IP addresses
  -6, --ipv6-addr              Extract IPv6 addresses
  -m, --mac-addr               Extract MAC addresses
  -c, --credit-card            Extract credit card numbers
  -u, --url                    Extract urls
  -F, --files                  Extract filenames
  -b, --bitcoin                Extract bitcoin wallets
  -a, --aws                    Extract AWS keys
  -g, --google                 Extract Google service account private key ids (used for google automations services)
  -d, --dns                    Extract Domain Name System records
  -s, --social                 Extract social security numbers
  -h, --help                   Print help
  -V, --version                Print version
```

## 03 - Usage

Specify a file to extract information.

```
$ ds -f /path/to/file
```

Specify a directory with files to extract information.

```
$ ds -d /path/to/directory/
```

---
## References

- [DataSurgeon](https://github.com/Drew-Alleman/DataSurgeon)