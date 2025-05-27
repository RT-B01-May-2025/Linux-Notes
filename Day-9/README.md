## 📘 `umask` in Linux

### 🔹 What is `umask`?
`umask` stands for **User File-Creation Mode Mask**. It determines the **default permission bits** that are **removed** from newly created files and directories.

### 🔹 Default Permissions
- New **files** are created with default **666** (`rw-rw-rw-`)
- New **directories** are created with default **777** (`rwxrwxrwx`)

## 📌 Default Permissions Before `umask`

| Item       | Default Permission (Octal) | Symbolic     |
|------------|----------------------------|--------------|
| Files      | 666                        | rw-rw-rw-    |
| Directories| 777                        | rwxrwxrwx    |

> **Note:** Files are never given execute (`x`) permission by default.
> **Note:** Permissions are not going to change for previous files and directories.If u change umask value of the user.

## 🧮 How `umask` Works

### Formula:
```
Final Permission = Default Permission - umask
```

### Example:
If umask = `022` and default file permission is `666`:
```
666 - 022 = 644 → rw-r--r--
```

> The `umask` value subtracts permission bits from the default.

## 📌 Diagram: Permission Calculation with `umask`

```
Default File Permission:    666 (rw-rw-rw-)
UMASK:                      022
-----------------------------
Final Permission:           644 (rw-r--r--)
```
```pgsql
rwx r-- r--
│   │   │
│   │   └── Others (o) permissions
│   └────── Group (g) permissions
└────────── Owner/User (u) permissions
```

```
Default Dir Permission:     777 (rwxrwxrwx)
UMASK:                      022
-----------------------------
Final Permission:           755 (rwxr-xr-x)
```

The permission string rwxr-xr-x represents file or directory permissions in symbolic format for:

```pgsql
rwx r-x r-x
│   │   │
│   │   └── Others (o) permissions
│   └────── Group (g) permissions
└────────── Owner/User (u) permissions
```


## 🛠 Real-time Examples

### 🔹 Check current umask value:
```bash
umask
```

### 🔹 Set umask temporarily:
```bash
umask 027
```

### 🔹 Create file and check permission:
```bash
touch abc.txt
ls -l abc.txt
```

### 🔹 Create directory and check permission:
```bash
mkdir devops
ls -ld devops
```

## 🧑‍💻 Default umask Values

| User Type     | Default umask |
|---------------|----------------|
| Root user     | 0022           |
| Normal user   | 0002 or 0022   |


## 🗂 Persistent `umask` Settings

### 🔸 For a specific user:
Add to `~/.bashrc` or `~/.profile`:
```bash
umask 027
```

### 🔸 System-wide:
Edit `/etc/profile`, `/etc/bash.bashrc`:
```bash
UMASK 027
```
---

## 🛠️ `chmod` Command

### 🔹 What is `chmod`?
`chmod` stands for **Change Mode**. It’s used to change the **permissions** of files and directories.

### 🔹 Linux File Permissions
Each file/directory has:
- **User (u)** – Owner
- **Group (g)**
- **Others (o)** – Everyone else

And three permissions:
- **Read (r = 4)**
- **Write (w = 2)**
- **Execute (x = 1)**

### 🔹 Syntax
```bash
chmod [options] MODE FILE
```

#### Modes:
1. **Symbolic mode**:
   ```bash
   chmod u+x file    # Add execute to user
   chmod go-w file   # Remove write from group and others
   chmod a=r file    # Set read-only for all
   ```

2. **Numeric mode**:
   - Format: `OWNER GROUP OTHERS`
   - Each digit = sum of permission bits

   | Number | Permission |
   |--------|------------|
   | 7      | rwx        |
   | 6      | rw-        |
   | 5      | r-x        |
   | 4      | r--        |
   | 3      | -wx        |
   | 2      | -w-        |
   | 1      | --x        |
   | 0      | ---        |

   ```bash
   chmod 755 script.sh   # rwxr-xr-x
   chmod 644 file.txt    # rw-r--r--
   ```

### 🔹 Examples
```bash
chmod 700 secret.txt       # Only owner has full access
chmod +x myscript.sh       # Add execute permission
chmod u=rwx,g=rx,o= file   # Set specific permissions


chmod 000 devops.txt

cat devops.txt   # Check by cat


chmod 444 devops.txt
       (or)
chmod +r devops.txt


chmod 766 devops.txt
      (or)
chmod u+rwx,go+rw devops.txt


chmod 777 devops.txt
       (or)
chmod ugo+rwx devops.txt


chmod u+x file.txt  # Adds execute permission for the user
chmod g+w file.txt  # Adds write permission for the group


chmod o-r file.txt  # Removes read permission for others
chmod u-w file.txt  # Removes write permission for the user


chmod u=rwx,g=rx,o=r file.txt  # Sets permissions explicitly
chmod -v 644 file.txt --> what changes done it will show.
```
---

## 📈 Real-World Use Case

### Automatically restrict others from reading your files:
```bash
umask 077
touch private.txt
ls -l private.txt
# -rw-------
```

### Make a script executable:
```bash
chmod +x deploy.sh
./deploy.sh
```

---

## 📌 What is `chown` in Linux?

### 🔹 Definition:
`chown` stands for **change ownership**. It is used to change the **user** and/or **group ownership** of a file or directory.

```

## 🔹 Syntax:
```bash
chown [OPTIONS] USER[:GROUP] FILE...
```

- `USER`: The username or user ID to set as the new owner.
- `GROUP`: (Optional) The group name or group ID.
- `FILE`: The target file or directory.

---

### 🔹 Example:
```bash
chown balaji:balaji myfile.txt
```
This sets:
- **Owner** to `balaji`
- **Group** to `balaji`

---

## 🔹 Commonly Used Options:

| Option | Description |
|--------|-------------|
| `-R`   | Recursively change ownership of directory and its contents |
| `-v`   | Verbose mode; displays files as ownership is changed |
| `-f`   | Suppress most error messages |
| `--reference=RFILE` | Use the owner and group of RFILE instead of specifying USER:GROUP |

---

---

### 🔹 Use Cases:
- Fixing ownership after copying/moving files with `sudo`
- Setting correct owner/group for web server files
- Changing ownership in shared folders for collaboration
---

### 📘 Example Scenario:

## ✅ Examples:

### 1. Change the owner of a file:
```bash
chown balaji file.txt
```

### 2. Change the owner and group:
```bash
chown balaji:balaji file.txt
```

### 3. Change group only (can use `:`):
```bash
chown :devops file.txt
```

### 4. Change ownership recursively:
```bash
chown -R balaji:balaji /home/balaji/project/
```

### 5. Change ownership based on a reference file:
```bash
chown --reference=ref.txt file.txt
```

## 🔐 Who Can Use `chown`?
Only the **root user** (or with `sudo`) can change the ownership of files. Regular users **cannot** use `chown` to give ownership of a file to another user.

---

## 🔄 `chown` vs `chmod`

| Feature          | `chown`                        | `chmod`                         |
|------------------|--------------------------------|---------------------------------|
| Purpose          | Changes **owner and group**    | Changes **permissions**         |
| Affects          | Ownership                      | Read/Write/Execute access rights |
| Example Use      | `chown user:group file`        | `chmod 755 file`                |
| Used By          | Admins managing ownership      | Users/Admins managing access    |
| Recursive Option | `-R`                           | `-R`                            |


1.  **`chown` Example**:
   ```bash
   chown balaji:devops script.sh
   ```
   Now, user `balaji` and group `devops` own `script.sh`.

2. **`chmod` Example**:
   ```bash
   chmod 755 script.sh
   ```
   Sets permissions: Owner can read/write/execute; Group and Others can read/execute.

---

### 🔐 Summary:

- **`chown`** = WHO owns the file  
- **`chmod`** = WHAT they can do with the file
---
# SCP vs RSYNC – With Password and Key-Based Authentication

This document provides examples and explanations for using `scp` and `rsync` commands with both **password-based** and **key-based** SSH authentication.

---

## 📦 SCP (Secure Copy)
Used to securely copy files/folders between local and remote systems using SSH.

### 🔑 1. SCP with Password-Based Authentication
```bash
scp file.txt user@remote_host:/remote/directory/
```
> Prompts for the password of `user@remote_host`.

📌 **Example:**
```bash
scp report.txt balaji@192.168.1.100:/home/balaji/reports/
```

---

### 🔐 2. SCP with Key-Based Authentication
```bash
scp -i /path/to/key.pemfile.txt user@remote_host:/remote/directory/
```

📌 **Example:**
```bash
scp -i /path/to/key.pem report.txt balaji@192.168.1.100:/home/balaji/reports/
```

💡 **Tip:** Ensure the privte key(Pem) file  on the system in which u execute scp or rsync.

---

## ⚙️ RSYNC (Remote Sync)
Efficiently copies files/folders, syncing only differences using SSH by default.

### 🔑 3. Rsync with Password-Based Authentication
If SSH password is required, just use normal syntax:
```bash
rsync -avz file.txt user@remote_host:/remote/directory/
```
> Prompts for password via SSH.

📌 **Example:**
```bash
rsync -avz /var/log/syslog balaji@192.168.1.100:/home/balaji/logs/
```

🛑 **Note:** For automated password login, consider using `sshpass` (not recommended for production):
```bash
sshpass -p 'password' rsync -avz file.txt user@remote_host:/remote/directory/
```

---

### 🔐 4. Rsync with Key-Based Authentication
```bash
rsync -avz -e "ssh -i /path/to/key.pem" file.txt user@remote_host:/remote/directory/
```

📌 **Example:**
```bash
rsync -avz -e "ssh -i /path/to/key.pem" /var/log/syslog balaji@192.168.1.100:/home/balaji/logs/
```

---

## 🧠 Comparison Table

| Feature          | SCP                                   | RSYNC                                                  |
|------------------|----------------------------------------|---------------------------------------------------------|
| Protocol         | SSH                                    | SSH                                                     |
| Incremental      | ❌ No                                   | ✅ Yes                                                   |
| Directory Support| ✅ Yes (use `-r`)                      | ✅ Yes (default)                                         |
| Compression      | ❌ No (native)                         | ✅ Yes (`-z`)                                            |
| Resume Support   | ❌ No                                   | ✅ Yes (`--partial`)                                     |
| Syntax Simplicity| ✅ Simple                               | ⚠️ Slightly complex for custom options                  |

---

## 📁 Directory Examples

### SCP Recursive Directory Copy
```bash
scp -r myfolder/ user@host:/remote/dir/
```

### RSYNC Directory Sync with Compression and Progress
```bash
rsync -avz --progress myfolder/ user@host:/remote/dir/
```

## 📌 Notes

- For **`.pem` file**, ensure it has the correct permission:
  ```bash
  chmod 400 key.pem
  ```

- If using EC2:
  - Default user for Amazon Linux: `ec2-user`
  - Ubuntu: `ubuntu`
  - RedHat/CentOS: `ec2-user` or `centos`

- Always **quote paths** if they contain spaces.