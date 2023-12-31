# Nuclei

- Detect wordpress themes and plugins

`$ nuclei -u <URL> -t ~/nuclei-templates -id wordpress-themes-detect,wordpress-plugins-detect`

- Bruteforce common credentials

`$ nuclei -u <URL> -t ~/nuclei-templates -id wordpress-weak-credentials`