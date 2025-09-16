# RoundCube

Step 1: Install Apache, MySQL, PHP, and other dependencies

```
sudo apt install apache2 mariadb-server php libapache2-mod-php php-mysql php-mbstring php-curl php-gd php-json php-xml php-zip
```

Step 2: Secure MySQL Installation
Run the MySQL secure installation script:

Step 3: Create a MySQL Database for Roundcube
Log in to MySQL as root:

```
sudo mysql -u root -p
```

Create a new database, user, and grant privileges:

```sql
CREATE DATABASE roundcubemail;
CREATE USER 'roundcubeuser'@'localhost' IDENTIFIED BY 'your_password_here';
GRANT ALL PRIVILEGES ON roundcubemail.* TO 'roundcubeuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

Step 5: Install Roundcube Webmail
Download and extract the latest stable version of Roundcube:

```
cd /tmp
wget https://github.com/roundcube/roundcubemail/releases/download/RELEASE_1_5_3/roundcubemail-1.5.3-complete.tar.gz
tar xzf roundcubemail-1.5.3-complete.tar.gz
sudo mv roundcubemail-1.5.3 /var/www/html/roundcube
```

Step 6: Configure Roundcube
Create a Roundcube configuration file:

```
sudo cp /var/www/html/roundcube/config/config.inc.php.sample /var/www/html/roundcube/config/config.inc.php
```

Edit the configuration file:

```
sudo nano /var/www/html/roundcube/config/config.inc.php
```

Configure the database settings:

```php
$config['db_dsnw'] = 'mysql://roundcubeuser:your_password_here@localhost/roundcubemail';
```

Save and close the file.

Step 7: Configure Apache
Enable necessary Apache modules:

```
sudo a2enmod rewrite
sudo systemctl restart apache2
```

Create a new Apache virtual host configuration file for Roundcube:

```
sudo nano /etc/apache2/sites-available/roundcube.conf
```

Add the following configuration:

```
<VirtualHost *:80>
    ServerAdmin webmaster@example.com
    ServerName webmail.example.com     # Replace with your domain or subdomain
    DocumentRoot /var/www/html/roundcube

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    <Directory /var/www/html/roundcube>
        Options -Indexes
        AllowOverride All
        Require all granted
    </Directory>

</VirtualHost>
```

Step 8: Enable the Roundcube Virtual Host and Restart Apache

```
sudo a2ensite roundcube.conf
sudo systemctl restart apache2
```

Step 9: Open Web Mail Server in Your Browser

Visit http://webmail.example.com (replace example.com with your domain) in your web browser to access the Roundcube webmail interface.

Step 10: Configure Postfix (Optional)
If you want to use Roundcube to send emails, you'll need to configure Postfix to relay emails for authenticated users. This setup is beyond the scope of a basic Roundcube installation, but you can find various tutorials online to set up Postfix as a mail relay with SMTP authentication.