
# Linux Commands – Interview Questions and Answers

A quick reference to common Linux commands often asked in technical interviews.

---

### What command is used to count the total number of lines, words, and characters contained in a file?

**Answer:**
> The `wc` command stands for "word count" and is used to display the number of lines, words, and bytes in a file.

---

### What command is used to remove files?
**Answer:**
> The `rm` command is used to delete files and directories.

---

### What command is used to remove a directory?

**Answer:**
> The `rmdir` command removes empty directories.

---

### 4. What command is used with `vi` editor to delete a single character?

**Answer:**  
> In `vi`, the `x` command deletes the character under the cursor.


---

###  What command you execute to count the number of lines in a file?

**Answer:**
> The `wc -l` command prints only the number of lines in the file.


---

### What command is used to display the characteristics of a process?

**Answer:**
> `ps` displays currently running processes and their details.

---

### What command is used to list contents of directories?

**Answer:** 
> The `ls` command lists the contents of a directory.

---

### Command used to create an empty file

**Answer:** `touch`

---

### Command used to show the logged-in user

**Answer:** `who`

---

### What command clears the contents of your terminal display?

**Answer:** `clear`

---

### What is the command to create the SSH key?

**Answer:** `ssh-keygen`

---

### What do you type in to move to the parent directory?

**Answer:** `cd ..`

---

### What command is used to change directories?

**Answer:** `cd`

---

### What command is used to get the IP address of all interfaces on a server?

**Answer:** `ip a` or `ifconfig` (deprecated but still in use on some systems)

---

### What command is used to change ownership of a file?

**Answer:** `chown`

---

### What command is used to copy a file?

**Answer:** `cp`

---

### What command(s) shows you disk partitions and percentage of disk space used?

**Answer:** `df -h` (disk free in human-readable format)  
  
For detailed partition info: `lsblk` or `fdisk -l`

---

### What command shows you how long it has been since the server was rebooted?

**Answer:** `uptime`

---


### What command shows you what directory you are in?

**Answer:** `pwd`

---

### What command creates an empty directory?

**Answer:** `mkdir`

---

### What command displays your current username?

**Answer:** `whoami`

---

### What command shows you CPU and memory utilization for running processes?

**Answer:** `top` or `htop` (if installed)

---

### What command allows you to open and view a file one page at a time?

**Answer:** `less` or `more`

---

### Which command(s) show users that are logged in?

**Answer:** `who`, `w`, or `users`

---

### What command is used to change a file name?

**Answer:** `mv oldname newname`

---

### What is the command to switch to the root user account?

**Answer:** `su -` or `sudo -i`

---

### What command is used to change the permissions of a file?

**Answer:** `chmod`

---

### What is the command to change your password?

**Answer:** `passwd`

---

###  What command is used to display your previously executed  commands?

**Answer:** `history`

---


### What command can you use to determine the current shell you are using at the command line?
**Ans:** `echo $SHELL`

### What is RPM?
**Ans:** RPM (Red Hat Package Manager) is a package management system used to install, update, remove, and manage software on RPM-based Linux distributions like RHEL, CentOS, Fedora.

###  What is apt-get?
**Ans:** `apt-get` is a command-line tool for handling packages in Debian-based Linux distributions such as Ubuntu. It is used for installing, upgrading, and removing software.

### What is the command to create a user in Linux server?
**Ans:** `useradd <username>`

### What is the difference between rm and rmdir commands?
**Ans:** `rm` is used to remove files and directories. `rmdir` is used to remove **only empty** directories.

### What is the command to display the user information like login name, real name, terminal name, shell?
**Ans:** `finger <username>` or `getent passwd <username>`

### What is the command to download any software from internet?
**Ans:** `wget <URL>` or `curl -O <URL>`

### What is the command to display the jobs that you are running in the background and in the foreground?
**Ans:** `jobs`

### How to check the status of one service?
**Ans:** `systemctl status <service-name>`

### What is the command which gives the description about any command?
**Ans:** `man <command>` or `whatis <command>`

---

### Explain the file system hierarchy in Linux system?
**Ans:**  
- `/`: Root directory  
- `/bin`: Essential binaries  
- `/boot`: Bootloader files  
- `/dev`: Device files  
- `/etc`: Configuration files  
- `/home`: User home directories  
- `/lib`: Shared libraries  
- `/opt`: Optional software packages  
- `/proc`: Process information  
- `/root`: Home directory of root user  
- `/sbin`: System binaries  
- `/tmp`: Temporary files  
- `/usr`: User-related programs  
- `/var`: Variable data (logs, cache, etc.)

### What is mkdir command and what are the -v, -p and -m options with mkdir command?
**Ans:**  
- `-v`: Verbose (shows what is being done)  
- `-p`: Create parent directories as needed  
- `-m`: Set file mode (permissions)

### What is `ls -ltr`? In this what is `l`, `t`, and `r`?
**Ans:**  
- `l`: Long listing format  
- `t`: Sort by modification time  
- `r`: Reverse the order

### How to list all hidden files and hidden directories?
**Ans:**  
- `ls -a | grep '^\.'`  
- `ls -ld .*`

### How to display only directories?
**Ans:**  
- `ls -d */`  
- `ls -l | grep '^d'`

### How to display only files?
**Ans:**  
- `ls -l | egrep -v '^d'`

### What is `cd -`?
**Ans:** Changes to the previous directory

### What is `cd ~`?
**Ans:** Changes to the home directory

### What is `cd`?
**Ans:** By itself, `cd` changes to the user's home directory


---

### Which user account is created on Linux during installation?  
**Ans:** `root` user

---

### What is the use of the `file` command?  
**Ans:** It is used to determine the type of a file (e.g., text, binary, script, image).

---

### How to check the RAM size?  
**Ans:** Using the `free` command  
Example:  
```bash
free -h
```

---

### How to check the server resource utilization?  
**Ans:** Using the `top` command

---

### 5. How to check CPU and memory statistics?  
**Ans:** Using the `top`  or `htop` command  
Example:  
```bash
top
```

---

### How to search for files with various conditions like empty files or based on size?  
**Ans:** Using the `find` command  
Examples:  
```bash
find /path -type f -empty             # Find empty files  
find /path -type f -size +100M        # Find files larger than 100MB
```

---

### How to set permissions for files or directories?  
**Ans:** Using the `chmod` command  
Example:  
```bash
chmod 755 script.sh
```

---

### What is `umask`?  
**Ans:** Umask defines the default permission bits for newly created files and directories.

---

### How to set the `umask` permanently for a user?  
**Ans:**  
Edit the `.bashrc` or `.profile` file in the user's home directory:  
```bash
vim ~/.bashrc
# Add the following line
umask 022
# Then source the file
source ~/.bashrc
```

---

### How to check open ports on the local system?  
**Ans:**  
```bash
netstat -tunlp
# or
ss -tuln
```

---

### How to check open ports on a remote server?  
**Ans:**  
```bash
nmap -A <server_ip>
```

---

### How to check which services are enabled across reboot?  
**Ans:**  
For systemd:  
```bash
systemctl list-unit-files --type=service
```

---

### What is load average in Linux?  
**Ans:** Load average is the average number of processes in the run queue or waiting for CPU over 1, 5, and 15 minutes.  
Use `top` or `uptime` to check it.

---

### What is a partial backup?  
**Ans:** A backup of selected directories or partitions instead of the entire system.

---

###  How can we review boot messages?  
**Ans:**  
```bash
journalctl -b
```

---

### What are the fields in the `/etc/passwd` file?  
**Ans:**  
```
username:password:UID:GID:comment:home_directory:login_shell
```

---

### How to check which RPM provides /etc/shadow file?  
**Ans:**  
```bash
rpm -qf /etc/shadow
```

---

### In which file are passwords saved for each user?  
**Ans:** `/etc/shadow`

---

### In which file is user information saved?  
**Ans:** `/etc/passwd`

---

### What is Inode? What is the use?  
**Ans:** Inode is a data structure used by Linux/Unix file systems to store information about a file or a directory except its name and content. It includes metadata such as file size, owner, permissions, and data block pointers.

---

### What is /etc/resolv.conf?  
**Ans:** This file configures DNS name servers.  
**If not configured:** The system won't be able to resolve domain names to IPs.

---

### What is vCPU? What if vCPU % is more than 1?  
**Ans:** vCPU is a virtual CPU allocated to a virtual machine. If vCPU usage exceeds 100%, it indicates CPU contention or overutilization, possibly causing performance issues.

---

### How to find memory details and explain swap memory?  
**Ans:**  
```bash
free -h
```
Swap memory is used when physical RAM is full. It's slower and resides on disk.

---

### Command to move `.log` files older than 5 days to another directory?  
**Ans:**  
```bash
find /source/path -name "*.log" -mtime +5 -exec mv {} /destination/path \;
```

---

### Booting process, runlevels, and default runlevel?  
**Ans:**  
- BIOS → Bootloader (GRUB) → Kernel → init/systemd → Runlevel  
- Runlevels: 0 (halt), 1 (single-user), 3 (multi-user), 5 (GUI), 6 (reboot)  
- Default: defined in `/etc/inittab` (init) or `systemctl get-default` (systemd)

---

### How to find top 10 processes?  
**Ans:**  
```bash
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head -n 11
```

---

### How to check open files on server?  
**Ans:**  
```bash
lsof
```

---

### What are directory special permissions?  
**Ans:** SUID, SGID, and Sticky Bit

---

### What is Sticky Bit?  
**Ans:** Prevents users from deleting files in a shared directory unless they own them (e.g., `/tmp`).

---

### What is NFS?  
**Ans:** Network File System – allows file sharing over the network.

---

### What does `mount -a` do?  
**Ans:** Mounts all filesystems defined in `/etc/fstab`.

---

### How to find a file containing specific content?  
**Ans:**  
```bash
grep -rl "search_text" /path/to/search
```

---

### How to check if a port is enabled?  
**Ans:**  
```bash
netstat -tuln | grep <port>
```
or  
```bash
ss -tuln
```

---

###  What is SSL?  
**Ans:** Secure Sockets Layer – used to encrypt connections over the internet.

---

###  What is GRUB?  
**Ans:** GRand Unified Bootloader – manages the boot process.

---

### Soft vs Hard Link?  
**Ans:**  
- Soft Link: pointer to the original file, breaks if file deleted  
- Hard Link: duplicate of file data blocks, survives original file deletion

---

### First statement in shell scripting?  
**Ans:**  Shebang Line
```bash
#!/bin/bash
```

---

### Explain Process and Threads?  
**Ans:**  

A process is an instance of a running program (or) any program under execution is called as process. It has its own:

- Memory space

- Environment variables

- System resources (like file descriptors, stack, heap, etc.)

- Unique Process ID (PID)


A thread is the smallest unit of execution within a process. It shares the same memory space and resources of its parent process.
Threads within the same process share memory, file descriptors, and other resources.
Threads are lightweight compared to processes.

---

### What is a Zombie Process?  
**Ans:** A process that has completed but still has an entry in the process table.

---

### How to find files used by a process?  
**Ans:**  
```bash
lsof -p <PID>
```

---

### What is a Zone File?  
**Ans:** DNS configuration file that maps domain names to IPs.

---

### How to prevent users from scheduling a cronjob?  
**Ans:**  
**Ans:** D) Create an empty file called `/etc/cron.allow`

---

###  How to display present working directory using command substitution?  
**Ans:** `echo $(pwd)`

---

### Which file contains default environment variables for bash?  
**Ans:** `/etc/profile`

---

### What is Crontab?  
**Ans:** Scheduler for executing tasks(commands/scripts) at specified times.

---

### What are vmstat and memstat?  
**Ans:**  
- `vmstat`: reports memory, CPU, and I/O usage  
- `memstat`: shows memory usage (mostly used in Solaris)

---

### How to change run levels?  
**Ans:**  
- SysV: `init 3`, `init 5`  
- Systemd: `systemctl isolate runlevel3.target`

---

### What is Linux Loader?  
**Ans:** A loader like LILO, LOADLIN, or GRUB that loads the kernel into memory.

---

### What is a stateless Linux server?  
**Ans:** A server with no persistent configuration or local storage — all configs/data fetched from a central server.

---

###  A process is identified by a unique?  
**Ans:** pid (process id)

---

### Best way to set up SSH without passwords?  
**Ans:** Use `ssh-keygen` to generate public-private keys

---

## Let’s say I have one shell script, and I want it to be executed **only during system boot time** (not at login or any other time). What should I do?

**Ans:**  
Place the script in one of the system boot initialization directories or configure it using one of the following:

- **Systemd method (recommended for modern systems):**  
  Create a custom systemd service in `/etc/systemd/system/myscript.service`:
  ```ini
  [Unit]
  Description=Run My Script at Boot Time
  After=network.target

  [Service]
  Type=oneshot
  ExecStart=/path/to/your/script.sh
  RemainAfterExit=yes

  [Install]
  WantedBy=multi-user.target
  ```
  Then enable it with:
  ```bash
  sudo systemctl enable myscript.service
  ```

- **Older systems (SysVinit):**  
  Place your script in `/etc/init.d/` and use `update-rc.d` or `chkconfig` to configure it.

---

### What is the difference between `.bash_profile` and `.bashrc` files in the user's home directory?

**Ans:**  
| File | When It's Used | Purpose |
|------|----------------|---------|
| `.bash_profile` | Executed for **login shells** | Setup environment variables, paths, etc. |
| `.bashrc` | Executed for **interactive non-login shells** | Customize shell behavior, aliases, functions |

> Note: `.bash_profile` often contains a line to source `.bashrc`, like:  
> `if [ -f ~/.bashrc ]; then . ~/.bashrc; fi`

---

###  What is a Login Shell and Non-Login Shell?

**Ans:**

- **Login Shell:**  
  When a user logs in via terminal, SSH, or the console. It reads config files like `/etc/profile`, `~/.bash_profile`.

- **Non-Login Shell:**  
  Invoked without logging in (e.g., opening a new terminal in a GUI). It reads `~/.bashrc`.

---

### What is the `/etc/shadow` file?

**Ans:**  
The `/etc/shadow` file contains secure user account information and is readable **only by root**. It stores:

- Encrypted passwords
- Password aging information
- Account expiry

**Format:** Each line contains the following fields, separated by `:`  
```
username:encrypted-password:last-change:min:max:warn:inactive:expire:reserved
```

**Example:**
```plaintext
john:$6$2vv...:19100:0:99999:7:::
```

**Explanation:**
- `username`: User login name  
- `encrypted-password`: Password hash or `!` for locked accounts  
- `last-change`: Days since Jan 1, 1970, of last password change  
- `min`: Minimum days before password can be changed  
- `max`: Maximum days password is valid  
- `warn`: Days before expiry to warn the user  
- `inactive`: Days after expiry before disabling account  
- `expire`: Account expiration date (in days since epoch)  
- `reserved`: Reserved field

---

### What is the difference between /bin and /sbin directory?
**Ans:**  
- `/bin` contains essential user binaries (e.g., `ls`, `cp`) available for all users.  
- `/sbin` contains system binaries (e.g., `shutdown`, `reboot`) intended for the root user.

---

### What configuration do we set to differentiate between normal and root users?
**Ans:**  
Shell prompt changes (`$` for normal user, `#` for root), and user-specific permissions in `/etc/sudoers`.

---

### There are settings that prevent normal users from accessing advanced commands. What are those?
**Ans:**  
Environment variables like `PATH` and permission configurations. Also, the `/etc/sudoers` file controls command access.

---

### What is PATH and what does it do?
**Ans:**  
`PATH` is an environment variable that tells the shell where to look for executable files.

---

### Difference between $* and $@
**Ans:**  
- `$*`: Treats all arguments as a single word.  
- `$@`: Treats each argument as a separate word.

---

### Explain about Cron Job?
**Ans:**  
Cron is a time-based job scheduler in Unix. You can schedule tasks using `crontab -e`.  
Example:
```
0 2 * * * /path/to/script.sh
```
(Runs the script daily at 2 AM)

---

### How to check where a software (e.g., Jenkins) is installed?
**Ans:**  
Use:
```bash
which jenkins
whereis jenkins
rpm -ql jenkins   # for RPM-based systems
dpkg -L jenkins   # for Debian-based systems
```

---

### How to set the PATH globally (accessible by all users)?
**Ans:**  
Edit `/etc/profile` or create a script under `/etc/profile.d/` to export the new path.

---

### How to create a user?
**Ans:**
```bash
useradd rushi
```

---

### How to create a group?
**Ans:**
```bash
groupadd devopsteam
```

---

### How to add a user to a group?
**Ans:**
```bash
usermod -g devopsteam rushi
```

---

### How to check CPU utilization?
**Ans:**  
Use `top` or `htop`

---

### What is load average?
**Ans:**  
It shows the average number of processes waiting to run in the last 1, 5, and 15 minutes.  


---

### What is the difference between load average and CPU load?
**Ans:**  
- **Load Average:** Reflects all processes in the queue including IO wait.  
- **CPU Load:** Only CPU usage, doesn't include processes waiting on IO.


---


### 27) What are Linux process states?

**Ans:**  
A process can be in any of the following states:
- `R`: Running or runnable (on run queue)
- `D`: Uninterruptible sleep (usually I/O)
- `S`: Interruptible sleep (waiting for an event)
- `Z`: Zombie (terminated but not reaped)
- `T`: Stopped (by job control or tracing)
- `W`: Paging (not used in modern kernels)
- `X`: Dead (should never be seen)

Processes start in the `R` state and end in the `Z` state before being cleaned up. Use `top` or `ps` to view process states.

---

### On what process the server will shutdown?

**Ans:**  
System shutdown typically terminates all processes. PID 1 (usually `systemd` or `init`) coordinates the shutdown process.

---

### How to find and delete empty directories in the current directory?

**Ans:**  
```bash
find . -type d -empty -delete
```

---

### How to find empty files in the current directory?

**Ans:**  
```bash
find . -type f -empty
```

---

### How to remove empty lines from a file?

**Ans:**  
Use `sed`:
```bash
sed -i '/^$/d' filename
```

---

### What is `umask`?

**Ans:**  
`umask` defines default permissions for newly created files and directories.  
- Common default: `022` (files: 644, directories: 755)

---

### What is the maximum UMASK value?

**Ans:**  
- For files: `666` (max), `000` (min)  
- For directories: `777` (max), `000` (min)

---

### What are the default permissions for a file?

**Ans:**  
Depends on `umask`. With default `umask 022`, new files have `644` permissions.

---

### What are the default permissions for a directory?

**Ans:**  
With default `umask 022`, new directories get `755` permissions.

---

###  What is `chmod`?

**Ans:**  
`chmod` (change mode) is used to change file and directory permissions.

---

### How to check open ports in Linux?

**Ans:**  
Using `netstat`:
```bash
netstat -a | grep LISTEN
```

---

### What do the following commands do?

- `tee`: Reads from standard input and writes to both stdout and files.
- `awk`: Pattern scanning and processing language.
- `tr`: Translates or deletes characters from input.
- `cut`: Removes sections from each line of input.
- `tac`: Displays file lines in reverse order.
- `curl`: Transfers data from or to a server (supports many protocols).
- `wget`: Downloads files from the internet via HTTP/HTTPS/FTP.
- `watch`: Runs a command repeatedly and shows output.
- `tail`: Displays the last lines of a file.

---

### What does an `&` after a command do?

**Ans:**  
The ampersand (`&`) is used to run a command **in the background**.

Example:
```bash
sh demo.sh &
```
This starts `demo.sh` as a background process and immediately returns control to the terminal.

> A background process will **not survive** if the shell session is closed. When a shell exits, it sends the `SIGHUP` signal to all background jobs, terminating them.

To keep a background process running **after disconnection**, use `nohup`:

```bash
nohup sh demo.sh &
```

This runs `demo.sh` in the background and prevents it from terminating when the session ends.

---

###  What is Swap and what is it used for?
**Ans:**
Swap is a dedicated space on the disk used as virtual memory when the system's RAM is fully utilized.

🔧 Purpose of Swap:
Acts as overflow memory when the system runs out of physical RAM.

Helps prevent out-of-memory errors.

Supports features like hibernation (on some systems).

🔄 How it works:
When active memory (RAM) is full, the OS moves inactive pages (least-used memory blocks) from RAM to the swap area.

This frees up RAM for active processes, maintaining system stability.

📁 Types of Swap:
Swap Partition: A separate disk partition.

Swap File: A regular file that acts like swap space.

---
### What is the difference between hard links and symlinks? What happens when you remove the source?

**Ans:**  
- **Hard Link:** Points to the same inode as the original file. File remains accessible even if the original file is deleted.
- **Symlink (Soft Link):** Points to the path of the original file. If the source is deleted, the symlink becomes broken.

---

### What is an inode and what fields are stored in an inode?

**Ans:**  
An inode stores metadata about a file:
- File type and permissions
- Owner and group
- Size
- Timestamps (created, modified, accessed)
- Number of links
- Pointers to data blocks

---

### How to add a user without `useradd` or `adduser`?

**Ans:**  
Manually:
- Create home directory
- Add entry to `/etc/passwd`, `/etc/shadow`, `/etc/group`
- Set password with `passwd`


---

### Filesystem shows full but `df` shows space – why?

**Ans:**  
Open files deleted by a process still consume space. Use `lsof | grep deleted`.

---

### Deleted file but `df` doesn’t free space?

**Ans:**  
File held open by a process. Use `lsof` to identify and kill process.

---

### How does `ps` work?

**Ans:**  
It reads `/proc` to list process status, PID, memory, CPU usage, etc.

---

### What happens when a child process dies and has no parent?

**Ans:**  
Becomes a **zombie** until reaped by `init`. Too many zombies = resource leak.

---

### How to find which process is listening on a port?

**Ans:**  
```bash
lsof -i :<port>
```

---

### Key to suspend and background a job?

**Ans:**  
`Ctrl + Z`

---

### Best tool for DNS queries?

**Ans:**  
**dig** 

---

### How to check if user is root?


To determine whether a user is root in Linux, you can use any of the following methods:

🔹 1. Using `id` Command
```bash
id -u
```
- Output: `0` → This is the **root** user  
- Output: Any other number → **Non-root** user


🔹 2. Using `$UID` Environment Variable
```bash
echo $UID
```
- Output: `0` → Root  
- Output: Any other number → Non-root

🔹 3. Using `whoami`
```bash
whoami
```
- Output: `root` → You are root  
- Output: any other username → You are not root

🔹 4. Inside a Shell Script
```bash
if [ "$(id -u)" -eq 0 ]; then
    echo "You are root"
else
    echo "You are NOT root"
fi
```

This script conditionally checks for root privileges and prints a message accordingly.

---

### How to give sudo access to user?

**Ans:**  
- Add user to sudoers file

---

### Last 10 commands used?

**Ans:**  
```bash
history 10
```

---

### Script to delete last word of every line?

**Ans:**  
```bash
awk '{sub(/[[:alnum:]]+$/, ""); print}' filename
```

---

### Replace last word with "hello"?

**Ans:**  
```bash
awk '{$NF="hello"}1' filename
```

---

### Find files > 1GB?

**Ans:**  
```bash
find /path -size +1G -type f
```

---

### Max length of file name in Linux?

**Ans:**  
255 characters

---

### Which directory under the root filesystem contains system configuration files in Linux?

**Ans:**  
`/etc`

---

### Command to uncompress gzip files?

**Ans:**  
```bash
gunzip filename.gz
```

---

### Difference between soft and hard mount?

**Ans:**  
- **Soft:** Times out if server not reachable.
- **Hard:** Keeps retrying indefinitely.

---

### File permissions in Linux?

**Ans:**  
- Read (r), Write (w), Execute (x)
- Set with `chmod`, `chown`

---

### How to check memory and CPU stats?

**Ans:**  
Use `top`, `htop`, `free -h`, `vmstat`

---

### How to secure password file?

**Ans:**  
Move hashes to `/etc/shadow`, use `chmod 000 /etc/shadow`

---

### Difference between Cron and Anacron?

**Ans:**  
- **Cron:** For systems that are always on.
- **Anacron:** For systems that are turned off periodically.

---

### Command to check quotas?

**Ans:**  
```bash
repquota -a
```

---

### How to manage memory?

**Ans:**  
- Monitor: `free`, `vmstat`, `top`
- Tune swappiness, clear cache: `echo 3 > /proc/sys/vm/drop_caches`

---

### System log file name and path?

**Ans:**  
`/var/log/syslog` or `/var/log/messages`

---

### What is `/proc`?

**Ans:**  
Virtual filesystem showing real-time process and system info.

---

### Fields in `/etc/passwd`?

**Ans:**  
`username:x:UID:GID:comment:home:shell`

---

### How to terminate a process?

**Ans:**  
```bash
kill <pid>
kill -9 <pid>
```

---

### Execution time of a command?

**Ans:**  
```bash
time <command>
```

---

### Append one file to another?

**Ans:**  
```bash
cat file1 >> file2
```

---

### Run a program in background on boot?

**Ans:**  
Use `cron @reboot`, `systemd` service, or `rc.local`


---

### What is `stop` command?

**Ans:**  
Depends on context. For services:
```bash
systemctl stop <service>
```

---

### How to stop a process?

**Ans:**  
```bash
kill <PID>
```

---

### Can you delete content using `sed`?

**Ans:**  
Yes. Example:
```bash
sed -i 'd' filename
```
