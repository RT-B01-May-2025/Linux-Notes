# Linux Command Guide

---
## `tr` Command (Translate Characters)
The `tr` command is used to translate or delete characters from input provided via stdin.

### Syntax
```bash
cat demo.txt | sort | tr [a-z] [A-Z]  # Converts lowercase to uppercase
```

### Use Case
- Format output (like logs or reports) to a specific case.
- Clean or normalize input data.

---

## Linux Editors

### `vi` Editor
A powerful, standard editor available on all Unix/Linux systems.

```bash
vi demo.txt     # Open file
:wq             # Save and exit
:q!             # Quit without saving
:q              # Quit if no changes
```

#### Navigation
```bash
:se nu        # Show line numbers
:se nonu      # Hide line numbers
:90           # Go to line 90
:/nginx:1.14.2 # Search for 'nginx:1.14.2'
:d           # Delete current (cursor) line
:u           # Undo
:5,10d       # Delete from line 5 to 10
```

### Use Case
- System administrators use `vi` to quickly edit config files.
- Lightweight and efficient on low-resource servers.

---

### `nano` Editor
A beginner-friendly text editor in Linux.

```bash
nano demo.txt
sudo yum install nano -y     # Install nano if not available
```

#### Commands
- Ctrl+O  → Save
- Ctrl+X  → Exit

### Use Case
- Quick and intuitive editing of small files or scripts.

---

## `find` Command (Search Files & Directories)
Used to search for files and directories based on different filters.

### Syntax & Examples
```bash
find . -type f -empty                 # Find empty files in current directory
find ~ -type f -empty                # Find empty files in home directory
find /tmp -type f -empty            # Find empty files in /tmp
find . -type d -name <dirName>      # Search directory by name

find . -name deployment.yaml         # Case-sensitive search
find . -iname deployment.yaml        # Case-insensitive search
find . -type f -perm 0777            # Files with 777 permissions

find . -mtime 1                      # Modified exactly 1 day ago
find . -mtime -1                     # Modified less than 1 day ago
find . -mtime +1                     # Modified more than 1 day ago

find / -mmin -5   # It will locate/display the files which modified less than 5 minutes ago.

find ./ -type f -name "*.txt"        # Find all .txt files

find /var/log -type f -name "*.log" -size +5M # Find files ending with .log and file size > 5M

find /var/tmp -type f -name "*.tmp" -delete  #Find and delete .tmp files

find . -maxdepth 1 -type f #Find only at top-level (depth 1)

find . -mindepth 2 -type d #Find directories deeper than 2 levels

find /var/log -name "*.log" -mtime +30 -exec rm -f {} \; # Tip for DevOps Use Case Clean up logs older than 30 days:


find . -name "*.sh" -exec chmod +x '{}' \; # Find all .sh files  and set executable permissions to all sh files in current directory.

# The argument '{}' inserts each found file into the chmod command line. The \; argument indicates the exec command line has ended.

find . -name "*.*" -ls | awk '{print $7 " " $11}' | sort -rn | head -n 10 # Find ten largest files in the current directory and recursion through all subdirectories


```

### Use Case
- Locate old log files for cleanup.
- Search configuration files across directory structures.
- Security scans for permission issues.

---

## `sed` Command (Stream Editor)
Used for parsing and transforming text in files without opening them.

### Syntax & Examples
```bash
sed -i 's/unix/linux/' abc.txt          # Replace first occurrence
sed -i -z 's/unix/linux/2' abc.txt      # Replace 2nd occurrence
sed -i 's/unix/linux/g' abc.txt         # Replace all occurrences

sed  -i '3 s/unix/linux/' abc.txt        # Replace on line 3
sed -i '3 s/am/was/p' sed.txt           # Duplicate replaced line
sed -n '/404/p' application.log         # Print only replaced lines
sed -i '/^$/d' abc.txt                  # Delete Blank Lines

sed -i '/This is Balaji Reddy/i\RushiTechnologies' abc.txt #Insert Line Before Match
sed -i '/This is Balaji Reddy/a\16 Years of Exp in IT' abc.txt #Append Line After Match

sed -i '/This/c\Balalji Reddy' abc.txt #Change Entire Line on Match.Replaces the full line where This is found.

sed -i -e 's/foo/bar/' -e 's/dev/prod/' config.txt #Use Multiple Commands,Chains two substitutions.

sed '1,3 s/unix/linux/' abc.txt      # Replace in line range
sed '5d' filename.txt                # Delete line 5
sed '3,6d' filename.txt              # Delete lines 3 to 6
sed -n '60,80p' filename             # To display lines 60 to 80 of a file using sed

```

### Use Case
- Modify large files programmatically.
- Replace strings in configuration or data files.
- Scripted cleanup of logs or report files.

---

## `who` Command (User Sessions)
Displays users currently logged into the system.

```bash
who -H    # Display with headers
```

## `w` Command
Shows who is logged in and what they are doing.

```bash
w
```

### Use Case
- Monitor logged-in users.
- Check terminal activity.
- System performance monitoring.
---

