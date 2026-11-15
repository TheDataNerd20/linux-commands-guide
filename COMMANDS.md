# Linux Commands Guide for Data Engineers

A comprehensive reference for essential Linux commands used in data engineering. Master these commands and you'll be 10x more productive on the job.

---

## Table of Contents

1. [File & Directory Operations](#1-file--directory-operations)
2. [Text Processing & Searching](#2-text-processing--searching)
3. [Permissions & Ownership](#3-permissions--ownership)
4. [Process Management](#4-process-management)
5. [System Administration](#5-system-administration)
6. [Networking](#6-networking)
7. [Disk & Storage](#7-disk--storage)
8. [Logging & Monitoring](#8-logging--monitoring)
9. [Job Scheduling](#9-job-scheduling)
10. [Quick Reference](#quick-reference)

---

## 1. File & Directory Operations

### Navigation
```bash
pwd                          # Print working directory
ls                          # List files
ls -la                      # List all with details
ls -lh                      # List with human-readable sizes
cd /path/to/directory       # Change directory
cd ~                        # Go to home directory
cd -                        # Go back to previous directory
```

### Create & Remove
```bash
mkdir folder_name           # Create directory
mkdir -p a/b/c             # Create nested directories
touch filename.txt         # Create empty file
rmdir folder_name          # Remove empty directory
rm filename                # Delete file
rm -rf folder_name         # Delete directory with contents (careful!)
```

### Copy & Move
```bash
cp file1 file2             # Copy file
cp -r folder1 folder2      # Copy directory recursively
mv file1 file2             # Move/rename file
mv folder1 folder2         # Move/rename directory
```

### View Contents
```bash
cat filename               # Display entire file
head -20 filename          # Show first 20 lines
tail -20 filename          # Show last 20 lines
tail -f logfile            # Follow log in real-time
wc -l filename             # Count lines
```

### Real-World Examples
```bash
# Preview CSV file
head -5 /data/raw/sales.csv

# Monitor ETL log
tail -f /var/log/etl_job.log

# Count records in data file
wc -l transactions.csv

# Copy backup
cp -r /data/warehouse /backup/warehouse_$(date +%Y%m%d)
```

---

## 2. Text Processing & Searching

### Grep - Search Patterns
```bash
grep "pattern" filename              # Search for pattern
grep -i "pattern" filename           # Case insensitive
grep -v "pattern" filename           # Invert (exclude)
grep -c "pattern" filename           # Count matches
grep "error" *.log                   # Search multiple files
grep -n "pattern" filename           # Show line numbers
```

### Awk - Data Processing
```bash
awk '{print $1}' file                # Print first column
awk -F',' '{print $2}' file.csv     # Use delimiter
awk '{sum += $3} END {print sum}' file    # Sum column
awk '{print NR, $0}' file            # Add line numbers
```

### Sed - Stream Editor
```bash
sed 's/old/new/' file               # Replace first occurrence
sed 's/old/new/g' file              # Replace all
sed -i 's/old/new/g' file           # In-place edit
sed '5d' file                        # Delete line 5
```

### Other Tools
```bash
cut -d',' -f1,3 file.csv            # Extract specific columns
sort file.txt                        # Sort lines
sort -rn file                        # Reverse numeric sort
uniq file                            # Remove duplicates (must be sorted)
tr ',' '|' file                      # Replace delimiter
```

### Real-World Examples
```bash
# Count errors in log
grep "ERROR" app.log | wc -l

# Extract and sum values
awk -F',' '{sum += $3} END {print "Total: " sum}' transactions.csv

# Find and process files
find /data -name "*.csv" | xargs wc -l

# Remove duplicates
sort data.csv | uniq > unique_data.csv

# Replace values
sed 's/NULL//g' messy_data.csv > clean_data.csv
```

---

## 3. Permissions & Ownership

### Change Permissions
```bash
chmod 755 script.sh                  # rwx for owner, rx for others
chmod 644 file.txt                   # rw for owner, r for others
chmod 600 credentials.txt            # rw for owner only
chmod u+x script.sh                  # Add execute to owner
chmod -R 755 folder/                 # Recursive change
```

### Change Ownership
```bash
chown user filename                  # Change owner
chown user:group filename            # Change owner and group
chown -R datauser /data/warehouse    # Recursive change
```

### View Permissions
```bash
ls -l filename                       # View permissions
ls -la folder/                       # View all files with permissions
```

### Real-World Examples
```bash
# Protect sensitive files
chmod 600 /etc/database_credentials.txt

# Make script executable
chmod +x deploy.sh

# Change data directory ownership
chown -R datauser:datagroup /data/

# Set directory permissions for sharing
chmod 775 /data/shared/
```

---

## 4. Process Management

### View Processes
```bash
ps aux                               # List all processes
ps lax                               # Long format listing
top                                  # Real-time monitoring (Shift+P=CPU, Shift+M=Memory)
htop                                 # Better version of top
uptime                               # System load and uptime
```

### Control Processes
```bash
kill PID                             # Terminate process
kill -9 PID                          # Force kill
killall processname                  # Kill all instances
pkill -f "pattern"                   # Kill by pattern
nice -n 10 command                   # Start with low priority
renice -n 15 -p PID                  # Change priority
nohup command &                      # Run in background (survives logout)
```

### Background Jobs
```bash
command &                            # Run in background
jobs                                 # List background jobs
fg %1                                # Bring job 1 to foreground
bg %1                                # Resume job 1 in background
Ctrl+Z                               # Pause current job
```

### Real-World Examples
```bash
# Monitor Spark job
ps aux | grep spark

# Check memory usage during job
top -b -n 1 | head -20

# Run heavy job with low priority
nice -n 10 python heavy_computation.py

# Run ETL job that survives logout
nohup python etl_pipeline.py > etl.log 2>&1 &

# Kill stuck job
kill -9 12345
```

---

## 5. System Administration

### Service Management
```bash
sudo systemctl start postgresql      # Start service
sudo systemctl stop postgresql       # Stop service
sudo systemctl restart postgresql    # Restart service
sudo systemctl enable postgresql     # Auto-start on boot
sudo systemctl status postgresql     # Check status
sudo systemctl disable service       # Disable service
journalctl -u postgresql -n 50      # View service logs
```

### Package Management (RedHat/CentOS)
```bash
yum install package-name             # Install
yum update                            # Update packages
yum search keyword                    # Search
yum remove package-name               # Remove
```

### User Management
```bash
useradd username                     # Create user
usermod -aG groupname username       # Add user to group
userdel username                     # Delete user
passwd username                      # Change password
sudo visudo                          # Edit sudo permissions
```

### Real-World Examples
```bash
# Restart database after config change
sudo systemctl restart postgresql

# Install Python development tools
yum install python3-devel

# Give Hadoop access to user
usermod -aG hdfs datauser

# Auto-start Spark on reboot
sudo systemctl enable spark-master
```

---

## 6. Networking

### Remote Access
```bash
ssh user@hostname                    # SSH login
ssh -i keyfile.pem user@host        # Use private key
ssh -p 2222 user@host               # Custom port
ssh -v user@host                    # Verbose output
scp file user@host:/path/           # Secure copy to remote
scp user@host:/path/file .          # Secure copy from remote
sftp user@host                       # Interactive file transfer
```

### Network Information
```bash
ping hostname                        # Test connectivity
ip address show                      # Show IP addresses
hostname                             # Show hostname
hostnamectl set-hostname newname     # Change hostname
netstat -tuln                        # Show listening ports
ss -tuln                             # Newer alternative
```

### Firewall
```bash
firewall-cmd --list-all              # View rules
firewall-cmd --permanent --add-port=5432/tcp    # Open port
firewall-cmd --reload                # Reload firewall
```

### Real-World Examples
```bash
# SSH to production database
ssh -i ~/.ssh/prod_key.pem ubuntu@db.prod.example.com

# Copy data to remote server
scp large_dataset.csv user@warehouse.example.com:/data/

# Test database connectivity
ping database.internal.example.com

# Open port for Spark UI
sudo firewall-cmd --permanent --add-port=8080/tcp
```

---

## 7. Disk & Storage

### Disk Usage
```bash
df -h                                # Disk free space
df -h /data                          # Specific partition
du -h folder                         # Disk usage per folder
du -sh /data                         # Total folder size
du -sh /* | sort -rh | head -10     # Top 10 largest dirs
```

### Storage Management
```bash
lsblk                                # List block devices
mount /dev/sda1 /data               # Mount partition
umount /data                         # Unmount
nano /etc/fstab                     # Edit mount table
```

### Logical Volume Management
```bash
pvs                                  # Physical volumes
vgs                                  # Volume groups
lvs                                  # Logical volumes
lvcreate -L 10G -n lv_data vg_stor  # Create volume
lvextend -L +5G /dev/vg_stor/lv_data # Extend volume
```

### Real-World Examples
```bash
# Check disk space
df -h /data

# Find largest tables
du -sh /warehouse/* | sort -rh

# Mount new storage
mount /dev/sdb1 /mnt/new_data

# Extend data volume
lvextend -L +100G /dev/vg_data/lv_warehouse
```

---

## 8. Logging & Monitoring

### View Logs
```bash
tail -f /var/log/app.log            # Follow log in real-time
tail -100 /var/log/syslog           # Last 100 lines
head -50 /var/log/app.log           # First 50 lines
grep "ERROR" /var/log/app.log       # Find errors
journalctl -u service -n 100        # Service logs
```

### System Information
```bash
uptime                               # Load and uptime
vmstat 1 5                           # Virtual memory (5 samples)
iostat -x 1                          # I/O statistics
free -h                              # Memory usage
dmesg | tail -50                     # Kernel messages
```

### Real-World Examples
```bash
# Monitor Spark job
tail -f /var/log/spark/job.log

# Find database errors in last hour
journalctl -u postgres --since "1 hour ago" | grep ERROR

# Check if system is memory bottlenecked
vmstat 1 10

# Follow application during deployment
tail -f /var/log/deployment.log
```

---

## 9. Job Scheduling

### Cron Jobs
```bash
crontab -e                           # Edit cron jobs
crontab -l                           # List cron jobs
```

### Cron Syntax
```
minute hour day month weekday command
0      2    *   *     *       /scripts/daily_etl.sh
0      */4  *   *     *       python sync_data.py
30     23   *   *     0       backup_db.sh
```

### Examples
```bash
# Run daily ETL at 2 AM
0 2 * * * /usr/local/bin/daily_etl.sh >> /logs/etl.log 2>&1

# Sync data every 6 hours
0 */6 * * * python /scripts/sync_external_data.py

# Monthly report on 1st day at midnight
0 0 1 * * /scripts/monthly_report.sh

# Capture both output and errors
0 3 * * * /scripts/backup.sh > /var/log/backup.log 2>&1
```

---

## 10. Pipes & Redirection (Essential Patterns)

### Redirection
```bash
command > file                       # Redirect to file (overwrite)
command >> file                      # Append to file
command 2> error.log                 # Redirect errors
command > output.log 2>&1            # Both output and errors
```

### Piping
```bash
command1 | command2                  # Pipe output
grep "pattern" file | wc -l          # Count matches
cat file | sort | uniq               # Unique lines
ps aux | grep python | wc -l         # Count Python processes
```

### Real-World Examples
```bash
# Save output and errors
python etl.py > output.log 2>&1

# Process and count
grep "ERROR" app.log | wc -l

# Complex pipeline
cat /data/*.csv | sort | uniq | wc -l

# Find and process
find /data -name "*.csv" | xargs wc -l
```

---

## Quick Reference

### Most Used Commands (Frequency)

| Frequency | Command | Purpose |
|-----------|---------|---------|
| **10x/day** | `ls`, `cd`, `cat`, `tail -f` | Navigation & viewing |
| **5x/day** | `grep`, `ssh`, `ps aux`, `df -h` | Search, access, monitor |
| **2x/day** | `chmod`, `systemctl`, `find` | Permissions, services |
| **Daily** | `head`, `awk`, `cut`, `sort` | Data processing |
| **Weekly** | `crontab`, `scp`, `lvcreate` | Scheduling, transfer |

---

## Essential Directories

```
/opt/              # Optional software (Spark, Hadoop)
/data/             # Data storage
/var/log/          # Logs
/home/username/    # User home
/tmp/              # Temporary files
/etc/              # Configuration files
/mnt/              # Mount points
```

---

## Troubleshooting Checklist

When something goes wrong, check:

```bash
# Disk space
df -h /data

# Memory
free -h

# CPU load
uptime

# Processes
ps aux | grep processname

# Network
ping host

# Logs
tail -100 /var/log/app.log

# Services
systemctl status service-name
```

---

## Learning Path

**Week 1-2:** Master File Operations, Text Processing, Permissions  
**Week 3-4:** System Admin, Networking, Process Management  
**Month 2:** Disk Management, Logging, Job Scheduling  
**Ongoing:** Practice daily until commands become muscle memory

---

**Author:** Vishnu Vardhan A | Senior Data Engineer  
**Last Updated:** November 2024  
**License:** MIT
