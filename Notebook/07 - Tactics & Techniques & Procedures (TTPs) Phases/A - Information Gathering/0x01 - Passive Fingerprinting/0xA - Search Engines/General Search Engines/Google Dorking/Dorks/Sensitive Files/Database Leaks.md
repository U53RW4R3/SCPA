# Database Leaks

## Generic

```
filetype:sql "insert into" (pass|passwd|password)
filetype:sql ("values * MD5" | "values * password" | "values * encrypt")
filetype:sql +"IDENTIFIED BY" -cvs
filetype:sql password
```

## MySQL

```
"MySQL dump" ext:sql "Host" "Table structure for table"
```

## PHPMyAdmin

```
"phpMyAdmin MYSQL-Dump" "INSERT INTO" -"the"
"phpMyAdmin MySQL-Dump" filetype:txt
```