# Linux Commands Guide for Data Engineers

Essential Linux commands for data engineers - 100+ commands with real-world examples.

**Author:** Vishnu Vardhan A | Senior Data Engineer  
**Updated:** November 2024  
**License:** MIT

---

## Quick Navigation

| Category | Purpose |
|----------|---------|
| File Operations | Navigate and manage files |
| Text Processing | grep, awk, sed for data transformation |
| Permissions | chmod, chown for security |
| Processes | ps, top, kill for job monitoring |
| System Admin | systemctl, yum, usermod for management |
| Networking | ssh, scp, firewall for remote access |
| Disk & Storage | df, du, mount for storage |
| Logging | tail, journalctl for monitoring |
| Job Scheduling | crontab for automation |

---

## Full Guide

👉 **Read the complete guide:** [COMMANDS.md](COMMANDS.md)

Includes:
- 100+ essential commands with examples
- Real-world data engineering use cases
- Performance optimization tips
- Troubleshooting checklist
- 4-week learning path

---

## Quick Examples

Monitor ETL job:
```bash
tail -f /var/log/etl_job.log
```

Count errors:
```bash
grep "ERROR" app.log | wc -l
```

Check disk space:
```bash
df -h /data
```

Schedule daily job:
```bash
0 2 * * * /usr/local/bin/daily_etl.sh
```

---

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md)

---

## License

MIT License - See [LICENSE](LICENSE) for details
