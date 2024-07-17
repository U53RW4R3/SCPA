# B - Manage Credentials

Search Tag(s): #empire #command-and-control #help-menu

## 01 - Help Menu

```
(Empire: credentials) > help

┌Help Options─────────────────────────────────────────────────────────┬──────────────────┐
│ Name   │ Description                                                │ Usage            │
├────────┼────────────────────────────────────────────────────────────┼──────────────────┤
│ help   │ Display the help menu for the current menu                 │ help             │
├────────┼────────────────────────────────────────────────────────────┼──────────────────┤
│ list   │ Get running/available agents                               │ list             │
├────────┼────────────────────────────────────────────────────────────┼──────────────────┤
│ remove │ Removes specified credential ID. if 'all' is provided, all │ remove <cred_id> │
│        │ credentials will be removed.                               │                  │
└────────┴────────────────────────────────────────────────────────────┴──────────────────┘
```

## 02 - Usage

* List the credentials

```
(Empire: usecredential/add) > list

┌Credentials─────┬────────┬───────────────┬──────────────┬───────────────┬─────┬────┬───────┐
│ ID │ CredType  │ Domain │ UserName      │ Host         │ Password/Hash │ SID │ OS │ Notes │
├────┼───────────┼────────┼───────────────┼──────────────┼───────────────┼─────┼────┼───────┤
│ 1  │ plaintext │ DEMO   │ Administrator │ 192.168.0.15 │ Password      │     │    │       │
└────┴───────────┴────────┴───────────────┴──────────────┴───────────────┴─────┴────┴───────┘
```

* Remove credential

```
(Empire: credentials) > remove 1
[*] Credential 1 removed.
```