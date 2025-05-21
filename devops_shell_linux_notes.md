# 🐧 DevOps Shell Scripting & Linux Basics

## 🔰 Shebang
```bash
#!/bin/bash
Used at the start of shell scripts to indicate the interpreter.
```

## 🔐 File Permissions
```bash
chmod 777 filename
```
Sets full permissions (read, write, execute) for:

- 7 – Owner (root)
- 7 – Group
- 7 – Others (me)

Permission values:
- 1 – Execute
- 2 – Write
- 4 – Read

## ⚙️ Why Shell Scripts in DevOps?
Shell scripts are widely used for:
- Infrastructure maintenance
- Lightweight automation on Linux systems
- Git operations
- Configuration management

## 🧠 System Monitoring Commands
| Command    | Description                                 |
|------------|---------------------------------------------|
| top        | Live view of CPU, memory, and disk usage    |
| df -h      | Human-readable disk usage info              |
| free       | Displays memory usage                       |
| nproc      | Number of CPU cores                         |

## 🧰 Process Management
```bash
ps -ef                          # Shows all running processes
ps -ef | grep "audited" | awk -F" " '{print $2}'  # Finds a specific process and prints its PID
kill -9 <PID>                   # Force kills a process by PID
```

## 🧪 Debugging & Execution
```bash
set -x       # Enable debug mode in shell scripts (logs each command before execution)
sudo su -    # Switch to root user
```

## 🔍 Log Analysis
```bash
curl logfile.log | grep "ERROR"
wget <url>    # Downloads files and saves them locally; useful for automation
```

## 🔎 File & Directory Utilities
```bash
sudo find / -name pam    # Searches entire system for folders/files named "pam"
sort                     # Sorts lines in files alphabetically or numerically
```

## 🔁 Links
- **Soft Links (Symbolic)**: Memory-based shortcuts to a file.
- **Hard Links**: Actual duplicate of the original file; can be reused even if the original is deleted.

## 🌐 Network Utilities
```bash
traceroute <hostname>     # Tracks the route packets take
tracepath <hostname>      # Similar to traceroute, often with fewer privileges
```

## 🔄 Log Management
- **logrotate**: Automatically rotates and compresses logs.
- Uses formats like `.gzip` or `.zip` to archive older logs.

## 📜 Example Script 1
```bash
#!/bin/bash

for i in {1..100};do
    if (( (i % 3 == 0 || i % 5 == 0) && i % 15 != 0)); then
        echo $i
    fi
done
```
**Output:**
```
3 5 6 9 10 12 18 20 21 24 25 27 33 35 36 39 40 42 48 50 51 54 55 57 63 65 66 69 70 72 78 80 81 84 85 87 93 95 96 99 100
```

## 📜 Example Script 2
```bash
#!/bin/bash

x="mississipi"
grep -o "s" <<< "$x" | wc -l
```
**Output:** `4`

---
**Author:** Deepakraj Ravi  
**Use Case:** Quick-reference DevOps & Linux notes for beginners and professionals.