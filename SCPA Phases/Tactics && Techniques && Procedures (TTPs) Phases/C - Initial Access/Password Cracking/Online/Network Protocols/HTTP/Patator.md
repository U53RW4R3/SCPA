# Patator

TODO: Provide more examples

`$ patator http_fuzz method=GET url=<URL> 0=passwords.lst header="Cookie: <cookie_session>" --threads=2 timeout=15 -x quit:fgrep!='<Error_message_response>',clen!='-1'`