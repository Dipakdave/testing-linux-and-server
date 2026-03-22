# 🚀 DevOps Environment Setup Assignment

## 👨‍💻 Author

**Dipak Dave**
Fresher DevOps Engineer

---

## 📌 Project Overview

This project demonstrates implementation of core DevOps tasks:

* 📊 System Monitoring
* 👥 User Management & Access Control
* 💾 Automated Backup Configuration

The goal is to create a **secure, monitored, and reliable development environment** for two developers: Sarah and Mike.

---

## 🧰 Tech Stack

* Linux (Ubuntu)
* Bash Scripting
* Cron Jobs
* Apache & Nginx
* htop, df, du

---

# 📊 Task 1: System Monitoring Setup

## ✅ Implementation

* Installed `htop` for monitoring CPU, memory, and processes
* Used `df -h` for disk usage
* Used `du -sh` for directory usage
* Used `ps aux` for identifying high CPU processes

## 📜 Monitoring Script

```bash
#!/bin/bash

echo "===== System Monitoring Report =====" >> /var/log/system_monitor.log
date >> /var/log/system_monitor.log

top -b -n1 | head -10 >> /var/log/system_monitor.log
df -h >> /var/log/system_monitor.log
du -sh /home/* >> /var/log/system_monitor.log
ps aux --sort=-%cpu | head >> /var/log/system_monitor.log
```

---

# 👥 Task 2: User Management & Access Control

## ✅ Users Created

* Sarah
* Mike

## 📁 Workspace Setup

```bash
/home/sarah/workspace
/home/mike/workspace
```

## 🔐 Permissions

```bash
sudo useradd sarah
sudo useradd mike

sudo mkdir -p /home/sarah/workspace
sudo mkdir -p /home/mike/workspace

sudo chown -R sarah:sarah /home/sarah
sudo chown -R mike:mike /home/mike

chmod 700 /home/sarah
chmod 700 /home/mike
```

✔ Ensures only respective users can access their directories

---

## 🔒 Password Policy

```bash
sudo chage -M 30 sarah
sudo chage -M 30 mike
```

* Password expires every 30 days

---

# 💾 Task 3: Backup Configuration

## 📦 Apache Backup Script

```bash
#!/bin/bash

DATE=$(date +%F)

/bin/tar -czvf /backups/apache_backup_$DATE.tar.gz /etc/apache2/ /var/www/html/

echo "Backup Created on $DATE" >> /backups/apache_backup.log

/bin/tar -tzf /backups/apache_backup_$DATE.tar.gz >> /backups/apache_backup.log
```

---

## 📦 Nginx Backup Script

```bash
#!/bin/bash

DATE=$(date +%F)

/bin/tar -czvf /backups/nginx_backup_$DATE.tar.gz /etc/nginx/ /usr/share/nginx/html/

echo "Backup Created on $DATE" >> /backups/nginx_backup.log

/bin/tar -tzf /backups/nginx_backup_$DATE.tar.gz >> /backups/nginx_backup.log
```

---

## ⏰ Cron Jobs

```bash
0 0 * * 2 /root/assignment/apache_backup.sh
0 0 * * 2 /root/assignment/nginx_backup.sh
```

* Runs every **Tuesday at 12:00 AM**

---

## 📂 Output

Backups stored in:

```bash
/backups/
```

Example:

```bash
apache_backup_2026-03-21.tar.gz
nginx_backup_2026-03-21.tar.gz
```

---

## ✔️ Verification

```bash
tar -tzf /backups/apache_backup_YYYY-MM-DD.tar.gz
```

Ensures backup integrity

---

# 📸 Screenshots

Add screenshots in `/screenshots` folder:

* htop output
* df -h
* du command
* user creation
* permissions
* password policy
* cron jobs
* backup files
* verification

---

# ⚠️ Challenges Faced

* Apache path issue (`/etc/httpd` vs `/etc/apache2`)
* Cron command typo (`cronetab`)
* GitHub SSH permission issue

✔ All issues were resolved successfully

---

# 🎯 Conclusion

Successfully implemented:

* System Monitoring
* Secure Use
s