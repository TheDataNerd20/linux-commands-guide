# Linux Commands Guide for Data Engineers

A comprehensive, production-ready reference for essential Linux commands used in data engineering. Master these commands and you'll be 10x more productive on the job.

**Author:** Vishnu Vardhan A | Senior Data Engineer  
**Last Updated:** November 2024  
**License:** MIT

---

## 🎯 Quick Navigation

| Category | Commands | Real-World Use |
|----------|----------|----------------|
| **File Operations** | `ls`, `cd`, `cp`, `mv`, `rm` | Navigate, organize data |
| **Text Processing** | `grep`, `awk`, `sed`, `cut` | Parse, transform logs & data |
| **Permissions** | `chmod`, `chown` | Secure data access |
| **Processes** | `ps`, `top`, `kill`, `nice` | Monitor ETL jobs |
| **System Admin** | `systemctl`, `yum`, `usermod` | Manage services & access |
| **Networking** | `ssh`, `scp`, `firewall-cmd` | Connect to servers & transfer data |
| **Disk & Storage** | `df`, `du`, `mount`, `lvm` | Monitor & manage storage |
| **Logging** | `tail -f`, `journalctl`, `grep` | Monitor running jobs |
| **Scheduling** | `crontab` | Automate daily ETL |

---

## 📚 Full Guide

See [COMMANDS.md](COMMANDS.md) for the complete comprehensive guide with:
- All 9 command categories explained
- 100+ essential commands
- Real-world data engineering examples
- Performance troubleshooting checklist
- Learning path (4-week mastery plan)

---

## 🚀 Quick Start Examples

### Monitor Your ETL Job
```bash
tail -f /var/log/etl_job.log
```

### Find Errors in Logs
```bash
grep "ERROR" app.log | wc -l
```

### Check Disk Space
```bash
df -h /data
du -sh /* | sort -rh | head -10
```

### Run Background Job (Survives Logout)
```bash
nohup python etl_pipeline.py > etl.log 2>&1 &
```

### Schedule Daily Job at 2 AM
```bash
0 2 * * * /usr/local/bin/daily_etl.sh >> /logs/etl.log 2>&1
```

---

## 📖 Learning Path

| Timeline | Focus |
|----------|-------|
| **Week 1-2** | File Operations, Text Processing, Permissions |
| **Week 3-4** | System Admin, Networking, Process Management |
| **Month 2** | Disk Management, Logging, Job Scheduling |
| **Ongoing** | Practice daily until commands become muscle memory |

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md)

Ideas for contributions:
- Add more real-world examples from your work
- Optimize commands for your use case
- Share troubleshooting tips
- Improve explanations

---

## 📋 Command Categories

1. **File & Directory Operations** - Navigate and manipulate files
2. **Text Processing & Searching** - grep, awk, sed for data transformation
3. **Permissions & Ownership** - Secure your data and scripts
4. **Process Management** - Monitor and control running jobs
5. **System Administration** - Manage services and users
6. **Networking** - SSH, SCP, firewalls for remote access
7. **Disk & Storage** - Monitor and manage storage systems
8. **Logging & Monitoring** - Real-time job monitoring
9. **Job Scheduling** - Automate repetitive tasks with cron

---

## 💡 Most Frequently Used Commands

```
10x/day:  ls, cd, cat, tail -f
5x/day:   grep, ssh, ps aux, df -h
2x/day:   chmod, systemctl, find
Daily:    head, awk, cut, sort
Weekly:   crontab, scp, lvcreate
```

---

## ⚠️ Common Pitfalls

- **`rm -rf`** - ALWAYS double-check paths before running
- **`chmod 777`** - Security risk; use 755 or 644 instead
- **`kill -9`** - Use `kill` first, only use `-9` if needed
- **Background jobs** - Use `nohup` to survive logout

---

## 📞 Feedback & Issues

Found an error or have a suggestion? Please open an issue or submit a pull request!

---

## 📄 License

MIT License - Feel free to use, modify, and share.

See [LICENSE](LICENSE) for full details.
