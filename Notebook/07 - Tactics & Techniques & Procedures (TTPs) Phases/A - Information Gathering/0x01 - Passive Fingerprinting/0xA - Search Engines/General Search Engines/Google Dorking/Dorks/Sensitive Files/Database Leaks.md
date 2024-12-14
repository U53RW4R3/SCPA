# Database Leaks

## Generic

```
filetype:sql "insert into" (pass|passwd|password)
filetype:sql ("values * MD5" | "values * password" | "values * encrypt")
filetype:sql +"IDENTIFIED BY" -cvs
filetype:sql password
ext:sql intext:admin inurl:admin
```

## MySQL

```
"MySQL dump" ext:sql "Host" "Table structure for table"
"index of" "user.MYD"
```

## Oracle

TNS names configuration.

```
filetype:ora tnsnames
```

## PHPMyAdmin

```
"phpMyAdmin MYSQL-Dump" "INSERT INTO" -"the"
filetype:txt "phpMyAdmin MySQL-Dump"
```