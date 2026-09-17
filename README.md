https://roadmap.sh/projects/server-stats

# 🖥️ Server Performance Stats

A beginner-friendly **Linux Bash/Shell scripting project** that analyzes basic server performance statistics.

The `server-stats.sh` script can be executed on a Linux server to quickly view CPU usage, memory usage, disk usage, and the top processes consuming CPU and memory resources.

---

## 📌 Project Overview

System administrators and DevOps engineers regularly need to check server health and identify resource-intensive processes.

Instead of manually running multiple Linux commands such as `top`, `free`, `df`, and `ps`, this project combines them into a single Bash script.

### 🎯 Goal

Create a portable Bash script:

```text
server-stats.sh
```

that provides a quick overview of Linux server performance.

---

## 🚀 Features

The script provides the following information:

* ✅ Total CPU usage
* ✅ Total memory usage
* ✅ Free memory
* ✅ Used memory
* ✅ Memory usage percentage
* ✅ Total disk usage
* ✅ Free disk space
* ✅ Used disk space
* ✅ Disk usage percentage
* ✅ Top 5 processes by CPU usage
* ✅ Top 5 processes by memory usage

### ⭐ Stretch Goals

Additional server information can optionally be displayed:

* Operating system information
* Kernel version
* Server hostname
* Server uptime
* Load average
* Logged-in users
* Failed login attempts
* Running services
* Network information

---

# 🏗️ Project Structure

```text
server-performance-stats/
│
├── server-stats.sh
│
└── README.md
```

---

# 🛠️ Technologies Used

| Technology | Purpose               |
| ---------- | --------------------- |
| Linux      | Operating System      |
| Bash       | Shell scripting       |
| `top`      | CPU information       |
| `free`     | Memory information    |
| `df`       | Disk information      |
| `ps`       | Process information   |
| `awk`      | Text processing       |
| `grep`     | Filtering             |
| `sed`      | Text manipulation     |
| `uptime`   | System uptime         |
| `who`      | Logged-in users       |
| `uname`    | OS/kernel information |

---

# 💻 Requirements

You need:

* Linux server
* Bash
* Standard Linux utilities

Tested on common Linux distributions such as:

```text
Ubuntu
Amazon Linux
Debian
CentOS/RHEL
```

---

# ⚙️ Installation

## 1. Clone the repository

```bash
git clone https://github.com/<YOUR-USERNAME>/server-performance-stats.git
```

Move into the project:

```bash
cd server-performance-stats
```

---

## 2. Check the script

```bash
ls -l
```

Expected:

```text
README.md
server-stats.sh
```

---

## 3. Make the script executable

```bash
chmod +x server-stats.sh
```

Verify:

```bash
ls -l server-stats.sh
```

You should see executable permissions:

```text
-rwxr-xr-x
```

---

# ▶️ Run the Script

Execute:

```bash
./server-stats.sh
```

Or:

```bash
bash server-stats.sh
```

---

# 📊 Sample Output

Example:

```text
========================================
       SERVER PERFORMANCE STATS
========================================

Hostname:
ip-172-31-20-91

Operating System:
Ubuntu 24.04 LTS

Kernel:
6.8.0-xx-generic

----------------------------------------
CPU USAGE
----------------------------------------

Total CPU Usage: 18%

----------------------------------------
MEMORY USAGE
----------------------------------------

Total Memory : 7.6 GB
Used Memory  : 2.4 GB
Free Memory  : 5.2 GB
Usage        : 31%

----------------------------------------
DISK USAGE
----------------------------------------

Filesystem      Size  Used Avail Use%
/               30G   10G   20G  34%

----------------------------------------
TOP 5 PROCESSES BY CPU
----------------------------------------

PID      USER       CPU%    MEM%    COMMAND
1234     root       25.4    2.1     java
2234     ubuntu     12.8    1.4     node
3234     root        8.5    0.8     nginx
4234     ubuntu      5.2    0.6     python
5234     root        3.7    0.4     dockerd

----------------------------------------
TOP 5 PROCESSES BY MEMORY
----------------------------------------

PID      USER       CPU%    MEM%    COMMAND
1234     root        2.1   15.4     java
2234     ubuntu      1.4    8.2     node
3234     root        0.8    5.4     postgres
4234     ubuntu      0.6    4.8     python
5234     root         0.4    3.7     dockerd

========================================
       END OF REPORT
========================================
```

---

# 🔍 Linux Commands Used

## CPU Usage

The script can use:

```bash
top
```

or:

```bash
mpstat
```

to determine CPU utilization.

Example:

```bash
top -bn1
```

The `-b` option runs `top` in batch mode and `-n1` takes one iteration.

---

## Memory Usage

Use:

```bash
free -h
```

Example:

```text
               total        used        free
Mem:            7.6Gi       2.4Gi       5.2Gi
```

The `-h` option displays human-readable values.

---

## Disk Usage

Use:

```bash
df -h
```

Example:

```text
Filesystem      Size  Used Avail Use%
/               30G   10G   20G  34%
```

---

## Top CPU Processes

Use:

```bash
ps aux --sort=-%cpu | head
```

This sorts processes based on CPU consumption.

For the top 5 processes:

```bash
ps aux --sort=-%cpu | head -n 6
```

The first line is the header.

---

## Top Memory Processes

Use:

```bash
ps aux --sort=-%mem | head -n 6
```

This displays the processes consuming the most memory.

---

# ⭐ Stretch Goals

## 1. Server Uptime

```bash
uptime
```

Example:

```text
10:30:20 up 15 days, 4:32, 2 users
```

---

## 2. Load Average

```bash
uptime
```

Example:

```text
load average: 0.42, 0.37, 0.29
```

These values represent approximately:

```text
1 minute
5 minutes
15 minutes
```

---

## 3. Logged-in Users

```bash
who
```

or:

```bash
users
```

---

## 4. Operating System Information

```bash
cat /etc/os-release
```

---

## 5. Kernel Version

```bash
uname -r
```

---

## 6. Hostname

```bash
hostname
```

---

## 7. Failed Login Attempts

On systems using `journalctl`:

```bash
sudo journalctl | grep -i "failed"
```

On systems using `/var/log/auth.log`:

```bash
sudo grep "Failed password" /var/log/auth.log
```

On RHEL/Amazon Linux systems, authentication logs may be available in:

```bash
/var/log/secure
```

Example:

```bash
sudo grep "Failed password" /var/log/secure
```

---

# 🧪 Testing

Test the script:

```bash
bash -n server-stats.sh
```

This checks Bash syntax without executing the script.

You can also run:

```bash
shellcheck server-stats.sh
```

if ShellCheck is installed.

---

# 🔐 Permissions

Make the script executable:

```bash
chmod +x server-stats.sh
```

Run:

```bash
./server-stats.sh
```

Some optional statistics may require `sudo`.

For example:

```bash
sudo ./server-stats.sh
```

Avoid running the entire script as root unless necessary.

---

# 📈 DevOps Use Case

This project demonstrates how Bash scripting can automate routine server administration tasks.

A DevOps engineer can use similar scripts to quickly investigate:

```text
High CPU
   ↓
Check CPU usage
   ↓
Identify top CPU process
   ↓
Check application logs
   ↓
Investigate process
```

For memory:

```text
High Memory
   ↓
Check free -h
   ↓
Identify top memory process
   ↓
Check application
   ↓
Restart / optimize / scale
```

For disk:

```text
Disk Alert
   ↓
df -h
   ↓
Identify full filesystem
   ↓
du -sh
   ↓
Find large files/directories
   ↓
Clean logs / increase storage
```

---

# 🏢 Production-Level Extension

The basic project can be extended into a production monitoring solution.

```text
                 Linux Server
                      |
              server-stats.sh
                      |
          +-----------+-----------+
          |           |           |
         CPU        Memory       Disk
          |           |           |
          +-----------+-----------+
                      |
                  Report
                      |
                 Log File
                      |
                Cron / Systemd
                      |
              Monitoring System
```

Possible improvements:

* Generate timestamped reports
* Store historical metrics
* Configure CPU thresholds
* Configure memory thresholds
* Configure disk thresholds
* Send email alerts
* Send Slack/Telegram notifications
* Run automatically with cron
* Export metrics
* Integrate with Prometheus
* Create Grafana dashboards

---

# ⏰ Cron Automation

The script can be scheduled using cron.

Edit crontab:

```bash
crontab -e
```

Example: run every 5 minutes:

```cron
*/5 * * * * /home/ec2-user/server-performance-stats/server-stats.sh >> /home/ec2-user/server-performance-stats/server-stats.log 2>&1
```

Check cron jobs:

```bash
crontab -l
```

---

# 📝 Learning Objectives

After completing this project, you should understand:

### Linux

* CPU monitoring
* Memory monitoring
* Disk monitoring
* Process monitoring
* Linux system commands

### Bash

* Variables
* Commands
* Command substitution
* Pipes
* Redirection
* `if` conditions
* Loops
* Functions
* `awk`
* `grep`
* `sed`

### DevOps

* Server health checks
* Troubleshooting
* Automation
* Log collection
* Cron jobs
* Basic incident investigation

---

# 🎯 Interview Questions

## 1. How do you check CPU usage?

```bash
top
```

or:

```bash
mpstat
```

---

## 2. How do you check memory?

```bash
free -h
```

---

## 3. How do you check disk usage?

```bash
df -h
```

---

## 4. How do you find the process consuming the highest CPU?

```bash
ps aux --sort=-%cpu | head
```

---

## 5. How do you find the process consuming the highest memory?

```bash
ps aux --sort=-%mem | head
```

---

## 6. What is the difference between `df` and `du`?

```text
df
 ↓
Filesystem-level disk usage
```

```text
du
 ↓
Directory/file-level disk usage
```

Examples:

```bash
df -h
```

and:

```bash
du -sh /var/log/*
```

---

## 7. How would you troubleshoot a server with high CPU?

A typical investigation:

```text
Check CPU
   ↓
Identify process
   ↓
Check process details
   ↓
Check application logs
   ↓
Check traffic/load
   ↓
Identify root cause
   ↓
Take corrective action
   ↓
Monitor again
```

---

# 🔄 Future Improvements

This project can later be upgraded to:

### Version 1

```text
Basic Bash Server Stats
```

### Version 2

```text
Server Stats + Threshold Alerts
```

### Version 3

```text
Server Stats + Cron + Logging
```

### Version 4

```text
Server Monitoring + Email/Telegram Alerts
```

### Version 5

```text
Prometheus + Grafana + AlertManager
```

This creates a natural progression from **Linux/Bash beginner project → production monitoring project**.

---

# 📚 Useful Commands

```bash
top
htop
free -h
df -h
du -sh
ps aux
uptime
who
hostname
uname -a
cat /etc/os-release
systemctl status
journalctl
```

---

# 👨‍💻 Project Skills

```text
Linux
Bash
Shell Scripting
CPU Monitoring
Memory Monitoring
Disk Monitoring
Process Management
System Administration
Troubleshooting
Cron
Automation
DevOps
```

---

# 🏁 Conclusion

The **Server Performance Stats** project is a practical introduction to Linux system administration and Bash automation.

It demonstrates how a DevOps engineer can combine standard Linux commands into an automated script to quickly understand server health and identify resource-intensive processes.

The project can be further extended into a complete monitoring solution using:

```text
Bash
  ↓
Cron
  ↓
Logs
  ↓
Prometheus
  ↓
Grafana
  ↓
AlertManager
```

---

## 📌 Repository

Repository name:

```text
server-performance-stats
```

Suggested GitHub description:

```text
A Bash script to analyze Linux server CPU, memory, disk usage, and top resource-consuming processes.
```

Suggested topics:

```text
linux
bash
shell-scripting
devops
server-monitoring
linux-administration
system-monitoring
automation
cpu-monitoring
memory-monitoring
disk-monitoring
```


This Bash script displays:

- CPU Usage
- Memory Usage
- Disk Usage
- Top 5 CPU Processes
- Top 5 Memory Processes
