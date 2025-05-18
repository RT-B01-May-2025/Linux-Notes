# 📦 `zip` Command in Linux

The `zip` command is used to compress files and directories into a `.zip` archive. It's widely used for reducing file size and combining multiple files into a single package for storage or transfer.

---

## 🔧 Basic Syntax

```bash
zip [options] zipfile.zip file1 file2 ...
```

---

## 📘 Commonly Used Options

| Option | Description |
|--------|-------------|
| `-r`   | Recursively include files in directories |
| `-e`   | Encrypt the contents of the zip file |
| `-q`   | Quiet mode (no output to terminal) |
| `-v`   | Verbose mode (shows progress) |
| `-9`   | Maximum compression |
| `-0`   | No compression (store only) |
| `-x`   | Exclude specific files |
| `-m`   | Move files into archive (delete originals) |
| `-j`   | Junk the path (store just the file names) |
| `-T`   | Test the integrity of the archive |
| `-FS`  | Save only changed files (freshen and update) |

---

## ✅ Examples and Real-Time Use Cases

### 1. **Zip a Single File**

```bash
zip archive.zip file.txt
```

👉 *Compresses `file.txt` into `archive.zip`*

---

### 2. **Zip Multiple Files**

```bash
zip archive.zip file1.txt file2.txt file3.txt
```

👉 *Creates `archive.zip` containing multiple files.*

---

### 3. **Zip an Entire Directory**

```bash
zip -r archive.zip my_folder/
```

👉 *Recursively zips the contents of `my_folder`.*

---

### 4. **Zip with Password Protection**

```bash
zip -e secure.zip secret.txt
```

👉 *Prompts for a password and encrypts `secret.txt`.*

---

### 5. **Exclude Specific Files**

```bash
zip -r archive.zip folder/ -x "*.log" "*.tmp"
```

👉 *Zips `folder` but excludes `.log` and `.tmp` files.*

---

### 6. **Maximum Compression**

```bash
zip -9 highcomp.zip data.csv
```

👉 *Uses best compression for `data.csv`.*

---

### 7. **Suppress Output (Quiet Mode)**

```bash
zip -q archive.zip file1 file2
```

👉 *No output shown during zip process.*

---

### 8. **Test Integrity of a Zip File**

```bash
zip -T archive.zip
```

👉 *Checks if the zip file is valid and uncorrupted.*

---

### 9. **Move Files into Archive**

```bash
zip -m archive.zip file1.txt
```

👉 *Adds `file1.txt` to archive and deletes the original.*

---

### 10. **Zip Without Folder Paths**

```bash
zip -j archive.zip /path/to/folder/*
```

👉 *Adds files to archive without their directory structure.*

---

## 🧪 Practical Use Cases

- 🔐 Sending encrypted documents via email.
- 🗜️ Archiving log files to save disk space.
- 📁 Packaging project folders for sharing or uploading.
- 🧹 Backing up code with exclusions like `*.log` and `*.tmp`.
- 🔁 Creating automated scripts to zip and move old data.
---

# unzip Command in Linux

The `unzip` command in Linux is used to extract files from a `.zip` archive. It is part of the `zip` package utilities and is commonly used to decompress `.zip` files created by the `zip` command or by other ZIP archiving tools.

---

## 🔹 Basic Syntax
```bash
unzip [options] zipfile.zip [file_to_extract] -d [destination_folder]
```

---

## 🔹 Commonly Used Options

| Option | Description |
|--------|-------------|
| `-l`   | List contents of the zip file without extracting |
| `-v`   | Verbose list (shows more info than `-l`) |
| `-d`   | Specify the directory to extract files to |
| `-n`   | Never overwrite existing files |
| `-o`   | Overwrite files without prompting |
| `-q`   | Quiet mode (suppresses output) |
| `-j`   | Junk paths (extracts files to current dir without creating folder structure) |
| `-x`   | Exclude specific file(s) from extraction |
| `-P`   | Specify password for encrypted ZIP files (insecure via command line) |

---

## 🔹 Examples

### ✅ Extract a ZIP file in the current directory
```bash
unzip archive.zip
```

### ✅ Extract to a specific directory
```bash
unzip archive.zip -d /home/user/extracted/
```

### ✅ View contents without extracting
```bash
unzip -l archive.zip
```

### ✅ Extract a specific file
```bash
unzip archive.zip file.txt
```

### ✅ Extract without overwriting existing files
```bash
unzip -n archive.zip
```

### ✅ Overwrite files silently
```bash
unzip -o archive.zip
```

### ✅ Extract ignoring folder structure
```bash
unzip -j archive.zip
```

### ✅ Extract all except specific files
```bash
unzip archive.zip -x "secret.txt" "ignore/*.log"
```

### ✅ Extract password-protected archive
```bash
unzip -P yourpassword archive.zip
```

---

## 🔹 Real-Time Use Cases

1. **Extract log files from a backup archive:**
   ```bash
   unzip logs_backup.zip -d /var/logs/backup/
   ```

2. **Deploy code from a zip package:**
   ```bash
   unzip project-release.zip -d /var/www/html/project/
   ```

3. **Extract a large zip file quietly in the background:**
   ```bash
   unzip -q large_dataset.zip -d ./data/
   ```

4. **Unzip attachments in a mail automation script:**
   ```bash
   unzip attachment.zip -d /tmp/mail_attachments/
   ```
---
# tar Command in Linux

The `tar` command in Linux is used to **create, extract, and manage archive files**, commonly with `.tar`, `.tar.gz`, `.tgz`, or `.tar.bz2` extensions. It's frequently used for **backup, compression, and packaging files**.

---

## 📦 Basic Syntax:

```bash
tar [OPTIONS] [ARCHIVE_FILE] [FILES/DIRECTORIES...]
```

---

## ✅ Commonly Used Options:

| Option | Description |
|--------|-------------|
| `-c`   | Create a new archive |
| `-x`   | Extract files from archive |
| `-t`   | List contents of archive |
| `-v`   | Verbose (show progress) |
| `-f`   | Specify archive file name |
| `-z`   | Compress using gzip (`.tar.gz`) |
| `-j`   | Compress using bzip2 (`.tar.bz2`) |
| `-J`   | Compress using xz (`.tar.xz`) |

---

## 📂 Real-Time Examples:

### 1. **Create a `.tar` archive:**
```bash
tar -cvf backup.tar /home/user/data
```

### 2. **Create a `.tar.gz` compressed archive:**
```bash
tar -czvf backup.tar.gz /home/user/data
```

### 3. **Extract a `.tar` archive:**
```bash
tar -xvf backup.tar
```

### 4. **Extract a `.tar.gz` archive:**
```bash
tar -xzvf backup.tar.gz
```

### 5. **List contents of archive:**
```bash
tar -tvf backup.tar
```

### 6. **Extract to a specific directory:**
```bash
tar -xvf backup.tar -C /tmp/extract_folder
```

### 7. **Create a `.tar.xz` archive:**
```bash
tar -cJvf backup.tar.xz /home/user/data
```

### 8. **Add files to an existing tar archive:**
```bash
tar -rvf backup.tar newfile.txt
```

### 9. **Extract specific file from archive:**
```bash
tar -xvf backup.tar filename.txt
```

---

## 📌 Notes:
- `.tar` is an archive, not compressed.
- `.tar.gz`, `.tgz` is a gzip-compressed archive.
- `.tar.bz2`, `.tar.xz` are alternatives with better compression.
---
# echo Command in Linux

The `echo` command is used to display **text or string values** on the terminal. It is commonly used in **shell scripts**, **printing variables**, **creating files**, and for **debugging**.

---

## 🔧 Basic Syntax:
```bash
echo [options] [string...]
```

---

## ✅ Common Use Cases and Examples

### 1. Print a Simple String
```bash
echo "Hello, World!"
```
**Output:** `Hello, World!`

---

### 2. Print Value of a Variable
```bash
name="Linux"
echo "Welcome to $name"
```
**Output:** `Welcome to Linux`

---

### 3. Create a File with Text
```bash
echo "This is a sample text" > file.txt
```
**Creates a file and writes the text into it.**

---

### 4. Append Text to a File
```bash
echo "Another line" >> file.txt
```
**Appends the text without overwriting.**

---

### 5. Suppress New Line (-n)
```bash
echo -n "Printing without newline"
```
**Output:** Text stays on the same line.

---

### 6. Interpret Escape Characters (-e)
```bash
echo -e "Line1\nLine2\tTabbed"
```
**Output:**
```
Line1
Line2    Tabbed
```

| Escape Sequence | Description          |
|-----------------|----------------------|
| \n             | New line             |
| \t             | Tab space            |
| \\            | Backslash `\`       |
| \"             | Double quote `"`     |
| \a             | Alert (beep)         |

---

### 7. Print Backslash or Quotes
```bash
echo -e "The path is C:\\Program Files\\"
echo -e "\"Quoted Text\""
```

---

### 8. Use in Shell Scripts
```bash
#!/bin/bash
echo "Script is starting..."
```

---

## 📋 Real-Time Use Cases

| Use Case         | Description                          |
|------------------|--------------------------------------|
| Display messages | Show success/failure info in scripts |
| Variable debugging | Print variables during script execution |
| File generation  | Quickly create files with text       |
| Logs             | Append time-stamped entries to logs  |

---

## 🧪 Practice Tip:
```bash
for i in {1..3}; do echo "Line $i"; done
```
**Prints Line 1, Line 2, Line 3**
---

# `more` Command in Linux

The `more` command in Linux is a **pager utility** used to **view the contents of a file one screen at a time**. It is especially useful for reading long text files in the terminal.

---

## 🔹 Syntax:
```bash
more [options] filename
```

---

## 🔹 Basic Usage:
```bash
more filename.txt
```
- Opens `filename.txt` and displays it page by page.
- You can scroll through the content using keyboard controls.

---

## 🔹 Common Navigation Keys:
| Key         | Action                                   |
|-------------|------------------------------------------|
| `Space`     | Go to the next page                      |
| `Enter`     | Scroll down one line                     |
| `b`         | Go back one page                         |
| `q`         | Quit (exit the `more` command)           |
| `/pattern`  | Search for `pattern`                     |
| `n`         | Go to next match of search pattern       |

---

## 🔹 Common Options:
| Option         | Description                                                |
|----------------|------------------------------------------------------------|
| `-d`           | Shows "Press space to continue..." prompt with message     |
| `-c`           | Clears screen before displaying each page                  |
| `-p`           | Similar to `-c` but suppresses scrolling                    |
| `+n`           | Starts displaying from line number `n`                     |
| `+/pattern`    | Starts displaying from the first match of `pattern`        |

---

## 🔹 Examples:

### 1. View a long file:
```bash
more /var/log/syslog
```

### 2. Start from a specific line:
```bash
more +100 filename.txt
```
- Opens the file starting from line 100.

### 3. Start from a search pattern:
```bash
more +/ERROR logfile.log
```
- Opens the file and jumps to the first line containing "ERROR".

### 4. Use with other commands (piping):
```bash
cat longfile.txt | more
```
or
```bash
ps aux | more
```

---

## 🔹 Real-time Use Cases:
- Viewing system logs:  
  `more /var/log/messages`
- Reading large configuration files:  
  `more /etc/ssh/sshd_config`
- Reviewing outputs of long command pipelines:  
  `dmesg | more`

---

## 🔹 Difference Between `more` and `less`:
| Feature          | `more`       | `less`          |
|------------------|--------------|------------------|
| Navigation       | Forward only | Forward and backward |
| Performance      | Basic        | Advanced          |
| Searching        | Limited      | Better search, highlight |
| Usability        | Older        | More powerful     |
---

# `less` Command in Linux

The `less` command is a **pager utility** used to view (but not edit) the contents of a file one screen at a time. It is commonly used to read **log files, configuration files, or command outputs** that are too large to fit on a single screen.

---

## 🔹 Basic Syntax

```bash
less [options] filename
```

---

## 🔹 Key Features

- Supports **scrolling forward and backward**.
- **Efficient for large files** – doesn't load the entire file into memory.
- Can search within the content.
- Works with **stdin** (standard input) from a pipeline.

---

## 🔹 Commonly Used Options

| Option | Description |
|--------|-------------|
| `-N`   | Show line numbers. |
| `-S`   | Do not wrap long lines (horizontal scroll). |
| `-X`   | Disable screen clearing after exit. |
| `-F`   | Automatically exits if the content fits on one screen. |
| `-E`   | Automatically exits at the end of the content. |
| `+F`   | Opens in **"follow mode"**, like `tail -f`. |
| `+<number>` | Starts displaying from the given line number. |

---

## 🔹 Useful Navigation Commands (Within `less`)

| Key | Action |
|-----|--------|
| `Space` | Move forward one screen |
| `b`     | Move backward one screen |
| `Enter` | Move forward one line |
| `q`     | Quit |
| `/search` | Search forward for "search" |
| `?search` | Search backward |
| `n` | Repeat previous search |
| `N` | Repeat previous search in reverse |

---

## ✅ Real-Time Use Cases

### 📄 1. View a Large File
```bash
less /var/log/syslog
```

---

### 🔍 2. Search for Specific Text
```bash
less /var/log/auth.log
```
Then type:
```
/failed
```

---

### 🔃 3. Follow a File Like `tail -f`
```bash
less +F /var/log/apache2/access.log
```

---

### 🔢 4. Display Line Numbers
```bash
less -N config.txt
```

---

### ↩ 5. View Output from Another Command
```bash
ps aux | less
```

---

### 📜 6. Avoid Wrapping Long Lines
```bash
less -S error.log
```

---

### 🧠 7. Read a File Starting from a Specific Line
```bash
less +1000 hugefile.log
```

---

## 📝 Tip

You can make `less` the default pager in scripts or for `man` pages:
```bash
export PAGER=less
```
---
# Soft Link and Hard Link in Linux with Examples

## 1. Hard Link

### What is a Hard Link?
A hard link is an additional name for an existing file. Both the original and the hard link refer to the same inode (i.e., same data on disk).

### Characteristics:
- Same inode number as the original file
- File data persists even if the original file is deleted
- Cannot link to directories
- Cannot span different filesystems

### Example:
```bash
# Create a file
echo "This is a test file" > original.txt

# Create a hard link
ln original.txt hardlink.txt

# List inode numbers
ls -li original.txt hardlink.txt
```
**Output:**
```
123456 -rw-r--r-- 2 user user 21 May 18 18:00 original.txt
123456 -rw-r--r-- 2 user user 21 May 18 18:00 hardlink.txt
```

### Modify Using Hard Link:
```bash
echo "New line added." >> hardlink.txt
cat original.txt
```
**Output:**
```
This is a test file
New line added.
```

## 2. Soft Link (Symbolic Link)

### What is a Soft Link?
A soft link is a shortcut to another file. It contains a path to the original file.

### Characteristics:
- Different inode than the original file
- Breaks if the target file is deleted
- Can link to directories
- Can span filesystems

### Example:
```bash
# Create a symbolic link
ln -s original.txt softlink.txt

# List symbolic link details
ls -l softlink.txt
```
**Output:**
```
lrwxrwxrwx 1 user user 12 May 18 18:02 softlink.txt -> original.txt
```

### Modify Using Soft Link:
```bash
echo "Edited via softlink." >> softlink.txt
cat original.txt
```
**Output:**
```
This is a test file
New line added.
Edited via softlink.
```

## 3. What Happens When the Original File is Deleted?
```bash
rm original.txt
cat hardlink.txt
cat softlink.txt
```
**Output:**
```
# hardlink.txt still works
This is a test file
New line added.
Edited via softlink.

# softlink.txt gives error
cat: softlink.txt: No such file or directory
```

## 4. Symbolic Link to a Directory
```bash
# Create a directory and file
mkdir mydir
echo "Hello from directory" > mydir/dirfile.txt

# Create symbolic link to directory
ln -s mydir mydir_link

# Access file via symbolic link
cat mydir_link/dirfile.txt
```
**Output:**
```
Hello from directory
```

---

## Summary Table

| Feature                | Hard Link              | Soft Link                    |
|------------------------|------------------------|------------------------------|
| Inode Shared           | Yes                    | No                           |
| File System            | Same only              | Can be different             |
| Works if target deleted| Yes                    | No (breaks)                  |
| Points to              | File's data (inode)    | File path                    |
| Can link directories?  | No                     | Yes                          |
| File size              | Same as original       | Small (path string)          |

---

This guide shows how to create and use both hard and soft links in Linux with real-world examples.
