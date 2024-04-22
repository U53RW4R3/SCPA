# A - HTTP

Search Tag(s): #empire #command-and-control

```
(Empire) > uselistener http

 Author       @harmj0y                                                              
 Description  Starts a http[s] listener (PowerShell or Python) that uses a GET/POST 
              approach.                                                             
 Name         HTTP[S]                                                               


┌Record Options────┬─────────────────────────────────────┬──────────┬─────────────────────────────────────┐
│ Name             │ Value                               │ Required │ Description                         │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ BindIP           │ 0.0.0.0                             │ True     │ The IP to bind to on the control    │
│                  │                                     │          │ server.                             │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ CertPath         │                                     │ False    │ Certificate path for https          │
│                  │                                     │          │ listeners.                          │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ Cookie           │ xhToxHyaIgSGxfmJ                    │ False    │ Custom Cookie Name                  │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ DefaultDelay     │ 5                                   │ True     │ Agent delay/reach back interval (in │
│                  │                                     │          │ seconds).                           │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ DefaultJitter    │ 0.0                                 │ True     │ Jitter in agent reachback interval  │
│                  │                                     │          │ (0.0-1.0).                          │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ DefaultLostLimit │ 60                                  │ True     │ Number of missed checkins before    │
│                  │                                     │          │ exiting                             │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ DefaultProfile   │ /admin/get.php,/news.php,/login/pro │ True     │ Default communication profile for   │
│                  │ cess.php|Mozilla/5.0 (Windows NT    │          │ the agent.                          │
│                  │ 6.1; WOW64; Trident/7.0; rv:11.0)   │          │                                     │
│                  │ like Gecko                          │          │                                     │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ Headers          │ Server:Microsoft-IIS/7.5            │ True     │ Headers for the control server.     │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ Host             │                                     │ True     │ Hostname/IP for staging.            │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ JA3_Evasion      │ False                               │ True     │ Randomly generate a JA3/S signature │
│                  │                                     │          │ using TLS ciphers.                  │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ KillDate         │                                     │ False    │ Date for the listener to exit       │
│                  │                                     │          │ (MM/dd/yyyy).                       │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ Launcher         │ powershell -noP -sta -w 1 -enc      │ True     │ Launcher string.                    │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ Name             │ http                                │ True     │ Name for the listener.              │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ Port             │                                     │ True     │ Port for the listener.              │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ Proxy            │ default                             │ False    │ Proxy to use for request (default,  │
│                  │                                     │          │ none, or other).                    │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ ProxyCreds       │ default                             │ False    │ Proxy credentials                   │
│                  │                                     │          │ ([domain\]username:password) to use │
│                  │                                     │          │ for request (default, none, or      │
│                  │                                     │          │ other).                             │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ SlackURL         │                                     │ False    │ Your Slack Incoming Webhook URL to  │
│                  │                                     │          │ communicate with your Slack         │
│                  │                                     │          │ instance.                           │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ StagerURI        │                                     │ False    │ URI for the stager. Must use        │
│                  │                                     │          │ /download/. Example:                │
│                  │                                     │          │ /download/stager.php                │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ StagingKey       │ e|E!-{[fIiJ6FAnw;:V7p>?)DS.HkN/&    │ True     │ Staging key for initial agent       │
│                  │                                     │          │ negotiation.                        │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ UserAgent        │ default                             │ False    │ User-agent string to use for the    │
│                  │                                     │          │ staging request (default, none, or  │
│                  │                                     │          │ other).                             │
├──────────────────┼─────────────────────────────────────┼──────────┼─────────────────────────────────────┤
│ WorkingHours     │                                     │ False    │ Hours for the agent to operate      │
│                  │                                     │          │ (09:00-17:00).                      │
└──────────────────┴─────────────────────────────────────┴──────────┴─────────────────────────────────────┘

(Empire: uselistener/http) >
```