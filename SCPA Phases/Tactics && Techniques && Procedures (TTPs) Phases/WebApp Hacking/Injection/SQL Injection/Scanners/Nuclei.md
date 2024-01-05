# Nuclei

`$ nuclei -u <URL> -t ~/nuclei-templates -id php-errors`

`$ nuclei -l ips.txt -id error-based-sql-injection -t ~/nuclei-templates`

`$ httpx -silent -l urls.txt | nuclei -tags sqli -t ~/nuclei-templates -o sqli-output.txt`