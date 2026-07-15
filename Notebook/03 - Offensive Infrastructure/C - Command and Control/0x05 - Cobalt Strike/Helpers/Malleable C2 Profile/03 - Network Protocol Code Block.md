---
author(s):
  - Userware
tags:
  - helpers
  - red-team-infrastructure
  - cobalt-strike
---
# 03 - Network Protocol Code Block

## 3.1 - HTTP Block

### 3.1.1 - HTTP Config

Just to take care of the default HTTP settings.

```
http-config {
	# Set Header names and values to make it seem like a webserver
     set headers "Date, Server, Content-Length, Keep-Alive, 
                    Connection, Content-Type";
     header "Server" "Apache";
     header "Content-Length" "";
     header "Keep-Alive" "timeout=5, max=100";
     header "Connection" "Keep-Alive”;
     
     header "Content-Type" "";
     set trust_x_forwarded_for "true";
     
     # Block specific User Agents
     set block_useragents "curl*,lynx*,wget*";
}
```

### 3.1.2 - HTTP Staging (Metasploit compatible payloads)

TODO: Finish the rest of the HTTP code block and provide steps to append NOPs or byte encoded image file via `hexdump`.

```
http-stager {
     set uri_x86 "/filename_32.<gif | jpg | png | jpeg | woff | woff2 | tiff>"; 
     set uri_x64 "/filename_64.<gif | jpg | png | jpeg | woff | woff2 | tiff>";
     
     client {
	     parameter "id" "1234";
	     header "Cookie" "SomeValue";
	     
	 server {
	     header "Content-Type" "image/<gif | jpg | png | jpeg | woff | woff2 | tiff>"; 
	     output {
	          prepend "GIF89a"; 
	          print;
	     }
	}
}
```

### 3.1.3 - HTTP GET Request Block

```
# Optionally you can add more http blocks by inserting variant names
# you can clearly see once you add a HTTP(S) listener
# http-get <variant_name> {

http-get {
	set verb "GET";
	set uri "";
}
```

### 3.1.4 - HTTP POST Request Block

```
# Optionally you can add more http blocks by inserting variant names
# you can clearly see once you add a HTTP(S) listener
# http-post <variant_name> {

http-post {
	set verb "POST";
	set uri "";
}
```

### 3.1.5 - HTTP Beacons

```
http-beacon {
    set library "winhttp"; (by default)
    # set library "wininet";
}
```

### 3.1.6 - HTTP Variant Configs

```
http-beacon "wininet-beacon-variant" {
    set library "wininet";
}

http-get "HTTP-GET-Variant" {
	set verb "GET";
	set uri "";
}

http-post "HTTP-POST-Variant" {
	set verb "POST";
	set uri "";
}
```

## 3.2 - DNS Block

TODO: Fill this info

```
dns-beacon {

}
```