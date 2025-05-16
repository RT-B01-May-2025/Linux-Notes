## 🖥️ `uptime`
**Purpose:** Shows how long the system has been running and the load average.

```bash
uptime
```
**Use case:** Check system stability and performance over time.

> Load average: `0.08, 0.15, 0.16` represent the system load over 1, 5, and 15 minutes.
---

# 🖥️ `top` Command in Linux

The `top` (table of processes)  command shows a dynamic , **real-time view** of running processes, resource utilization including CPU and memory usage, and performance metrics.

---

## ✅ **Basic Usage**

```bash
top
```

- Launches the interactive interface showing live CPU, memory, and task information.

---

## 📊 **Understanding the Output**

When you run `top`, you'll see something like:

```
top - 14:21:58 up 3 days,  1:00,  2 users,  load average: 0.10, 0.20, 0.15
Tasks: 150 total,   2 running, 148 sleeping,   0 stopped,   0 zombie
%Cpu(s):  5.0 us,  1.2 sy,  0.0 ni, 93.5 id,  0.2 wa,  0.0 hi,  0.1 si,  0.0 st
MiB Mem :   7853.9 total,   1532.1 free,   2653.2 used,   3668.6 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.   4332.6 avail Mem 
```

### Header Breakdown:

- **Load average**: System load over 1, 5, and 15 minutes.
- **Tasks**: Total number of processes and their states.
- **CPU(s)**: Breakdown of CPU usage (us = user, sy = system, id = idle, wa = waiting for I/O).
- **Memory/Swap**: RAM and swap usage statistics.

## ⚙️ Commonly Used Options

```bash
top -option
```

| Option | Description |
|--------|-------------|
| `-d <secs>` | Delay between updates (e.g., `top -d 2`) |
| `-p <pid>` | Monitor a specific process ID |
| `-n <num>` | Number of updates before top exits |
| `-u <user>` | Show processes for a specific user |
| `-b`        | Batch mode (non-interactive, useful for scripting) |
| `-c`        | Show full command path |

---

## 🖱️ Interactive Commands (within `top`)

| Key | Action |
|-----|--------|
| `P` | Sort by CPU usage |
| `M` | Sort by Memory usage |
| `T` | Sort by time (running time) |
| `k` | Kill a process (enter PID) |
| `r` | Renice a process |
| `h` | Help |
| `q` | Quit `top` |

---

## 🧪 Examples

1. **Monitor a single process using PID**:
   ```bash
   top -p <PID>
   ```


2. **Update every 3 seconds**:
   ```bash
   top -d 3
   ```

3. **View processes of a specific user**:
   ```bash
   top -u <usernmae>
   ```

---

## 📎 Use Cases

- **Diagnose high CPU or memory usage**
- **Monitor server performance**
- **Identify zombie or stuck processes**
- **Script resource usage reporting**

---

# 🖥️ `free` Command in Linux
The `free` command in Linux is used to **display information about the system's memory usage** — including **RAM and swap memory** — in a simple and readable format.

---

## 🔹 Syntax
```bash
free [options]
```

---

## 🔹 Key Fields Explained

When you run `free`, you'll see output like this:
```bash
              total        used        free      shared  buff/cache   available
Mem:        16384256     8204096     2125824      562432     6044336    7438432
Swap:        2097148      102400     1994748
```

### ✅ Breakdown of columns:

| Column       | Meaning |
|--------------|---------|
| `total`      | Total installed memory (RAM or Swap). |
| `used`       | Memory currently used (total - free - buffers/cache). |
| `free`       | Unused memory (not in use at all). |
| `shared`     | Memory used by tmpfs (shared between processes). |
| `buff/cache` | Memory used by kernel buffers and cache. |
| `available`  | Estimated memory available for starting new applications, without swapping. |

---

## 🔹 Common Options

| Option | Description |
|--------|-------------|
| `-h`   | Human-readable (e.g., shows memory in MB/GB). |
| `-m`   | Display in megabytes. |
| `-g`   | Display in gigabytes. |
| `-b`   | Display in bytes. |
| `-s N`| Continuously show memory usage every N seconds. |
| `-t`   | Show the total of physical RAM + swap. |
| `--si`| Use powers of 1000 instead of 1024 (e.g., MB vs MiB). |

---

## 🔹 Examples

### 1. Basic Usage
```bash
free
```

---

### 2. Human-Readable Format
```bash
free -h
```

---

### 3. Update Every 5 Seconds
```bash
free -h -s 5
```

---

### 4. Display in Megabytes
```bash
free -m
```

---

### 5. Include Total Memory + Swap
```bash
free -h -t
```

---

## 🔹 Real-Time Use Cases

- 🧠 **Monitoring system performance**: Check memory pressure when your system is slow.
- 📉 **Debugging applications**: See how much memory an app is consuming in real time.
- 💾 **Managing swap usage**: Identify if swap is being overused (which is slower than RAM).
- 📈 **Scripts & automation**: Use in monitoring scripts to send alerts when memory is low.

---

# 🖥️ `df`  Command in Linux

The `df` command in Linux is used to **display disk space usage** of file systems. It shows the amount of total, used, and available space on the mounted file systems in a system.

---

## 🔧 Syntax:
```bash
df [OPTION]... [FILE]...
```

---

## 📌 Common Options and Their Uses:

| Option        | Description |
|---------------|-------------|
| `-h`          | Human-readable format (e.g., GB, MB) |
| `-a`          | Includes pseudo, duplicate, and inaccessible file systems |
| `-T`          | Shows file system type |
| `-i`          | Displays inode usage instead of block usage |
| `--total`     | Displays a grand total of all file systems |
| `-x` TYPE     | Excludes specific file system type |
| `--output`    | Customize the output columns |

---

## 📘 Examples:

### 1. Basic Usage
```bash
df
```
Shows disk space in blocks (default format).

### 2. Human-readable Format
```bash
df -h
```
Displays sizes in **KB/MB/GB**.
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   25G   23G  53% /
```

### 3. Display File System Type
```bash
df -T
```
Adds the file system type column.

### 4. Check Inodes Usage
```bash
df -i
```
Useful for checking inode depletion.

### 5. Total Disk Usage of All File Systems
```bash
df -h --total
```

### 6. Exclude File System Types
```bash
df -x tmpfs -x devtmpfs
```
Excludes temporary file systems.

### 7. Specific File or Directory
```bash
df -h /home
```
Shows disk usage of the file system where `/home` resides.

---

## 📈 Use Cases:

- Monitor disk space to avoid “disk full” errors.
- Check space before and after software installation or data copy.
- Identify partitions consuming excessive disk space.
- Troubleshoot application issues due to full partitions.

---
# 🖥️ `du`  Command in Linux

The `du` command in Linux stands for **Disk Usage**. It is used to **estimate the amount of disk space used by files and directories**. This command is very useful when you want to find out which directories are consuming the most space on your system.

---

## 🔧 Syntax
```bash
du [OPTION]... [FILE]...
```

---

## 📌 Commonly Used Options

| Option       | Description |
|--------------|-------------|
| `-h`         | Human-readable format (e.g., KB, MB, GB) |
| `-s`         | Summary: display only the total size |
| `-a`         | Show sizes for all files and directories |
| `-c`         | Display a grand total |
| `--max-depth=N` | Limit the depth of directory traversal |
| `-d N`       | Similar to `--max-depth=N` |
| `--apparent-size` | Show actual file sizes rather than disk blocks |

---

## 📂 Examples

### 1. 🔍 Show disk usage of current directory
```bash
du
```

### 2. 📏 Human-readable sizes
```bash
du -h
```

### 3. 📄 List usage of all files and directories
```bash
du -ah
```

### 4. 🧮 Show only the total size of a directory
```bash
du -sh /home/user
```

### 5. 🧾 Total size of each subdirectory (depth = 1)
```bash
du -h --max-depth=1 /var
```

### 6. 🧠 Show grand total
```bash
du -ch /etc
```

---

## 🎯 Use Cases

1. **Identify large directories:**
   ```bash
   du -h --max-depth=1 /
   ```
   Helps locate directories taking up the most space.

2. **Monitor disk usage for specific projects or folders.**

3. **Combine with sort to find largest folders:**
   ```bash
   du -h --max-depth=1 | sort -hr | head -n 10
   ```

4. **Useful in shell scripts for space monitoring.**

---
# 📅 `date` Command in Linux

The `date` command is used to **display** and **set the system date and time** in Linux. It's useful for logging, backups, scripts, and scheduling.

---

## 🔹 Basic Syntax

```bash
date [OPTION]... [+FORMAT]
```

---

## 🔹 Common Use Cases

| Use Case                           | Command                         | Description                                      |
|-----------------------------------|----------------------------------|--------------------------------------------------|
| Display current date and time     | `date`                          | Shows system date and time.                     |
| Custom date format                | `date "+%d-%m-%Y"`              | Prints date in `DD-MM-YYYY` format.             |
| Display only time                 | `date "+%T"`                    | Displays current time as `HH:MM:SS`.            |
| Display yesterday’s date          | `date --date="yesterday"`      | Shows the date of the previous day.             |
| Future or past date               | `date --date="2 weeks ago"`    | Displays date two weeks ago.                    |

---

## 🔹 Format Specifiers

| Format | Meaning                            | Example Output |
|--------|------------------------------------|----------------|
| `%Y`   | Year (4 digits)                    | `2025`         |
| `%y`   | Year (2 digits)                    | `25`           |
| `%m`   | Month (01..12)                     | `05`           |
| `%d`   | Day of month (01..31)              | `16`           |
| `%H`   | Hour (00..23)                      | `22`           |
| `%I`   | Hour (01..12)                      | `10`           |
| `%M`   | Minute (00..59)                    | `45`           |
| `%S`   | Seconds (00..59)                   | `07`           |
| `%p`   | AM or PM                           | `PM`           |
| `%A`   | Full weekday name                  | `Friday`       |
| `%a`   | Abbreviated weekday name           | `Fri`          |
| `%B`   | Full month name                    | `May`          |
| `%b`   | Abbreviated month name             | `May`          |
| `%Z`   | Time zone                          | `IST`          |
| `%z`   | Time zone offset                   | `+0530`        |
| `%j`   | Day of year (001..366)             | `136`          |
| `%s`   | Seconds since UNIX epoch           | `1715888743`   |

---

## 🔹 Real-Time Examples

### ✅ Display current date in DD-MM-YYYY format

```bash
date "+%d-%m-%Y"
# Output: 16-05-2025
```

---

### ✅ Display current time in HH:MM:SS

```bash
date "+%T"
# Output: 22:20:43
```

---

### ✅ Show date and time with day and month names

```bash
date "+%A, %d %B %Y %I:%M %p"
# Output: Friday, 16 May 2025 10:20 PM
```

---

### ✅ Get yesterday's date

```bash
date --date="yesterday"
# Output: Thu May 15 22:21:32 IST 2025
```

---

### ✅ Get date 7 days from now

```bash
date --date="7 days"
# Output: Fri May 23 22:21:59 IST 2025
```

---

### ✅ Convert a string into a specific date format

```bash
date --date="2025-01-01" "+%A, %B %d, %Y"
# Output: Wednesday, January 01, 2025
```

---

### ✅ Get epoch time

```bash
date +%s
# Output: 1715888743
```

---

### ✅ Convert epoch time to readable date

```bash
date -d @1715888743
# Output: Fri May 16 22:25:43 IST 2025
```

---

## 🔧 Setting Date (Requires `sudo`)

```bash
sudo date --set="2025-05-16 22:30:00"
```

---


# ps Command in Linux

The `ps` (process status) command is used to display information about active processes on a Linux system. It's a crucial tool for system monitoring and debugging.

---

## 📌 Basic Syntax
```bash
ps [options]
```

---

## 🔹 Most Commonly Used Options

| Option            | Description |
|-------------------|-------------|
| -e / -A           | Show all processes |
| -f                | Full format (tree-like view) |
| -u <user>         | Show processes for a specific user |
| -x                | Show processes without terminal |
| -l                | Long format |
| -o                | User-defined output format |
| -p <pid>          | Display process with specific PID |
| --sort            | Sort output by a specific field (e.g., %cpu, %mem) |

---

## 🔹 BSD Format Options (no `-` required)

| Option  | Description |
|---------|-------------|
| a       | Show processes for all users |
| u       | Display user-oriented format |
| x       | Include processes without a terminal |
| aux     | Show all processes with user, CPU, memory |

---

## 🔹 Output Column Fields (used with `-o`)

| Field        | Description |
|--------------|-------------|
| pid          | Process ID |
| ppid         | Parent Process ID |
| uid / user   | User ID / name |
| cmd          | Command |
| %cpu         | CPU usage |
| %mem         | Memory usage |
| etime        | Elapsed time |
| stime        | Start time |
| stat         | Process state |
| rss          | Resident Set Size (RAM used) |

---

## ✅ Real-Time Use Cases & Examples

### 🔸 1. View All Running Processes
```bash
ps -ef
```

### 🔸 2. List All Processes in BSD Format
```bash
ps aux
```

### 🔸 3. Filter Processes by a Specific User
```bash
ps -u root
```

### 🔸 4. View a Specific PID
```bash
ps -p 1234
```

### 🔸 5. Custom Output: Only Show CPU & Memory Usage
```bash
ps -eo pid,cmd,%cpu,%mem --sort=-%cpu
```

### 🔸 6. See Top Memory-Hungry Processes
```bash
ps aux --sort=-%mem | head
```

### 🔸 7. Monitor a Specific Program
```bash
ps aux | grep apache2
```

### 🔸 8. See Processes Without a Terminal
```bash
ps -x
```

### 🔸 9. Show Process Tree with PPID
```bash
ps -eo pid,ppid,cmd --sort=ppid
```

### 🔸 10. Check for Zombie or Stuck Processes
```bash
ps -eo pid,stat,cmd | grep Z
```


## 📂 Summary Table

| Command | Description |
|---------|-------------|
| ps | Show current shell's processes |
| ps -ef | Full system process listing |
| ps aux | All user/system processes |
| ps -u <user> | Filter by user |
| ps -p <pid> | Show specific process |
| ps -eo pid,cmd | Custom format output |
| ps aux --sort=-%cpu | Sort by CPU |
| ps aux --sort=-%mem | Sort by memory |

---

# `kill` Command in Linux — Complete Guide

The `kill` command in Linux is used to **send signals** to processes. Most commonly, it's used to **terminate processes** gracefully or forcefully.

---

## 📌 Syntax

```bash
kill [options] <PID> [PID...]
```

- `<PID>` – Process ID(s) to which the signal will be sent.

---

## 🧰 All `kill` Command Options

| Option | Description |
|--------|-------------|
| `-s <signal>` | Send a signal by name |
| `-<signal>`  | Send signal by name or number directly (e.g., `-9`, `-SIGKILL`) |
| `-l`         | List all signal names with numbers |
| `-L`         | Same as `-l` but displays more clearly on some distros |
| `-p`         | Print the PID of named processes (not common in standard `kill`) |
| `--help`     | Display help message |
| `--version`  | Show version of kill utility |

---

## 🚦 All Signals You Can Use with `kill`

Run `kill -l` to list signals. Here are some important ones:

| Signal Name | Signal No. | Description |
|-------------|-------------|-------------|
| `SIGTERM`   | 15          | Graceful termination (default) |
| `SIGKILL`   | 9           | Force kill (cannot be caught or ignored) |
| `SIGSTOP`   | 19          | Pause a process |
| `SIGCONT`   | 18          | Resume a stopped process |
| `SIGHUP`    | 1           | Reload configuration (common in daemons) |
| `SIGINT`    | 2           | Interrupt from keyboard (Ctrl+C) |
| `SIGUSR1`/`SIGUSR2` | 10/12 | Custom user-defined signals |

---

## ✅ Real-Time Use Cases

### Gracefully stop process using PID
```bash
sudo kill 1234
```

### Force kill a frozen application using PID
```bash
kill -9 1234
```

### Gracefully stop a web server(apach2)
```bash
sudo pkill apache2
```

### Pause and resume a long-running process using PID
```bash
kill -SIGSTOP 1234  # Pause
kill -SIGCONT 1234  # Resume
```



### Terminate multiple processes at once
```bash
kill -9 1234 5678 9012
```

### 7. List all signals
```bash
kill -l
```
 ### Kill by id using `pgrep`
```bash
sudo kill -15 $(pidof apache2)
```

### Kill by name using `pgrep`
```bash
kill $(pgrep apache2)
```

Or directly using `pkill`:
```bash
pkill -9 apache2
```

---

## 🔐 Permissions

- You can kill only **your own processes**.
- Use `sudo` to kill **system or other user’s processes**.

---

## 🧠 Best Practices

- Always try `SIGTERM` (15) before `SIGKILL` (9).
- Use `kill` in scripts to manage child/background processes.
- Combine with `ps`, `pgrep`, `top`, etc., for dynamic control.
