# Encyclopedia Scraper

Note: This only works for wikipedia. Improvements and suggestions are highly encouraged.

```bash
#!/bin/bash

# Encyclopedia web scraper

function process_url() {
    url="$1"

    # Base URL
    base_url=$(echo "$url" | grep -Eo "https?://[^/]+")

    # Download the raw contents of the page
    curl -o "${directory_destination}raw.html" -s "$url"

    # Print extracted URLs
    grep -Eo 'href="/wiki/[^"]+"' "${directory_destination}raw.html" | sed 's|href="\(\/wiki\/[^"]\+\)"|'"$base_url\1"'|' > "${directory_destination}raw_urls.txt"
    grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" "${directory_destination}raw.html" | awk -F "/" '{print $3}' | sort -u >> "${directory_destination}raw_urls.txt"

    # Sort the URLs
    sort -u "${directory_destination}raw_urls.txt" > "${directory_destination}unique_urls.txt"

    # Download content of extracted URLs
    wget -i "${directory_destination}unique_urls.txt" -qO- | grep -Eo "https?://[^/]+" | grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" | sort -u > "${directory_destination}urls.txt"

    # Clean up
    rm "${directory_destination}raw.html"
    rm "${directory_destination}raw_urls.txt"
    rm "${directory_destination}unique_urls.txt"
}

if [ "$#" -lt 1 ] || [ "$#" -gt 2 ] || [ $1 = "-h" ]
then
    echo "Usage: $0 <URL_FILE | URL> [OUTPUT_DIRECTORY]"
    echo "Examples: $0 urls.txt ./"
    echo "Examples: $0 urls.txt /path/to/directory/"
    echo "Examples: $0 https://en.wikipedia.com/ ./"
    echo "Examples: $0 https://en.wikipedia.com/ /path/to/directory/"
    exit 1
fi

# Check if a URL or URL file is provided
if [ -f "$1" ]
then
    # Read URLs from the file
    urls_file="$1"
else
    # Treat the argument as a single URL
    urls_file=""
    single_url="$1"
fi

# Output directory
if [ "$#" -eq 2 ]
then
    directory_destination="${2%/}/"
else
    directory_destination="./"
fi

# Create the directory if it doesn't exist
mkdir -p "$directory_destination"

if [ -n "$urls_file" ]
then
    # Process URLs from the file line by line
    while IFS= read -r url
    do
        process_url "$url"
    done < "$urls_file"
elif [ -n "$single_url" ]
then
    process_url "$single_url"
fi
```

- Scrape the URLs from encyclopedia websites.

```
$ chmod +x encyclopedia-scraper.sh

$ ./encyclopedia-scraper.sh https://en.wikipedia.com/ Results_Directory
```

Here are the list of targets for the scraper. Just copy the URL and paste it in the bash script.

```
List of companies of <country_name>
List of multinational companies with research and development centres in <country_name>
List of <country_name> companies listed on the Nasdaq
Companies of <country_name> by industry

List of lighthouses in <country_name>
List of airlines of <country_name>
List of airports in <country_name>
List of casinos in the <country_name>

Logistics companies of the <country_name>
Shipping companies of <country_name>
List of automobile manufacturers of <country_name>

Transport companies of <country_name>
Bus companies of <country_name>
List of cargo airlines

List of fast food restaurant in <country_name>
List of restaurant chains in <country_name>

List of internet service providers in <country_name>
List of <country_name> telephone companies
Telecommunications in <country_name>
VPS Providers
Web Hosting Providers
Data Centers

Computer companies of <country_name>
List of computer system manufacturers
List of computer hardware manufacturers
<country_name> computer hardware manufacturers

Foreign exchange companies

Mining in <country_name>
Mines in <country_name>

List of <country_name> defense contractors
```

---
## References

- [[Gathering URLs References]]