# File Containers

Search Tag(s): #operation-security #luks #cryptography #command-line #linux

`$ cryptsetup --type luks2 -c aes-xts-plain64 -h sha512 -s 512 --pbkdf argon2id --use-urandom -y [--label <label_name>] luksFormat /path/to/container_or_drive`