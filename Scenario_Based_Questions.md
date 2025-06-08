


## Scenario: Server Disk Full Suddenly

**Question:**  
A production server suddenly stops responding. You try to SSH but it’s very slow. After logging in, you notice the disk is 100% full. How would you resolve this?

**Answer:**
```bash
df -h
du -sh /* 2>/dev/null | sort -hr | head -10
> /var/log/messages
yum clean all
```

**Explanation:**  
This scenario is common in production. I follow a structured approach—check space, trace file growth, clean or archive. It shows my awareness of file systems, log management, and system recovery.

---

## Scenario: CPU Usage is High

**Question:**  
A developer reports the application is very slow. You suspect high CPU usage. How do you investigate?

**Answer:**
```bash
top
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head
systemctl restart <servicename>
```

**Explanation:**  
I check system metrics using `top`, `ps`, and act based on the issue (e.g., looping process). This reflects hands-on troubleshooting and good decision-making in performance issues.

---

## Scenario: Service Fails to Start

**Question:**  
A web service (e.g., Apache) fails to start on boot. How will you troubleshoot?

**Answer:**
```bash
systemctl status httpd
journalctl -xe
apachectl configtest
netstat -tuln | grep :80
```

**Explanation:**  
I approach this step-by-step: verify the service state, examine logs, validate config, and check port conflicts. It proves structured problem-solving with knowledge of systemd and networking.

---

##  Scenario: User Cannot Login via SSH

**Question:**  
A team member cannot SSH into a server. What steps would you take to resolve the issue?

**Answer:**
```bash
systemctl status sshd
id username
passwd -S username
ls -ld ~/.ssh
ls -l ~/.ssh/authorized_keys
tail -f /var/log/secure
```

**Explanation:**  
This checks for SSH service issues, user account problems, file permissions, and logs. It shows in-depth SSH knowledge and ability to handle real-time access issues securely.

---

##  Scenario: Crontab Not Working

**Question:**  
A scheduled backup script in crontab isn’t running. How do you debug it?

**Answer:**
```bash
crontab -l
systemctl status crond
grep CRON /var/log/cron
# Example cron job with logging
0 1 * * * /path/to/script.sh >> /tmp/backup.log 2>&1
```

**Explanation:**  
I verify cron syntax, service status, and logs. Adding logs to the script helps in debugging silently failing jobs. This shows my command over automation and job scheduling.


---
##  Scenario: Permission Denied When Running a Script

**Question:**  
A user runs a shell script but gets a "Permission denied" error. How would you resolve it?

**Answer:**
```bash
ls -l script.sh
chmod +x script.sh
```

**Explanation:**  
The issue is usually missing execute permission. I use `ls -l` to verify and `chmod +x` to fix. This shows basic but critical knowledge of Linux permissions and script execution.

---

##  Scenario: Port 80 is Already in Use

**Question:**  
You try to start Apache, but it fails because port 80 is already in use. How do you handle this?

**Answer:**
```bash
netstat -tuln | grep :80
lsof -i :80
kill -9 <PID>  # if safe to stop
```

**Explanation:**  
This shows the ability to identify conflicting services using `netstat` and `lsof`, and the judgment to safely terminate processes. It’s a real-world issue in multi-service environments.

---

## Scenario: Root Password Forgotten

**Question:**  
You have physical access to a Linux machine but forgot the root password. How would you reset it?

**Answer:**
1. Reboot the machine.
2. In GRUB menu, edit the boot entry and add:
   ```
   init=/bin/bash
   ```
3. Once in shell:
   ```bash
   mount -o remount,rw /
   passwd root
   exec /sbin/init
   ```

**Explanation:**  
This is a critical recovery scenario. Shows knowledge of boot process, GRUB, single-user mode, and password recovery—great for proving deep system understanding.

---

## Scenario: Swap Memory is Full

**Question:**  
The system is using too much swap memory and becoming slow. What would you do?

**Answer:**
```bash
free -h
swapon --show
top  # check swap-using processes
swapoff -a
swapon -a
```

**Explanation:**  
Demonstrates understanding of virtual memory, how to monitor it, and how to clear swap. You might also investigate the need for more RAM or optimize heavy applications.

---

## Scenario: File Deleted Accidentally – Need Recovery

**Question:**  
A critical file was deleted accidentally from the system. Can it be recovered?

**Answer:**  
- If it's still open by a process:
  ```bash
  lsof | grep deleted
  cp /proc/<pid>/fd/<fd> /recovered_file
  ```
- Otherwise, restore from backup or snapshots (if available).

**Explanation:**  
This scenario shows creative use of `/proc` and `lsof` for emergency recovery. It also highlights the importance of having backup policies in place.

---
```

## Scenario: Find All Failed SSH Login Attempts

**Command Used:** `grep`

**Question:**  
You are asked to find all failed SSH login attempts from the logs. How would you do that?

**Answer:**
```bash
grep "Failed password" /var/log/secure
```

**Explanation:**  
This command filters lines from `/var/log/secure` that show failed login attempts. It's useful for security auditing and shows understanding of system logs and `grep` filtering.

---

## Scenario: Get Only IP Addresses from Failed Logins

**Command Used:** `awk`

**Question:**  
From the failed SSH login entries, how do you extract just the IP addresses?

**Answer:**
```bash
grep "Failed password" /var/log/secure | awk '{print $11}'
```

**Explanation:**  
Here, `awk` is used to print the 11th field (which contains the IP). This scenario shows the power of `awk` in parsing structured text like log files.

---

##  Scenario: Replace a Configuration Parameter in a File

**Command Used:** `sed`

**Question:**  
You need to change `PermitRootLogin no` to `PermitRootLogin yes` in the ssh config. How would you do it?

**Answer:**
```bash
sed -i 's/^PermitRootLogin no/PermitRootLogin yes/' /etc/ssh/sshd_config
```

**Explanation:**  
This demonstrates real-world use of `sed` for in-place editing. It also reflects on secure configuration management, often part of sysadmin and DevOps tasks.

---

## Scenario: Summarize Disk Usage from `df -h` Output

**Command Used:** `awk`

**Question:**  
You want to list all mount points along with their usage percentage. How would you do that?

**Answer:**
```bash
df -h | awk 'NR>1 {print $6, $5}'
```

**Explanation:**  
`awk` is used here to skip the header (`NR>1`) and print mount point (6th field) and usage (5th). This shows how `awk` can be used to filter and format output quickly.

---

## Scenario: Count Occurrences of a Word in a File

**Command Used:** `grep`, `wc`

**Question:**  
You want to know how many times the word "error" appears in a log file. How?

**Answer:**
```bash
grep -i "error" /var/log/messages | wc -l
```

**Explanation:**  
Combining `grep` and `wc` counts the number of matching lines. Shows effective use of piping and log analysis — something interviewers love to hear.

---
## Scenario: Check if Server Was Recently Rebooted

**Command Used:** `uptime`

**Question:**  
How can you check how long a server has been running, or if it was recently rebooted?

**Answer:**
```bash
uptime
```

**Explanation:**  
The `uptime` command shows how long the system has been running, number of users, and load averages. Useful in troubleshooting to confirm if a server was rebooted unexpectedly or recently patched.

---

##  Scenario: Investigate High Load Averages

**Command Used:** `uptime`

**Question:**  
A developer says the server is slow. You suspect high load. How do you confirm it?

**Answer:**
```bash
uptime
```

**Explanation:**  
The load averages at the end of `uptime` output indicate the system load in the last 1, 5, and 15 minutes. High values compared to CPU cores can indicate overuse. Interviewers like candidates who can correlate performance issues with load.

---

##  Scenario: Check Disk Space on All Mounted Filesystems

**Command Used:** `df`

**Question:**  
How do you check disk usage on all file systems in human-readable format?

**Answer:**
```bash
df -h
```

**Explanation:**  
`df -h` gives an overview of disk usage in GB/MB. It's essential for detecting full partitions, especially `/`, `/var`, or `/home`. Commonly used in troubleshooting “disk full” errors.

---

## Scenario: Check Which Directory is Taking Up Most Space

**Command Used:** `du`

**Question:**  
The `/var` partition is nearly full. How do you find out which subdirectory is using the most space?

**Answer:**
```bash
du -sh /var/* | sort -hr | head -10
```

**Explanation:**  
This command summarizes each subdirectory’s size, sorts them in human-readable format, and lists the top 10 largest. Perfect for space audits and finding logs or backups consuming storage.

---

##  Scenario: Check Disk Usage of Current Directory Recursively

**Command Used:** `du`

**Question:**  
You're inside a directory and want to see size of all subfolders recursively. How do you do that?

**Answer:**
```bash
du -h --max-depth=1
```

**Explanation:**  
This shows a readable breakdown of folder sizes one level deep. Very helpful when analyzing which folders are growing in size within applications, backups, or user directories.

---
```
