# Usage

Search Tag(s): #empire #command-and-control #help-menu

## 01 - Help Menu

```
(Empire) > agents

┌Agents─────┬──────────┬─────────────┬──────────┬─────────┬─────┬───────┬───────────┬──────────┐
│ ID │ Name │ Language │ Internal IP │ Username │ Process │ PID │ Delay │ Last Seen │ Listener │
└────┴──────┴──────────┴─────────────┴──────────┴─────────┴─────┴───────┴───────────┴──────────┘

(Empire: agents) > help

┌Help Options───────────────────────────────────────────────────────┬──────────────────────────────────────┐
│ Name   │ Description                                              │ Usage                                │
├────────┼──────────────────────────────────────────────────────────┼──────────────────────────────────────┤
│ clear  │ Clear tasks for selected listener                        │ clear <agent_name>                   │
├────────┼──────────────────────────────────────────────────────────┼──────────────────────────────────────┤
│ help   │ Display the help menu for the current menu               │ help                                 │
├────────┼──────────────────────────────────────────────────────────┼──────────────────────────────────────┤
│ kill   │ Kills and removes specified agent [agent_name, stale, or │ kill <agent_name>                    │
│        │ all].                                                    │                                      │
├────────┼──────────────────────────────────────────────────────────┼──────────────────────────────────────┤
│ list   │ Get running/available agents                             │ list                                 │
├────────┼──────────────────────────────────────────────────────────┼──────────────────────────────────────┤
│ rename │ Rename selected listener                                 │ rename <agent_name> <new_agent_name> │
└────────┴──────────────────────────────────────────────────────────┴──────────────────────────────────────┘
```

## 02 - Usage

- List available agents.

`(Empire: agents) > list`

- Rename selected agent.

`(Empire: agents) > rename <agent_name> <new_agent_name>`

- Clear tasks on the selected agent.

`(Empire: agents) > clear <agent_name>`

- Kill current agent.

`(Empire: agents) > kill <agent_name>`