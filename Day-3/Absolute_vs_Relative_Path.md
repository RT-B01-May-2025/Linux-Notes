# Absolute Path vs Relative Path in Linux

## 📁 What is a Path in Linux?
A **path** in Linux specifies the location of a file or directory in the filesystem. There are two main types:
- **Absolute Path**
- **Relative Path**

---

## 🔹 Absolute Path – In Detail

### ✅ Definition:
An **absolute path** is the **complete path** that starts from the **root directory (`/`)** and specifies the complete location of a file or directory.

### ✅ Characteristics:
- Always Starts with a `/` (root directory)
- Does **not depend on your current location**
- Provides a complete and unambiguous path to a file or directory, regardless of the current directory.

### ✅ Syntax:
`/root/parent/child/filename`

### ✅ Examples:
```bash
/etc/passwd
/home/balaji/docs/resume.pdf
/var/log/syslog
```

### ✅ Real-Time Use Case:
You're writing a **cron job** script to back up a config file:
```bash
cp /etc/nginx/nginx.conf /backup/nginx.conf.backup
```

---

## 🔸 Relative Path – In Detail

### ✅ Definition:
A **relative path** specifies the location **relative to the current working directory**.

### ✅ Characteristics:
- **Does NOT start with `/`**
- Starts from the current working directory (pwd). 
- Specifies a location in relation to the user's current position in the file system. 
- Uses `.` for current directory and `..` for parent
- Depends on where you are in the terminal

### ✅ Syntax:
`./child/filename` or `../sibling_folder/file.txt`

### ✅ Examples:
Assume you are in: `/home/balaji`

```bash
cd docs/
cat ./notes.txt
cd ../scripts
```

### ✅ Real-Time Use Case:
While working on a project:
```bash
cd myproject
ls ../otherproject/config.yaml
```

---

## 🔁 Comparison Table

| Feature              | Absolute Path                     | Relative Path                          |
|----------------------|------------------------------------|-----------------------------------------|
| Starts With          | `/` (root)                         | Does **not** start with `/`             |
| Based On             | Root directory                     | Current working directory               |
| Context Dependency   | Independent                        | Dependent on current directory          |
| Stability            | Always reliable                    | May break if directory changes          |
| Used In              | Scripts, crons, services           | Terminal navigation, temporary scripts  |

---

## 📘 Additional Examples

```bash
# Absolute
cp /home/balaji/scripts/install.sh /usr/local/bin/

# Relative (assuming you're in /home/balaji)
cp ./scripts/install.sh ../bin/
```