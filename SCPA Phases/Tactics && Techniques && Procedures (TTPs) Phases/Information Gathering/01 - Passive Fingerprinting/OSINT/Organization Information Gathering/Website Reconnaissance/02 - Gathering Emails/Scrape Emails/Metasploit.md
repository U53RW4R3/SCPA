# Metasploit

```
msf > use auxiliary/gather/search_email_collector

msf auxiliary(gather/search_email_collector) > options

Module options (auxiliary/gather/search_email_collector):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   DOMAIN                          yes       The domain name to locate email addresses for
   OUTFILE                         no        A filename to store the generated email list
   SEARCH_BING    true             yes       Enable Bing as a backend search engine
   SEARCH_GOOGLE  true             yes       Enable Google as a backend search engine
   SEARCH_YAHOO   true             yes       Enable Yahoo! as a backend search engine

msf auxiliary(gather/search_email_collector) > set domain <website.com>

msf auxiliary(gather/search_email_collector) > set search_bing <true | false>

msf auxiliary(gather/search_email_collector) > set search_google <true | false>

msf auxiliary(gather/search_email_collector) > set search_yahoo <true | false>

msf auxiliary(gather/search_email_collector) > set outfile /path/to/file.txt

msf auxiliary(gather/search_email_collector) > run
```