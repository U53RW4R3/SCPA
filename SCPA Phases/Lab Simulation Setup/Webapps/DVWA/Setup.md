# Setup

#dvwa #lab #webapp
## Linux DVWA Setup

- Install dependencies

```
$ sudo apt update && sudo apt install -y apache2 mariadb-server mariadb-client php php-mysqli php-gd libapache2-mod-php
```

- Extract and setup DVWA

```
$ wget https://github.com/digininja/DVWA/archive/refs/tags/2.3.tar.gz

$ sudo tar xzf DVWA-2.3.tar.gz -C /var/www/html/

$ sudo mv /var/www/html/DVWA-2.3 /var/www/html/dvwa/

$ sudo cp /var/www/html/dvwa/config/config.inc.php.dist

$ sudo chmod -R 777 /var/www/html/dvwa/

$ sudo chown -R www-data:www-data /var/www/html/dvwa/

$ sudo cp /var/www/html/dvwa/config/config.inc.php.dist /var/www/html/dvwa/config/config.inc.php
```

- Configure PHP file

```
$ sudo nano /etc/php/7.4/apache2/php.ini
allow_url_include = On  
display_startup_errors = On  
display_errors = On
```

```
$ sudo nano /var/www/html/dvwa/config/config.inc.php
$_DVWA[ 'default_security_level' ] = 'low';
```

- Enable Apache2 Webserver and MySQL Server

```
$ sudo systemctl start apache2

$ sudo systemctl start mysql
```

- Setup MySQL server and leave root password empty.

`$ sudo mysql_secure_installation`

- Create Database and `dvwa@localhost` DB user account.

```
$ sudo mysql
MariaDB [(none)]> CREATE DATABASE dvwa;

MariaDB [(none)]> CREATE USER dvwa@localhost IDENTIFIED BY 'p@ssw0rd';

MariaDB [(none)]> ALTER USER dvwa@localhost IDENTIFIED BY 'p@ssw0rd';
```

- This will grant the `dvwa@localhost` DB user with least privileges.

```
MariaDB [(none)]> GRANT ALL ON dvwa.* TO dvwa@localhost;
```

Note: For this demonstration let's grant `dvwa@localhost` using all SQL statements.

`MariaDB [(none)]> GRANT ALL PRIVILEGES ON *.* TO dvwa@localhost;`

- You can of course grant privileges one by one.

```
MariaDB [(none)]> GRANT INSERT ON *.* TO dvwa@localhost;

MariaDB [(none)]> GRANT SELECT ON *.* TO dvwa@localhost;

MariaDB [(none)]> GRANT DROP ON *.* TO dvwa@localhost;

MariaDB [(none)]> GRANT DELETE ON *.* TO dvwa@localhost;

MariaDB [(none)]> GRANT UPDATE ON *.* TO dvwa@localhost;

MariaDB [(none)]> GRANT FILE ON *.* TO dvwa@localhost;
```

- Save changes

`MariaDB [(none)]> FLUSH PRIVILEGES;`

- Login as `dvwa@localhost` with a `dvwa` database.

`$ mysql -u dvwa -pp@ssw0rd -D dvwa`

## DNS Hosts Addresses

^214bb7

Map the DVWA IPv4 address as a DNS reference

```
$ sudo nano /etc/hosts
<DVWA_Server_IP> dvwa.local
```

## References

- [DVWA](https://github.com/digininja/DVWA)