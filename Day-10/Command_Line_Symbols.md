
# Linux Command Line Symbols – Detailed Guide with Examples

## 1. `#` – Comment Symbol
Used for comments in shell scripts or interactive shell.

```bash
# This is a comment
echo "Hello" # Inline comment
```

## 2. `$` – Variable Expansion
Used to reference variable values.

```bash
name="Balaji"
echo "Hello, $name"
echo $HOME # Prints your home directory path
```

## 3. `;` – Command Separator
Runs multiple commands sequentially, one after another.
```bash
echo "Hello"; echo "World"
# Output:
# Hello
# World
```

## 4. `&&` – Logical AND
Second command executes only if the first succeeds.

```bash
mkdir test && cd test
```

## 5. `||` – Logical OR
Executes second command only if first fails.

```bash
cd /fake || echo "Directory change failed"
```

## 6. `&` – Background Process
Runs a command in the background, returning control to the shell immediately.
```bash
sleep 30 &
echo "Executing Next Commands"
```

## 7. `|` – Pipe
Sends output of one command as input to another.
```bash
cat file.txt | grep "pattern"
```

## 8. `>` – Redirect Output (Overwrite)
Redirects standard output to a file, overwriting if file exists.

```bash
echo "Hello" > output.txt
```

## 9. `>>` – Redirect Output (Append)
Appends output to a file instead of overwriting.

```bash
echo "World" >> output.txt
```

## 10. `<` – Input Redirection
Reads input from a file instead of keyboard.

```bash
sort < names.txt
```
## 11. `1>` – Redirect Standard Output

```bash
ls /etc 1> error.log # Redirect out to a file.
ls /etc 1> /dev/null # Output is not shown or saved.
```

## 11. `2>` – Redirect Standard Error

```bash
ls /invalid 2> error.log # error saved to a file.
ls /invalid 2> /dev/null # Error messages are ignored not saved
```

## 12. 2>&1 - Redirect stderr to stdout
Redirect standard error (stderr) to the same location as standard output (stdout)

```bash
ls /etc /notexist > output.txt 2>&1  # Both stdout and stderr go to output.txt

ls /etc /notexist >  /dev/null 2>&1  # Both stdout and stderris completely suppressed(Silencing output (stdout/stderr)

# Crontan
corontab -e
* * * * * /path/to/script.sh > /dev/null 2>&1 # Silencing noisy cron jobs
```


## 13. `&>` – Redirect stdout and stderr Same as 2>&1
Redirects both standard output and standard error.

```bash
ls /etc /notexist &> output.log
```

## 14. `~` – Home Directory

```bash
cd ~
```

## 15. `*` – Wildcard (All Files)
Matches zero or more characters.
```bash
ls *.txt # Lists all files ending with .txt
rm test*.log 
```

## 16. `?` – Single Character Wildcard

```bash
ls file?.txt # Lists file1.txt, fileA.txt but not file10.txt
```

## 17. `{}` – Brace Expansion
Generates arbitrary strings.
```bash
echo file{1..3}.txt # # Output: file1.txt file2.txt file3.txt
```

## 18. `[]` – Character Set
Matches any one character within brackets.
```bash
ls file[123].txt  # # Lists file1.txt, file2.txt, file3.txt
```

## 19. `!` – Negation / History

```bash
ls file[!1].txt
!ls
```

## 20. `\` – Escape Character
Preserves literal value of next character.

```bash
echo "This is a \"quote\"" # Output: This is a "quote"
```

## 21. `` `command` `` – Deprecated(Older) Command Substitution

```bash
echo "Today is `date`" # Same as below but older syntax
```

## 22. `$(command)` – Preferred Command Substitution

```bash
echo "Today is $(date)" # Output: Today is [current date]
```

## 23. `()` – Subshell

```bash
(cd /tmp && ls)
```

## 24. `[[ ... ]]` – Advanced Condition Test

```bash
if [[ $name == "Balaji" ]]; then echo "Match"; fi
```

## 25. `[ ... ]` – Basic Condition Test

```bash
if [ -f /etc/passwd ]; then echo "Exists"; fi
```

## 26. `-` – Option Indicator

```bash
ls -l
```

## 27. `--` – End of Options

```bash
rm -- -file
```

## 28. `:` – Null Command

```bash
:
```

## 29. `#!` – Shebang Line

```bash
#!/bin/bash
```

## 30. `^` – Start of Line (Regex)

```bash
grep '^root' /etc/passwd
```

## 31. `$` – End of Line (Regex)

```bash
grep 'bash$' /etc/passwd
```
---

# 📝 Summary Table – Linux Command Line Symbols


## Wildcard and Filename Expansion Symbols

| Symbol | Meaning                             | Example              | Description                           |
|--------|-------------------------------------|----------------------|---------------------------------------|
| `*`    | Matches zero or more characters     | `ls *.txt`           | Lists all `.txt` files                |
| `?`    | Matches exactly one character       | `ls file?.txt`       | Matches `file1.txt`, not `file10.txt` |
| `[]`   | Matches one character inside brackets | `ls file[1-3].txt` | Matches `file1.txt`, `file2.txt`, `file3.txt` |

## Redirection Symbols

| Symbol | Meaning                     | Example                        | Description                               |
|--------|-----------------------------|--------------------------------|-------------------------------------------|
| `>`    | Redirect stdout to file     | `echo "Hello" > hello.txt`     | Overwrites `hello.txt` with "Hello"       |
| `>>`   | Append stdout to file       | `echo "Again" >> hello.txt`    | Appends "Again" to `hello.txt`            |
| `<`    | Redirect stdin from file    | `wc -l < file.txt`             | Counts lines in `file.txt`                |
| `2>`   | Redirect stderr to file     | `ls /no/such/dir 2> error.log` | Redirects error messages to `error.log`   |
| `&>`   | Redirect stdout and stderr  | `command &> output.log`        | All output → `output.log`                 |

## Pipe and Command Chaining Symbols

| Symbol | Meaning                  | Example                      | Description                                      |
|--------|--------------------------|------------------------------|--------------------------------------------------|
| `|`    | Pipe output              | `ls -l | grep txt`           | Passes output of `ls -l` to `grep`               |
| `||`   | OR (if previous fails)   | `mkdir dir || echo "Fail"`   | Executes echo if mkdir fails                     |
| `&&`   | AND (if previous passes) | `make && echo "Success"`     | Executes echo if make succeeds                   |
| `;`    | Run both regardless      | `echo Hi; echo Bye`          | Executes both commands                           |

## Background and Job Control

| Symbol | Meaning                     | Example        | Description                                   |
|--------|-----------------------------|----------------|-----------------------------------------------|
| `&`    | Run in background           | `sleep 60 &`   | Runs command in background                    |
| `fg`   | Foreground background job   | `fg %1`        | Brings job #1 to foreground                   |
| `jobs` | List background jobs        | `jobs`         | Lists current background jobs                 |

## Substitution and Expansion

| Symbol           | Meaning                  | Example            | Description                                 |
|------------------|--------------------------|--------------------|---------------------------------------------|
| `` `command` ``  | Command substitution     | `` echo `date` ``  | Inserts output of date                      |
| `$(command)`     | Modern command sub       | `echo $(date)`     | More readable form                          |
| `$((expression))`| Arithmetic evaluation    | `echo $((2+3))`    | Evaluates math expression                   |
| `${var}`         | Variable expansion       | `echo ${HOME}`     | Shows user home dir                         |

## Permissions and Path Symbols

| Symbol | Meaning                | Example         | Description                                |
|--------|------------------------|-----------------|--------------------------------------------|
| `~`    | Home directory         | `cd ~`          | Changes to user’s home directory           |
| `.`    | Current directory      | `./script.sh`   | Executes from current directory            |
| `..`   | Parent directory       | `cd ..`         | Moves up one level                         |
| `/`    | Root/path separator    | `cd /var/log`   | Navigates to full path                     |
| `-`    | Previous directory     | `cd -`          | Switches to last directory                 |

## Shell Scripting Special Characters

| Symbol | Meaning                | Example             | Description                                 |
|--------|------------------------|---------------------|---------------------------------------------|
| `#`    | Comment                | `# comment`         | Line ignored by shell                       |
| `!`    | Negation/history       | `#!/bin/bash`       | Starts script with interpreter              |
| `$`    | Variable access        | `echo $USER`        | Prints current user                         |
| `\`   | Escape character       | `echo \$HOME`      | Prints literal `$HOME`                      |
| `' '`  | Single quotes (no expand) | `'${USER}'`     | Prints literal ${USER}                      |
| `" "`  | Double quotes (expand) | `"${USER}"`         | Expands to current username                 |
| `:`    | Null operation         | `: > file.txt`      | Clears file without deleting it             |

## Brace Expansion

| Symbol   | Meaning               | Example                 | Description                                 |
|----------|-----------------------|-------------------------|---------------------------------------------|
| `{}`     | Pattern expansion     | `echo file{1,2,3}.txt`  | Expands to file1.txt file2.txt file3.txt    |
| `{1..5}` | Range expansion       | `echo {1..5}`           | Expands to 1 2 3 4 5                         |

## Here Document & Here String

| Symbol | Meaning                 | Example                         | Description                           |
|--------|-------------------------|----------------------------------|---------------------------------------|
| `<<`   | Here document           | `cat <<EOF ... EOF`              | Multi-line input block                |
| `<<<`  | Here string             | `grep root <<< "root:x:0:0"`     | Feeds a string into command           |

## 10. Exit Status and History

| Symbol | Meaning                   | Example      | Description                                |
|--------|---------------------------|--------------|--------------------------------------------|
| `$?`   | Exit status               | `echo $?`    | Shows success (0) or failure (non-zero)    |
| `!!`   | Repeat last command       | `sudo !!`    | Re-runs previous command with sudo         |
| `$_`   | Last argument of previous | `echo $_`    | Prints last argument from last command     |

## Sample Shell Script

```bash
#!/bin/bash
# Backup script

SRC_DIR="$HOME/documents"
DEST_DIR="/mnt/backup"
DATE=$(date +%F)

mkdir -p "$DEST_DIR"

tar -czf "$DEST_DIR/backup_$DATE.tar.gz" "$SRC_DIR" &> /dev/null && echo "Backup successful." || echo "Backup failed."

ls -lh "$DEST_DIR" | grep "$DATE"
```
