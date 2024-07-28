# A - Help Menu

Search Tag(s): #help-menu #command-and-control #empire

```
(Empire) > admin
(Empire: admin) > help

┌Help Options──────────────┬──────────────────────────────────────────────────────────────┬─────────────────────────────────────────┐
│ Name                     │ Description                                                  │ Usage                                   │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ add_notes                │ Add user notes (use quotes)                                  │ add_notes <notes>                       │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ clear_notes              │ Clear user notes                                             │ clear_notes                             │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ create_user              │ Create user account for Empire                               │ create_user <username> <password>       │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ delete_malleable_profile │ Delete malleable c2 profile from the database                │ delete_malleable_profile <profile_name> │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ disable_user             │ Disable user account for Empire                              │ disable_user <user_id>                  │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ download                 │ Download a file from the server to /empire/client/downloads  │ download <filename>                     │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ enable_user              │ Enable user account for Empire                               │ enable_user <user_id>                   │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ help                     │ Display the help menu for the current menu                   │ help                                    │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ keyword_obfuscation      │ Add key words to to be obfuscated from commands. Empire will │ keyword_obfuscation <keyword>           │
│                          │ generate a random word if no replacement word is provided.   │ [replacement]                           │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ load_malleable_profile   │ Load malleable c2 profile to the database                    │ load_malleable_profile                  │
│                          │                                                              │ <profile_directory> [profile_category]  │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ malleable_profile        │ View malleable c2 profile                                    │ malleable_profile <profile_name>        │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ notes                    │ Display your notes                                           │ notes                                   │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ obfuscate                │ Turn on obfuscate all future powershell commands run on all  │ obfuscate <obfucate_bool>               │
│                          │ agents.                                                      │                                         │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ obfuscate_command        │ Set obfuscation technique to run for all future powershell   │ obfuscate_command <obfucation_type>     │
│                          │ commands run on all agents.                                  │                                         │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ preobfuscate             │ Preobfuscate modules on the server.                          │ preobfuscate <force_reobfuscation>      │
│                          │                                                              │ <obfuscation_command>                   │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ report                   │ Produce report CSV and log files: sessions.csv,              │ report                                  │
│                          │ credentials.csv, master.log                                  │                                         │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ upload                   │ Upload a file to the server from /empire/client/downloads.   │ upload <file_directory>                 │
│                          │ Use '-p' for a file selection dialog.                        │                                         │
├──────────────────────────┼──────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
│ user_list                │ Display all Empire user accounts                             │ user_list                               │
└──────────────────────────┴──────────────────────────────────────────────────────────────┴─────────────────────────────────────────┘

(Empire: admin) >
```