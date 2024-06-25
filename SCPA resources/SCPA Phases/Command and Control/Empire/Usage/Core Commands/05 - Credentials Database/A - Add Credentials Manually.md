# A - Add Credentials Manually

Search Tag(s): #empire #command-and-control #help-menu

## 01 - Help Menu

```
(Empire) > usecredential add

┌Record Options────┬──────────┬───────────────────────────────┐
│ Name     │ Value │ Required │ Description                   │
├──────────┼───────┼──────────┼───────────────────────────────┤
│ credtype │       │ True     │ Must be one of "plaintext" or │
│          │       │          │ "hash"                        │
├──────────┼───────┼──────────┼───────────────────────────────┤
│ domain   │       │ True     │                               │
├──────────┼───────┼──────────┼───────────────────────────────┤
│ username │       │ True     │                               │
├──────────┼───────┼──────────┼───────────────────────────────┤
│ host     │       │ True     │                               │
├──────────┼───────┼──────────┼───────────────────────────────┤
│ password │       │ True     │                               │
├──────────┼───────┼──────────┼───────────────────────────────┤
│ sid      │       │ False    │                               │
├──────────┼───────┼──────────┼───────────────────────────────┤
│ os       │       │ False    │                               │
├──────────┼───────┼──────────┼───────────────────────────────┤
│ notes    │       │ False    │                               │
└──────────┴───────┴──────────┴───────────────────────────────┘
```

## 02 - Usage

```
(Empire: usecredential/add) > set credtype <plaintext | hash>

(Empire: usecredential/add) > set domain <domain_name>

(Empire: usecredential/add) > set username <username>

(Empire: usecredential/add) > set password <password>

(Empire: usecredential/add) > set host <target_IP>

(Empire: usecredential/add) > execute
```