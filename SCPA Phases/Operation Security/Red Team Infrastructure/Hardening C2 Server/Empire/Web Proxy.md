# Web Proxy

Search Tag(s): #red-team-infrastructure #empire

## 01 - HTTP_HOP

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

---
## References

- [drb-ra: C2IntelFeeds](https://github.com/drb-ra/C2IntelFeeds)

- [Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)