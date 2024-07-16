# Reset Teamserver Database

Search Tag(s): #havoc #command-and-control

`$ cat reset-teamserver.sh`

---

```bash
#!/bin/sh
echo "Stopping the Havoc TeamServer"
pid=$(ps aux | grep "havoc server" | grep -v grep | awk '{print $2}')
kill "$pid"

echo "Clearing the Database"
sqlite3 /opt/post-exploitation/Havoc/data/teamserver.db "DELETE FROM TS_Agents;"

echo "Agents cleared"
```