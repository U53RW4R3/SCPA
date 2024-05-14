# Setup

Search Tag(s): #lab #wordpress #webapp-pentesting

TODO: Fill this info

## Linux Wordpress Setup

Install dependencies.

```
$ sudo apt update && sudo apt install -y apache2 mariadb-server mariadb-client php php-mysqli php-gd libapache2-mod-php
```

```
$ sudo mysql_secure_installation
```


```
# mysql -u root -p
CREATE DATABASE wordpress;
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY '<password>';
GRANT ALL ON wordpress.* TO 'wp_user'@'localhost' IDENTIFIED BY '<password>';
FLUSH PRIVILEGES;
exit
```

```
$ wget https://www.wordpress.org/latest.tar.gz && \
sudo mkdir -p /var/www/html/wordpress/ && \
sudo tar xzf latest.tar.gz -C /var/www/html && \
sudo chown -R www-data:www-data /var/www/html/wordpress/ && \
sudo chmod -R 755 /var/www/html/wordpress/ && \
sudo chown -R www-data:www-data /var/www/html/wordpress/wp-content/uploads
```

## Windows Wordpress Setup

Download the [XAMPP](https://www.apachefriends.org/download.html) executable and follow the instructions during the wizard process.

TODO: Setup PHPMyAdmin for linux and make note of it as optional and setup XAMPP for Windows.

---
## References

- [[Lab Simulation Setup/Server/Linux/MySQL|Setup: MySQL]]

https://bitbelle.wordpress.com/portfolio/set-up-a-wordpress-pentesting-lab/

- [Hacking Articles: Lab Setup WordPress](https://www.hackingarticles.in/penetration-testing-lab-setup-wordpress/)

https://www.youtube.com/watch?v=9c-fl1JYCIY

https://www.youtube.com/watch?v=5JprReNkjzE