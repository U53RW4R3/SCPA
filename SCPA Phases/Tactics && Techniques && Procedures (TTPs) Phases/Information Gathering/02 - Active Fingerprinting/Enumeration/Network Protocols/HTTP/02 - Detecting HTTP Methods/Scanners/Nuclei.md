# Nuclei

- Gather HTTP methods

`$ nuclei -u <URL> -t ~/nuclei-templates -id options-method`

- Find a misconfiguration HTTP option to upload files.

`$ nuclei -u <URL> -t ~/nuclei-templates -id put-method-enabled`