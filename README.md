# Linux Commands Guide for Data Engineers

**A production-ready reference for 100+ essential Linux commands used in data engineering.**

---

## 📖 Complete Guide

See **[COMMANDS.md](COMMANDS.md)** for the full guide containing:

- **File Operations** - ls, cd, cp, mv, rm, touch, mkdir
- **Text Processing** - grep, awk, sed, cut, tr, sort, uniq  
- **Permissions** - chmod, chown, sudo
- **Process Management** - ps, top, kill, nice, nohup
- **System Administration** - systemctl, yum, useradd, usermod
- **Networking** - ssh, scp, sftp, firewall-cmd, ping
- **Disk & Storage** - df, du, mount, fdisk, lvm
- **Logging & Monitoring** - tail, journalctl, vmstat, iostat
- **Job Scheduling** - crontab

---

## 🚀 Quick Examples

```bash
# Monitor ETL log
tail -f /var/log/etl_job.log

# Count errors
grep "ERROR" app.log | wc -l

# Check disk space  
df -h /data

# Run background job
nohup python script.py > output.log 2>&1 &

# Schedule daily task at 2 AM
0 2 * * * /usr/local/bin/daily_job.sh
```

---

## 👤 Author

Vishnu Vardhan A | Senior Data Engineer

## 📄 License

MIT License - See [LICENSE](LICENSE)

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md)
