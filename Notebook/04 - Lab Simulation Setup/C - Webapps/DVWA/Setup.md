# Setup

Search Tag(s): #lab #dvwa #webapp-pentesting

## Linux DVWA Setup

### Automated

```
$ sudo bash -c "$(curl --fail --show-error --silent --location https://raw.githubusercontent.com/IamCarron/DVWA-Script/main/Install-DVWA.sh)"
```

### Manual

Install dependencies.

```
$ sudo apt update && sudo apt install -y apache2 mariadb-server mariadb-client php php-mysqli php-gd libapache2-mod-php
```

Extract and setup DVWA.

```
$ sudo git clone https://github.com/digininja/DVWA.git /var/www/html/dvwa/ && \
sudo cp /var/www/html/dvwa/config/config.inc.php.dist /var/www/html/dvwa/config/config.inc.php && \
sudo chmod 777 /var/www/html/dvwa/hackable/uploads/ && \
sudo chown www-data /var/www/html/dvwa/config
```

Configure PHP file.

```
$ cat /etc/php/8.2/apache2/php.ini
..[omitted]..
allow_url_fopen = On
allow_url_include = On
..[omitted]..
display_errors = On
display_startup_errors = On
..[omitted]..
```

## Windows DVWA Setup

Download the [XAMPP](https://www.apachefriends.org/download.html) executable and follow the instructions during the wizard process.

TODO: Setup PHPMyAdmin for linux and make note of it as optional and setup XAMPP for Windows.

## Setup Database

Edit the `/var/www/html/dvwa/config/config.inc.php` file and add a password that is used for setting a MySQL user account.

`$ cat /var/www/html/dvwa/config/config.inc.php`

---

```php
$DBMS = 'MySQL';
$_DVWA = array();
$_DVWA[ 'db_server' ]   = getenv('DB_SERVER') ?: '127.0.0.1';
$_DVWA[ 'db_database' ] = 'dvwa';
$_DVWA[ 'db_user' ]     = 'dvwa';
$_DVWA[ 'db_password' ] = 'p@ssw0rd';
$_DVWA[ 'db_port']      = '3306';
// ..[omitted]..
$_DVWA[ 'default_security_level' ] = 'low';
```

- Enable Apache2 Webserver and MySQL Server

```
$ sudo systemctl start apache2

$ sudo systemctl start mysql
```

#### Setup Database user acccount

Setup MySQL server and leave root password empty.

```
$ sudo mysql_secure_installation
```

Create Database and `dvwa@localhost` DB user account.

```
$ sudo mysql
MariaDB [(none)]> CREATE DATABASE dvwa;

MariaDB [(none)]> CREATE USER dvwa@localhost IDENTIFIED BY 'p@ssw0rd';
```

You can of course change the password for the database user.

```
MariaDB [(none)]> ALTER USER dvwa@localhost IDENTIFIED BY 'p@ssw0rd';
```

#### Grant user privileges

This will grant the `dvwa@localhost` DB user with least privileges. But skip this step and move on for [[04 - Lab Simulation Setup/C - Webapps/DVWA/Setup#^14f9b2|granting all privileges]] to have the full experience of SQLi.

```
MariaDB [(none)]> GRANT ALL ON dvwa.* TO dvwa@localhost;
```

Note: For this demonstration let's grant `dvwa@localhost` using all SQL statements.

```
MariaDB [(none)]> GRANT ALL PRIVILEGES ON *.* TO dvwa@localhost;
```

^14f9b2

- You can of course grant privileges one by one.

```
MariaDB [(none)]> GRANT SELECT,INSERT,UPDATE,DROP,DELETE,EXECUTE ON dvwa.* TO dvwa@localhost;

MariaDB [(none)]> GRANT FILE ON *.* TO dvwa@localhost;
```

- To revoke all privileges.

```
MariaDB [(none)]> REVOKE ALL PRIVILEGES ON *.* FROM dvwa@localhost;
```

 Save changes.

```
MariaDB [(none)]> FLUSH PRIVILEGES;
```

Login as `dvwa@localhost` with a `dvwa` database.

```
$ mysql -u dvwa -pp@ssw0rd -D dvwa
```

## DNS Hosts Addresses

^214bb7

Map the DVWA IPv4 address as a DNS reference

```
$ sudo nano /etc/hosts
<web_server_IP> dvwa.local
```

---
## References

- [DVWA](https://github.com/digininja/DVWA)

- [Hacking Articles: Configure Web Application Penetration Testing Lab](https://www.hackingarticles.in/configure-web-application-penetration-testing-lab/)

- [Hacking Articles: Web Application Lab Setup on Windows](https://www.hackingarticles.in/web-application-lab-setup-on-windows/)

- [How Do I Change The Privileges For MySQL User that is Already Created](https://serverfault.com/questions/115950/how-do-i-change-the-privileges-for-mysql-user-that-is-already-created)

- [How to Create a New User Account in MySQL and Grant Permissions on a Database](https://blog.devart.com/how-to-create-a-new-user-and-grant-privileges.html)

- [MySQL GRANT Privileges](https://www.mysqltutorial.org/mysql-grant.aspx)

- [MySQL Privileges The Ultimate Guide](https://www.prisma.io/dataguide/mysql/authentication-and-authorization/privilege-management)