# Bash Script README

This README provides a comprehensive overview of basic Bash scripting, common commands, file manipulation, permission management, redirection, piping, arithmetic operations, and debugging techniques.

---

**Table of Contents**

1. [Running Scripts](#running-scripts)
2. [Basic Commands](#basic-commands)
3. [File and Directory Operations](#file-and-directory-operations)
4. [User and Permission Management](#user-and-permission-management)
5. [Redirection and Piping](#redirection-and-piping)
6. [Text Manipulation](#text-manipulation)
7. [Bash Operators](#bash-operators)
8. [Numerical Comparison Operators](#numerical-comparison-operators)
9. [Mathematical and Logical Expressions](#mathematical-and-logical-expressions)
10. [Variables in Bash](#variables-in-bash)
11. [Bash Control Flow](#bash-control-flow)
12. [Debugging Bash Scripts](#debugging-bash-scripts)
13. [Other Utilities](#other-utilities)
14. [Environment Variables](#environment-variables)

---

## Running Scripts

To run a Bash script:

- `./scriptName.sh` — Runs the script in a subshell. Variables and changes within the script do not affect the current shell.
- `. scriptName.sh` or `source scriptName.sh` — Runs the script in the current shell, allowing access to variables and functions defined in the script.

---

## Basic Commands

- `pwd` — Display the current directory.
- `su account_name` — Switch to another user account.
- `ls` — List directory contents.
  - `ls -l` — Detailed listing with permissions.
  - `ls -a` — Show hidden files (files starting with `.`).
  - `ls -i <filename>` — Show inode number of a file.
- `cd` — Change directory.
- `touch <filename>` — Create an empty file.
- `rm <filename>` — Remove a file.
  - `rm -r` — Remove a non-empty directory.
  - `rmdir` or `rm -d` — Remove an empty directory.
- `clear` — Clear the terminal screen.
- `echo "message"` — Print a message to the terminal.
- `exit` — Exit the current shell session.

---

## File and Directory Operations

- `mkdir <directory>` — Create a directory.
  - `mkdir -p <parent/child>` — Create a directory along with its parent directories.
- `cp <file> <destination>` — Copy a file to a destination.
- `cat <filename>` — Display the content of a file.
- `head <filename>` — Display the first part of a file.
- `tail <filename>` — Display the last part of a file.
- `find -name '*.php' | wc -l` — Count the number of `.php` files in a directory.
- `ln -s <target> <link>` — Create a symbolic link to a file or directory.

---

## User and Permission Management

- `whoami` — Display the current user.
- `chown <user>:<group> <file/directory>` — Change file or directory ownership.
- `chgrp <group_name> <file/directory>` — Change the group ownership.
- `chmod` — Change file permissions.
  - Example: `chmod 755 <filename>` — Full permissions for the owner (rwx), read-execute for group and others.
  - Example: `chmod 155 <filename>` — Execute-only for the owner, read-execute for group and others.
- `passwd <username>` — Change the password for a user.

**File Permissions Overview**:

- Permission: rwx for owner, r-x for group, r-x for all.
- Binary Format: 111 for owner, 101 for group, 101 for all.
- Decimal Format: 755.

---

## Redirection and Piping

- `>` — Redirect output to a file, overwriting it.
- `>>` — Append output to a file.
- `|` — Pipe the output from one command as input to another.
  - Example: `ls | grep "n"` — List files and pipe the output to `grep` to search for filenames containing "n."
- `2>` — Redirect error messages to a file.
- `&>` — Redirect both stdout and stderr to a file.

---

## Text Manipulation

- `grep "word" <filename>` — Search for a word in a file.
- `cut -d"delimiter" -f<field number> <filename>` — Extract sections from each line of a file.
- `tr "char1" "char2"` — Translate or replace characters in a file.
- `column -t <filename>` — Format the output into tabular form.
- `awk '{print $2, $3, $NF}' <filename>` — Print specific fields from each line.
- `sed 's/pattern/replacement/g' <filename>` — Search and replace text globally in a file.
- `sort <filename>` — Sort the lines in a file.
- `wc -l <filename>` — Count the number of lines in a file.

---

## Bash Operators

- **`&&`** — Logical AND (combines multiple commands).
- **`||`** — Logical OR.
- **`>`** — Greater than.
- **`<`** — Less than.
- **`=`**, **`!=`** — String comparison.

---

## Numerical Comparison Operators

- **`-eq`**: Checks if two numbers are equal.

  ```bash
  if [ "$a" -eq "$b" ]; then
      echo "a is equal to b"
  fi
  ```

- **`-ne`**: Checks if two numbers are not equal.

  ```bash
  if [ "$a" -ne "$b" ]; then
      echo "a is not equal to b"
  fi
  ```

- **`-lt`**: Checks if the left number is less than the right number.

  ```bash
  if [ "$a" -lt "$b" ]; then
      echo "a is less than b"
  fi
  ```

- **`-le`**: Checks if the left number is less than or equal to the right number.

  ```bash
  if [ "$a" -le "$b" ]; then
      echo "a is less than or equal to b"
  fi
  ```

- **`-gt`**: Checks if the left number is greater than the right number.

  ```bash
  if [ "$a" -gt "$b" ]; then
      echo "a is greater than b"
  fi
  ```

- **`-ge`**: Checks if the left number is greater than or equal to the right number.
  ```bash
  if [ "$a" -ge "$b" ]; then
      echo "a is greater than or equal to b"
  fi
  ```

### Example of Using Comparison Operators

```bash
#!/bin/bash

a=10
b=20

if [ "$a" -eq "$b" ]; then
    echo "a is equal to b"
elif [ "$a" -lt "$b" ]; then
    echo "a is less than b"
elif [ "$a" -gt "$b" ]; then
    echo "a is greater than b"
else
    echo "a is not equal to b"
fi
```

### Important Notes

- **Quotes**: Always quote your variables to prevent errors when they are empty or contain spaces.
- **Brackets**: You can use `[ ]` or `[[ ]]` for tests, but `[[ ]]` is generally preferred in modern Bash scripts for its additional features, such as pattern matching and logical operators.

---

## Mathematical and Logical Expressions

- Arithmetic operations:
  - `expr` — Example: `z=$(expr 1 + 2)`
  - `let` — Example: `let z=1+2`
  - `$((expression))` — Example: `z=$((1 + 2))`
  - Increment and decrement: `((z++))` or `((x+=2)`
- Logic gates in bash:
  - `-a` — AND.
  - `-o` — OR.

---

## Variables in Bash

- Global Variables: `var=15` — Accessible throughout the script.
- Local Variables: `local var=15` — Accessible only within the function.
- Exporting Variables:
  - `export var=15` — Makes the variable accessible in child processes.
- Special Variables:
  - `$#` — Number of positional parameters.
  - `$?` — Exit status of the last command.
  - `$$` — Process ID of the current shell.
  - `$!` — Process ID of the last background command.

---

## Bash Control Flow

- `if` statements:
  ```bash
  if [ condition ]; then
    # commands
  fi
  ```
- `for` loops:
  ```bash
  for variable in list; do
    # commands
  done
  ```
- `while` loops:
  ```bash
  while [ condition ]; do
    # commands
  done
  ```
- `case` statements:
  ```bash
  case variable in
    pattern1)
      # commands
      ;;
    pattern2)
      # commands
      ;;
  esac
  ```

---

## Debugging Bash Scripts

- To debug a script, use:
  - `bash -
x <script_name.sh>` — Run the script in debug mode to see each command as it's executed.
  - `set -x` — Enable debugging output in the script.
  - `set +x` — Disable debugging output in the script.
- Check for syntax errors with:
  - `bash -n <script_name.sh>` — Check for syntax errors without executing the script.

---

## Other Utilities

### Commonly Used Commands

- **`alias`** — Create shortcuts for commands.
  - Example: `alias cls='clear'` — Create an alias to clear the terminal.
- **`unalias <name>`** — Remove an alias.
- **`echo`** — Print text to the terminal.
  - Example: `echo "Hello, World!"`

### File Management

- **`basename <path>`** — Strip the directory and suffix from filenames, leaving only the base name.
  - Example: `basename /path/to/file.txt` will output `file.txt`.
- **`dirname <path>`** — Strip the last component from the file name, returning the directory path.

  - Example: `dirname /path/to/file.txt` will output `/path/to`.

- **`date`** — Display or set the system date and time.

  - Example: `date +"%Y-%m-%d %H:%M:%S"` will output the current date and time in the specified format.

- **`df -h`** — Display disk space usage in a human-readable format.

- **`du -h <directory>`** — Show the disk usage of a directory in a human-readable format.

- **`ps aux`** — Display information about all running processes.

- **`kill <PID>`** — Terminate a process by its process ID (PID).

- **`top`** — Display a dynamic view of system processes.

- **`wget <URL>`** — Download files from the web.

  - Example: `wget http://example.com/file.txt` will download the specified file.

- **`curl <URL>`** — Transfer data from or to a server, using various protocols.
  - Example: `curl -O http://example.com/file.txt` will download the file.

---

## Environment Variables

### Setting and Accessing Variables

- **Setting Environment Variables**:
  - To set a temporary environment variable: `VAR_NAME=value command`
  - To export an environment variable: `export VAR_NAME=value`
- **Accessing Environment Variables**:
  - Use `$VAR_NAME` to access the value of an environment variable.

### Common Environment Variables

- `PATH` — A list of directories where the system looks for executables.
- `HOME` — The home directory of the current user.
- `USER` — The name of the current user.
