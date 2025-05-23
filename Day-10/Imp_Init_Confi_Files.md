
# Important Linux Initialization and Configuration Files

Linux relies on various **initialization** and **configuration** files to manage system settings, services, environment variables, and user-specific configurations.

---

## /etc/fstab – Static File System Configuration
**Description:** Static file system info. Auto-mount partitions/devices.
**Example:** `UUID=xxxx-xxxx / ext4 defaults 0 1`

```
/dev/sda1   /       ext4    defaults        0       1
/dev/sdb1   /data   ext4    defaults        0       2
```

---

##  /etc/hostname – System Hostname
**Description:** Sets the system hostname used during boot.

```
web-server-01
```

---

## /etc/hosts – Static Hostname to IP Mapping
**Description:** Local DNS mappings. Maps IPs to hostnames.Used for local name resolution.

```
127.0.0.1   localhost
192.168.1.100 web-server-01
```

---

## /etc/resolv.conf – DNS Resolver Configuration
**Description:** DNS resolver configuration.Specifies nameservers.
**Example:** `nameserver 8.8.8.8`


```
nameserver 8.8.8.8
nameserver 1.1.1.1
```

---

## /etc/systemd/system/ or /lib/systemd/system/ – Systemd Unit Files
**Description:** Systemd service unit files for managing daemons.

Custom service configurations.

```
[Unit]
Description=Apache Tomcat
After=network.target

[Service]
Type=forking
User=tomcat
ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

[Install]
WantedBy=multi-user.target
```

---

##  /etc/passwd – User Account Information
**Description:** Stores user account information.
**Format:** `username:x:UID:GID:comment:home:shell`

```
balaji:x:1001:1001:Balaji:/home/balaji:/bin/bash
```

---

##  /etc/shadow – Password Information (Encrypted)
**Description:** Stores encrypted user passwords. Only readable by root.

```
username:encrypted_password:last_change:min:max:warn:inactive:expire
```

---

## /etc/group – Group Definitions
**Description:** Defines groups and group memberships.

```
admin:x:1002:balaji,alice
```

---

## /etc/sudoers – Sudo Privileges
**Description:** Defines who has access to sudo command.

```
balaji ALL=(ALL) NOPASSWD: ALL
```

---

## /etc/ssh/sshd_config – SSH Daemon Configuration

**Description:** sshd process configurations.

```
PermitRootLogin no
PasswordAuthentication no
```


---

## /etc/crontab – System Cron Jobs
**Description:** Schedules recurring cron jobs.

```
0 3 * * * root /opt/scripts/backup.sh
```

---

## /etc/sysctl.conf – Kernel Parameters

**Description:** Kernel parameter config (e.g., memory, networking).


```
net.ipv4.ip_forward=1
vm.swappiness=10
```


---

## /etc/init.d/ – Legacy Init Scripts

**Description:** Legacy init scripts for service control (SysVinit systems).

```
/etc/init.d/apache2 start
```

---

## /etc/environment – Global Environment Variables
**Description:** System-wide environment variables for all users.

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
JAVA_HOME="/usr/lib/jvm/java-11-openjdk"
```

---

## Summary Table

| File/Directory             | Purpose                                 | Applies To            |
|---------------------------|------------------------------------------|------------------------|
| `/etc/fstab`              | Mount points configuration               | Boot & Mounting        |
| `/etc/hostname`           | System hostname                          | Network & Identity     |
| `/etc/hosts`              | Static IP-Hostname resolution            | DNS                    |
| `/etc/resolv.conf`        | DNS resolver setup                       | Network                |
| `/etc/network/*`          | Network interface settings               | Network config         |
| `/etc/systemd/system/`    | Custom service definitions               | Service management     |
| `/etc/profile`            | System-wide shell settings               | Shell/Env              |
| `~/.bashrc`, `~/.bash_profile` | User shell settings                 | User sessions          |
| `/etc/passwd`, `/etc/shadow` | User and password data               | User management        |
| `/etc/sudoers`            | Sudo privilege config                    | Permissions            |
| `/etc/ssh/sshd_config`    | SSH daemon settings                      | Remote login           |
| `/etc/default/grub`       | Boot loader settings                     | Boot config            |
| `/etc/crontab`            | Scheduled tasks                          | Automation             |
| `/etc/sysctl.conf`        | Kernel parameters                        | Performance/Security   |
