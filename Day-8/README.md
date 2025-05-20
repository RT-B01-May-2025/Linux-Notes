
# 👤 Users and Groups in Linux

Linux is a **multi-user** operating system. Every user and group is assigned unique identifiers and permissions to access files and system resources.

---

## 🧑‍💼 What is a User in Linux?

A **user** in Linux represents a single account that can log into the system. Each user has a unique **UID (User ID)** and a **home directory**.

### Types of Users:
1. **Root user**: Superuser with full control (UID=0).
2. **System users**: For system services like `jenkins`, `mysql`.
3. **Regular users**: Created by admins or during OS setup.

---

## 👥 What is a Group in Linux?

A **group** is a collection of users. Groups are used to assign permissions collectively to multiple users.

- Each group has a **GID (Group ID)**.
- A user can be in:
  - **Primary group**: Defined in `/etc/passwd`.
  - **Secondary groups**: Defined in `/etc/group`.

---

## 📂 Important Files

| File | Description |
|------|-------------|
| `/etc/passwd` | Stores user account info |
| `/etc/shadow` | Stores encrypted passwords |
| `/etc/group` | Stores group info |
| `/etc/gshadow` | Stores encrypted group passwords |

---

## 🛠️ User Management Commands

🔐 **Only the `root` user or users with `sudo` privileges can manage users.**

```
ls -l /home                    # List user home directories
cat /etc/passwd                 # View all user account information
cat /etc/group                  # View all group information
cat /etc/shadow                 # View encrypted passwords (only root can view)
```

### 🧠 Notes:
- `/etc/passwd`: Stores basic user info like username, UID, GID, shell, home dir.
- `/etc/group`: Stores group info.
- `/etc/shadow`: Stores hashed passwords and password aging info (readable only by root).

---

### ➕ Create a User
```bash
sudo useradd <username>
```
**Options:**
- `-m` → Create a home directory
- `-s` → Define shell (e.g., `/bin/bash`)
- `-u` → Set custom UID
- `-d` → Set custom home directory

**Example:**
```bash
sudo useradd balaji # Basic Command
sudo useradd -m -s /bin/bash balaji # Command with additional options
```
When a new user is created, a new group with the same name is created and the user is added to it. This group is called the primary group of the user.

---

### 🔑 Set User Password
```bash
sudo passwd <username>
```
**Example:**
```bash
sudo passwd balaji
```
## ⏳ Password Expiry with `chage` (If Required)

### 🔹 Set password expiration for a user:
```bash
sudo chage balaji
```

You’ll be prompted to enter:
- Minimum password age
- Maximum password age
- Password expiration warning, etc.

### 🔹 View updated values:
```bash
cat /etc/shadow
```

---

### ✏️ Modify a User
```bash
sudo usermod [options] <username>
```
**Common Options:**
- `-l` → Rename user
- `-d` → Change home directory
- `-s` → Change shell
- `-G` → Add to secondary groups
- `-L`/`-U` → Lock/Unlock account

**Example:**
```bash
sudo usermod -d /home/newdir balaji
```

---

### ❌ Delete a User
```bash
sudo userdel <username>
```
- User is removed from `/etc/passwd`
- Home directory `/home/testuser` is **not deleted**

**With home directory:**
```bash
sudo userdel -r <username>
```
- User removed
- `/home/testuser` and mail files deleted

---

## 🛠️ Group Management Commands

### ➕ Create a Group
```bash
sudo groupadd <groupname>
```
**Example:**
```bash
sudo groupadd devops
```

- Groups info is stored in: `/etc/group`
- Each user also has a default group created with their name.

## ➕ Add a User to a Group with `usermod`

```bash
sudo usermod -aG devops balaji
```
---

### ✏️ Modify a Group
```bash
sudo groupmod [options] <groupname>
```
**Options:**
- `-n` → Rename group
- `-g` → Change GID

**Example:**
```bash
sudo groupmod -n developers devteam
```

---

### ❌ Delete a Group
```bash
sudo groupdel <groupname>
```
**Example:**
```bash
sudo groupdel devteam
```
> Group must not be the **primary group** for any user
### ⚠️ Fix if group is still in use:
```bash
sudo usermod -g <otherGroup> balaji
sudo groupdel devops
```

---

## 👤👥 Add User to Group
```bash
sudo usermod -aG <groupname> <username>
```
**Example:**
```bash
sudo usermod -aG devops balaji
```

---

## 📜 View Users and Groups

### List All Users
```bash
cut -d: -f1 /etc/passwd
```

### List All Groups
```bash
cut -d: -f1 /etc/group
```

### View User Info
```bash
id <username>
```

**Example Output:**
```bash
uid=1001(balaji) gid=1001(balaji) groups=1001(balaji),27(sudo)
```
### 🔹 Verify Group Members:
```bash
sudo lid -g devops
```
> If `lid` is not installed, install it:
```bash
sudo yum install libuser -y
```

## 💼 Check User's Group Membership

```bash
id balaji          # Shows UID, GID, and group membership
groups devops      # Lists all groups the user belongs to
```

---

## 📌 Real-Time Use Cases

### ✅ Use Case 1: Create a Developer User
```bash
sudo useradd -m -s /bin/bash -G devteam devuser
sudo passwd devuser
```

### ✅ Use Case 2: Add a User to Sudo Group
```bash
sudo usermod -aG sudo balaji
```

### ✅ Use Case 3: List Members of a Group
```bash
getent group <groupname>
```
**Example:**
```bash
getent group devops
```

---

## 📁 Bonus: View Current User and Groups

### Current User
```bash
whoami
```

### Groups for Current User
```bash
groups
```

## 💡 Pro Tips

- Backup user data before deletion
- Use `find / -user username` to locate leftover files
- Automate with user cleanup scripts for offboarding

---

# `sudo` Command in Linux

The `sudo` (short for **superuser do**) command allows a permitted user to **execute a command as another user**, typically the **root user**, with elevated privileges. This is commonly used for administrative tasks without needing to switch to the root user permanently.

---

## 🔹 Basic Syntax

```bash
sudo [OPTION] COMMAND
```

---

## 🔹 Key Features

- Executes a command as root or another user
- Logs all sudo activities (`/var/log/auth.log` on Debian/Ubuntu)
- Requires user authentication
- Respects permissions defined in the **`/etc/sudoers`** file

---

## 🔹 Common Use Cases

| Task                                  | Command                                |
|---------------------------------------|----------------------------------------|
| Update package index (Debian-based)   | `sudo apt update`                      |
| Install a package                     | `sudo apt install nginx`               |
| Edit a system file                    | `sudo nano /etc/fstab`                 |
| Reboot the system                     | `sudo reboot`                          |
| Change file ownership                 | `sudo chown user:user /path/file`      |

---

## 🔹 `sudo` Command Examples

### 1. Run a command as root

```bash
sudo mkdir /opt/myapp
```

### 2. Run a command as another user

```bash
sudo -u postgres psql
```

### 3. Edit a file with root privileges using a text editor

```bash
sudo nano /etc/hosts
```

---

## 🔹 Useful Options

| Option       | Description                                      |
|--------------|--------------------------------------------------|
| `-u user`    | Run the command as the specified user            |
| `-k`         | Reset the timestamp and require a new password   |
| `-l`         | List permitted and forbidden commands for user   |
| `-s`         | Run the shell as the target user (default root)  |
| `-v`         | Extend the sudo timeout (keeps session alive)    |
| `-i`         | Simulate initial login environment of the user   |

---


## 📁 What is the `sudoers` File?

The `/etc/sudoers` file defines **which users or groups can run what commands using `sudo`**.

> **Never edit it directly.** Use: `visudo` to edit this file to avoid syntax errors.

```bash
sudo visudo
```

### 🔹 Format of an Entry:
```bash
<user> <host>=<user_to_run_as>: <command>
```

### ✅ Example:
```bash
balaji ALL=(ALL:ALL) ALL
```
- `balaji`: Username
- `ALL`: Any host
- `(ALL:ALL)`: Run as any user and group
- `ALL`: Can run all commands

---

## 🧍 How to Get `sudo` Access

### 🔸 Method 1: Add User to `sudo` Group (Ubuntu/Debian)
```bash
sudo usermod -aG sudo <username>
```

🧪 Example:
```bash
sudo usermod -aG sudo balaji
```

Then verify:
```bash
groups balaji
```

---

### 🔸 Method 2: Add User in `sudoers` File
```bash
sudo visudo
```

Add this line:
```bash
balaji ALL=(ALL:ALL) ALL
```

### Grant passwordless sudo:

```bash
balaji ALL=(ALL) NOPASSWD: ALL
```

---

## 🔹 Get Sudo Access

### 1. Add user to `sudo` group (Debian/Ubuntu)

```bash
sudo usermod -aG sudo username
```

### 2. Add user to `wheel` group (Red Hat/CentOS/Fedora)

```bash
sudo usermod -aG wheel username
```

---

## 🔹 Check Sudo Access

```bash
sudo -l
```

Shows what commands you're allowed to run as `sudo`.

---

## 🔹 Real-Time Use Cases

- Installing software (`sudo apt install nginx`)
- Managing system services (`sudo systemctl restart sshd`)
- Modifying restricted system files (`sudo vi /etc/hosts`)
- Adding users (`sudo adduser newuser`)
- Setting file permissions on system files (`sudo chmod 600 /etc/passwd`)
---

# 🧑‍💻 `sudo su` vs `sudo su -` in Linux

Both `sudo su` and `sudo su -` are used to switch to the `root` user, but they behave differently regarding environment variables and login shell behavior.

---

## ✅ Purpose

| Command     | Description                                |
|-------------|--------------------------------------------|
| `sudo su`   | Switches to root user **without** a login shell |
| `sudo su -` | Switches to root user **with** a login shell    |

---

## 📌 1. `sudo su`

- **Function:** Switches to root user, preserving the **current user's environment**.
- **Does not** load root's `.bashrc` or `.profile`.
- **Current working directory** remains unchanged.
- **Command:**
  ```bash
  sudo su
  ```
- **Example Use Case:** You quickly need to become root but want to retain your existing shell and environment.

---

## 📌 2. `sudo su -`

- **Function:** Switches to root with a **full login shell**.
- Loads environment variables and startup scripts like `.bashrc`, `.profile` for root.
- Changes working directory to `/root`.
- **Command:**
  ```bash
  sudo su -
  ```
- **Example Use Case:** You want a **clean root environment**, like for installing software or running system-wide tasks.

---

## 🔍 Environment Comparison

| Feature            | `sudo su`       | `sudo su -`     |
|--------------------|------------------|------------------|
| Login shell        | ❌ No             | ✅ Yes            |
| User environment   | ✅ Preserved      | ❌ Replaced       |
| Root environment   | ❌ Not loaded     | ✅ Fully loaded   |
| Working directory  | 🟡 Current        | 🟢 /root           |

---

## 🧾 Real Example

Suppose your regular user has an alias:
```bash
alias ll='ls -alF'
```

- After `sudo su`, alias might still work.
- After `sudo su -`, alias won’t be available unless defined in root’s profile.

---

## 🛠️ Best Practice

- ✅ Use `sudo su -` for system-level tasks (installing packages, editing config files).
- ⚠️ Use `sudo su` only for quick tasks and when you intentionally want to keep your current shell environment.

---
 PATH Environment Variable in Linux

## 🧾 What is `PATH` Environment Variable in Linux?

`PATH` is a **special environment variable** in Linux that tells the shell **where to look** for executable files (commands or programs). When you type a command in the terminal, Linux searches through the directories listed in PATH to find that command.



### 🔹 Why `PATH` is Important
When you type a command like `ls`, Linux searches through the directories listed in `PATH` to find and execute the corresponding binary.

Without PATH, you'd have to type the full path to every command, like:

```bash
/usr/bin/ls
```bash

But with PATH, you can just type:

```bash
ls
```bash

Because /usr/bin is already in your PATH

### 🔹 Syntax of `PATH`

```bash
echo $PATH
```bash

Example Output:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

Each path is **colon (`:`) separated**, and the shell looks for executables in the order listed.

---

## 🧑‍💻 How to Set PATH – User-Wise and System-Wise

### 1️⃣ User-wise PATH Setting

#### 🔸 Temporary (for current session)
Add a directory to the user's `PATH` in the current session:

```bash
export PATH=$PATH:/home/username/scripts
```

> This will work only until you close the terminal.

#### 🔸 Permanent (for a specific user)

Edit one of the user's shell configuration files, such as:
- `~/.bashrc` (for Bash)
- `~/.zshrc` (for Zsh)
- `~/.bash_profile` (for Bash)
- `~/.profile` (for login shells)

**Steps:**

```bash
nano ~/.bashrc
```

Add the line:

```bash
export PATH=$PATH:/home/username/scripts
```

Save and apply changes:

```bash
source ~/.bashrc
```

---

### 2️⃣ System-wide PATH Setting

#### 🔸 Temporary (affects all users for current session)

You can export a path for all users in a running session by editing `/etc/profile` or creating a file in `/etc/profile.d/`.

```bash
sudo nano /etc/profile
```

Add the line:

```bash
export PATH=$PATH:/opt/tools
```

Or, better, create a new script:

```bash
sudo nano /etc/profile.d/custom_path.sh
```

```bash
export PATH=$PATH:/opt/tools
```

Make it executable:

```bash
sudo chmod +x /etc/profile.d/custom_path.sh
```

#### 🔸 Permanent system-wide (for all users and sessions)

You can also edit:
- `/etc/environment`: Only for defining the variable (no scripting allowed).

```bash
sudo nano /etc/environment
```

Add or modify:

```bash
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/tools"
```

Changes take effect on next login or after reboot.

---

## ✅ Verifying the PATH

```bash
echo $PATH
```

## 🔍 Finding a Command Path

```bash
which <command>
```

Example:
```bash
which python3
# Output: /usr/bin/python3
```

---

## ⚠️ Best Practices

- Always append using `$PATH` to preserve existing directories.
- Avoid using `.` in PATH for security reasons.
- Keep custom paths like scripts/tools towards the end of PATH to avoid overriding system binaries.
