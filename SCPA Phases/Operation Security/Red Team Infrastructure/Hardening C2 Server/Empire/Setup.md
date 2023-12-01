# Empire

Search Tag(s): #red-team-infrastructure #empire

## 01 - Setup

### 1.1 - HTTP_HOP

```
(Empire) > uselistener http_hop

 Author       @harmj0y                                                              
 Description  Starts a http[s] listener (PowerShell or Python) that uses a GET/POST 
              approach.                                                             
 Name         HTTP[S] Hop                                                           


┌Record Options──────┬────────────────────────────────┬──────────┬────────────────────────────────────┐
│ Name               │ Value                          │ Required │ Description                        │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ DefaultProfile     │                                │ False    │ Default communication profile for  │
│                    │                                │          │ the agent, extracted from          │
│                    │                                │          │ RedirectListener automatically.    │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ Host               │                                │ True     │ Hostname/IP for staging.           │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ Launcher           │ powershell -noP -sta -w 1 -enc │ True     │ Launcher string.                   │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ Name               │ http_hop                       │ True     │ Name for the listener.             │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ OutFolder          │ /tmp/http_hop/                 │ True     │ Folder to output redirectors to.   │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ Port               │                                │ True     │ Port for the listener.             │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ RedirectListener   │                                │ True     │ Existing listener to redirect the  │
│                    │                                │          │ hop traffic to.                    │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ RedirectStagingKey │                                │ False    │ The staging key for the redirect   │
│                    │                                │          │ listener, extracted from           │
│                    │                                │          │ RedirectListener automatically.    │
├────────────────────┼────────────────────────────────┼──────────┼────────────────────────────────────┤
│ SlackURL           │                                │ False    │ Your Slack Incoming Webhook URL to │
│                    │                                │          │ communicate with your Slack        │
│                    │                                │          │ instance.                          │
└────────────────────┴────────────────────────────────┴──────────┴────────────────────────────────────┘

(Empire: uselistener/http_hop) >
```

### 1.2 - Redirector

TODO: Provide a usage example redirector for Empire

---
## References

- [Cobalt Strike Malleable C2 (Empire supports this feature with their own version)](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_main.htm)

- [Securing your Empire C2 with Apache mod_rewrite](https://thevivi.net/blog/infrastructure/2017-11-03-securing-your-empire-c2-with-apache-mod-rewrite/)

- [Tales of a Red Teamer](https://holdmybeersecurity.com/2018/04/30/tales-of-a-red-teamer-ub-2018/)

- [Beginning Powershell Empire Attack](https://www.securitynik.com/2022/02/beginning-powershell-empire-attack-in.html)

- [Red-Team-Infrastructure-Wiki](https://github.com/bluscreenofjeff/Red-Team-Infrastructure-Wiki)

- [Github Gist Native Windows User Agents Malicious](https://gist.github.com/GossiTheDog/77527a34cdecb0ad840910c0beb8ba41)

- [Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)