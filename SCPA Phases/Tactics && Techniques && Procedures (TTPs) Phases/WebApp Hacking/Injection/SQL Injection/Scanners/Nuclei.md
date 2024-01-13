# Nuclei

`$ nuclei -u <URL> -t ~/nuclei-templates -id php-errors`

`$ nuclei -l ip_targets.txt -id error-based-sql-injection -t ~/nuclei-templates`

`$ httpx -silent -l url_targets.txt | nuclei -tags sqli -t ~/nuclei-templates -o sqli-output.txt`