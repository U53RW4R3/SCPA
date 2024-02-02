# WPScan

## Help Menu

```
$ wpscan --hh                                                                                                                                                                                130 ⨯
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.24
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

Usage: wpscan [options]
        --url URL                                 The URL of the blog to scan
                                                  Allowed Protocols: http, https
                                                  Default Protocol if none provided: http
                                                  This option is mandatory unless update or help or hh or version is/are supplied
    -h, --help                                    Display the simple help and exit
        --hh                                      Display the full help and exit
        --version                                 Display the version and exit
        --ignore-main-redirect                    Ignore the main redirect (if any) and scan the target url
    -v, --verbose                                 Verbose mode
        --[no-]banner                             Whether or not to display the banner
                                                  Default: true
        --max-scan-duration SECONDS               Abort the scan if it exceeds the time provided in seconds
    -o, --output FILE                             Output to FILE
    -f, --format FORMAT                           Output results in the format supplied
                                                  Available choices: cli-no-colour, cli-no-color, json, cli
        --detection-mode MODE                     Default: mixed
                                                  Available choices: mixed, passive, aggressive
        --scope DOMAINS                           Comma separated (sub-)domains to consider in scope. 
                                                  Wildcard(s) allowed in the trd of valid domains, e.g: *.target.tld
                                                  Separator to use between the values: ','
        --user-agent, --ua VALUE
        --headers HEADERS                         Additional headers to append in requests
                                                  Separator to use between the headers: '; '
                                                  Examples: 'X-Forwarded-For: 127.0.0.1', 'X-Forwarded-For: 127.0.0.1; Another: aaa'
        --vhost VALUE                             The virtual host (Host header) to use in requests
        --random-user-agent, --rua                Use a random user-agent for each scan
        --user-agents-list FILE-PATH              List of agents to use with --random-user-agent
                                                  Default: /usr/share/rubygems-integration/all/gems/cms_scanner-0.13.8/app/user_agents.txt
        --http-auth login:password
    -t, --max-threads VALUE                       The max threads to use
                                                  Default: 5
        --throttle MilliSeconds                   Milliseconds to wait before doing another web request. If used, the max threads will be set to 1.
        --request-timeout SECONDS                 The request timeout in seconds
                                                  Default: 60
        --connect-timeout SECONDS                 The connection timeout in seconds
                                                  Default: 30
        --disable-tls-checks                      Disables SSL/TLS certificate verification, and downgrade to TLS1.0+ (requires cURL 7.66 for the latter)
        --proxy protocol://IP:port                Supported protocols depend on the cURL installed
        --proxy-auth login:password
        --cookie-string COOKIE                    Cookie string to use in requests, format: cookie1=value1[; cookie2=value2]
        --cookie-jar FILE-PATH                    File to read and write cookies
                                                  Default: /tmp/wpscan/cookie_jar.txt
        --cache-ttl TIME_TO_LIVE                  The cache time to live in seconds
                                                  Default: 600
        --clear-cache                             Clear the cache before the scan
        --cache-dir PATH                          Default: /tmp/wpscan/cache
        --server SERVER                           Force the supplied server module to be loaded
                                                  Available choices: apache, iis, nginx
        --force                                   Do not check if the target is running WordPress or returns a 403
        --[no-]update                             Whether or not to update the Database
        --api-token TOKEN                         The WPScan API Token to display vulnerability data, available at https://wpscan.com/profile
        --wp-content-dir DIR                      The wp-content directory if custom or not detected, such as "wp-content"
        --wp-plugins-dir DIR                      The plugins directory if custom or not detected, such as "wp-content/plugins"
        --interesting-findings-detection MODE     Use the supplied mode for the interesting findings detection. 
                                                  Available choices: mixed, passive, aggressive
        --wp-version-all                          Check all the version locations
        --wp-version-detection MODE               Use the supplied mode for the WordPress version detection, instead of the global (--detection-mode) mode.
                                                  Available choices: mixed, passive, aggressive
        --main-theme-detection MODE               Use the supplied mode for the Main theme detection, instead of the global (--detection-mode) mode.
                                                  Available choices: mixed, passive, aggressive
    -e, --enumerate [OPTS]                        Enumeration Process
                                                  Available Choices:
                                                   vp   Vulnerable plugins
                                                   ap   All plugins
                                                   p    Popular plugins
                                                   vt   Vulnerable themes
                                                   at   All themes
                                                   t    Popular themes
                                                   tt   Timthumbs
                                                   cb   Config backups
                                                   dbe  Db exports
                                                   u    User IDs range. e.g: u1-5
                                                        Range separator to use: '-'
                                                        Value if no argument supplied: 1-10
                                                   m    Media IDs range. e.g m1-15
                                                        Note: Permalink setting must be set to "Plain" for those to be detected
                                                        Range separator to use: '-'
                                                        Value if no argument supplied: 1-100
                                                  Separator to use between the values: ','
                                                  Default: All Plugins, Config Backups
                                                  Value if no argument supplied: vp,vt,tt,cb,dbe,u,m
                                                  Incompatible choices (only one of each group/s can be used):
                                                   - vp, ap, p
                                                   - vt, at, t
        --exclude-content-based REGEXP_OR_STRING  Exclude all responses matching the Regexp (case insensitive) during parts of the enumeration.
                                                  Both the headers and body are checked. Regexp delimiters are not required.
        --plugins-list LIST                       List of plugins to enumerate
                                                  Examples: 'a1', 'a1,a2,a3', '/tmp/a.txt'
        --plugins-detection MODE                  Use the supplied mode to enumerate Plugins.
                                                  Default: passive
                                                  Available choices: mixed, passive, aggressive
        --plugins-version-all                     Check all the plugins version locations according to the choosen mode (--detection-mode, --plugins-detection and --plugins-version-detection)
        --plugins-version-detection MODE          Use the supplied mode to check plugins' versions.
                                                  Default: mixed
                                                  Available choices: mixed, passive, aggressive
        --plugins-threshold THRESHOLD             Raise an error when the number of detected plugins via known locations reaches the threshold. Set to 0 to ignore the threshold.
                                                  Default: 100
        --themes-list LIST                        List of themes to enumerate
                                                  Examples: 'a1', 'a1,a2,a3', '/tmp/a.txt'
        --themes-detection MODE                   Use the supplied mode to enumerate Themes, instead of the global (--detection-mode) mode.
                                                  Available choices: mixed, passive, aggressive
        --themes-version-all                      Check all the themes version locations according to the choosen mode (--detection-mode, --themes-detection and --themes-version-detection)
        --themes-version-detection MODE           Use the supplied mode to check themes versions instead of the --detection-mode or --themes-detection modes.
                                                  Available choices: mixed, passive, aggressive
        --themes-threshold THRESHOLD              Raise an error when the number of detected themes via known locations reaches the threshold. Set to 0 to ignore the threshold.
                                                  Default: 20
        --timthumbs-list FILE-PATH                List of timthumbs' location to use
                                                  Default: /home/userware/.wpscan/db/timthumbs-v3.txt
        --timthumbs-detection MODE                Use the supplied mode to enumerate Timthumbs, instead of the global (--detection-mode) mode.
                                                  Available choices: mixed, passive, aggressive
        --config-backups-list FILE-PATH           List of config backups' filenames to use
                                                  Default: /home/userware/.wpscan/db/config_backups.txt
        --config-backups-detection MODE           Use the supplied mode to enumerate Config Backups, instead of the global (--detection-mode) mode.
                                                  Available choices: mixed, passive, aggressive
        --db-exports-list FILE-PATH               List of DB exports' paths to use
                                                  Default: /home/userware/.wpscan/db/db_exports.txt
        --db-exports-detection MODE               Use the supplied mode to enumerate DB Exports, instead of the global (--detection-mode) mode.
                                                  Available choices: mixed, passive, aggressive
        --medias-detection MODE                   Use the supplied mode to enumerate Medias, instead of the global (--detection-mode) mode.
                                                  Available choices: mixed, passive, aggressive
        --users-list LIST                         List of users to check during the users enumeration from the Login Error Messages
                                                  Examples: 'a1', 'a1,a2,a3', '/tmp/a.txt'
        --users-detection MODE                    Use the supplied mode to enumerate Users, instead of the global (--detection-mode) mode.
                                                  Available choices: mixed, passive, aggressive
        --exclude-usernames REGEXP_OR_STRING      Exclude usernames matching the Regexp/string (case insensitive). Regexp delimiters are not required.
    -P, --passwords FILE-PATH                     List of passwords to use during the password attack.
                                                  If no --username/s option supplied, user enumeration will be run.
    -U, --usernames LIST                          List of usernames to use during the password attack.
                                                  Examples: 'a1', 'a1,a2,a3', '/tmp/a.txt'
        --multicall-max-passwords MAX_PWD         Maximum number of passwords to send by request with XMLRPC multicall
                                                  Default: 500
        --password-attack ATTACK                  Force the supplied attack to be used rather than automatically determining one.
                                                  Multicall will only work against WP < 4.4
                                                  Available choices: wp-login, xmlrpc, xmlrpc-multicall
        --login-uri URI                           The URI of the login page if different from /wp-login.php
        --stealthy                                Alias for --random-user-agent --detection-mode passive --plugins-version-detection passive
```

## Usage

`$ wpscan --url "<URL>" --rua -o wordpress-scan-output.txt`

`$ wpscan --no-banner --url "<URL>" --rua`

`$ wpscan --url "<URL>" --disable-tls-checks`

`$ wpscan --url "<URL>" -e u,cb`

`$ wpscan --url "<URL>" -e <vp | ap | p>,<vt | at | t> --plugins-detection <mixed | passive | aggressive> --detection-mode <mixed | passive | aggressive>`

`$ wpscan --url "<URL>" -U <username | usernames.txt> -P passwords.lst`

`$ wpscan --url "<URL>" --rua --api-token <API>`