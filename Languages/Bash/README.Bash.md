Here's the updated README file with your provided information incorporated, including a functional table of contents:

---

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
8. [Mathematical and Logical Expressions](#mathematical-and-logical-expressions)
9. [Variables in Bash](#variables-in-bash)
10. [Bash Control Flow](#bash-control-flow)
11. [Debugging Bash Scripts](#debugging-bash-scripts)
12. [Other Utilities](#other-utilities)

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

---

## File and Directory Operations

- `mkdir <directory>` — Create a directory.
  - `mkdir -p <parent/child>` — Create a directory along with its parent directories.
- `cp <file> <destination>` — Copy a file to a destination.
- `cat <filename>` — Display the content of a file.
- `head <filename>` — Display the first part of a file.
- `tail <filename>` — Display the last part of a file.
- `find -name '*.php' | wc -l` — Count the number of `.php` files in a directory.

---

## User and Permission Management

- `whoami` — Display the current user.
- `chown <user>:<group> <file/directory>` — Change file or directory ownership.
- `chgrp <group_name> <file/directory>` — Change the group ownership.
- `chmod` — Change file permissions.
  - Example: `chmod 755 <filename>` — Full permissions for the owner (rwx), read-execute for group and others.
  - Example: `chmod 155 <filename>` — Execute-only for the owner, read-execute for group and others.

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

---

## Text Manipulation

- `grep "word" <filename>` — Search for a word in a file.
- `cut -d"delimiter" -f<field number> <filename>` — Extract sections from each line of a file.
- `tr "char1" "char2"` — Translate or replace characters in a file.
- `column -t <filename>` — Format the output into tabular form.
- `awk '{print $2, $3, $NF}' <filename>` — Print specific fields from each line.
- `sed 's/pattern/replacement/g' <filename>` — Search and replace text globally in a file.

---

## Bash Operators

- `&&` — Logical AND (combines multiple commands).
- `||` — Logical OR.
- `>` — Greater than.
- `<` — Less than.
- `=`, `!=` — String comparison.
- `-a` — Logical AND for test expressions.
- `-o` — Logical OR for test expressions.

---

## Mathematical and Logical Expressions

- Arithmetic operations:
  - `expr` — Example: `z=$(expr 1 + 2)`
  - `let` — Example: `let z=1+2`
  - `$((expression))` — Example: `z=$((1 + 2))`
  - Increment and decrement: `((z++))` or `((x+=2)).`
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
  - `bash -x script.sh` — Prints each command before executing it.
  - `set -x` — Enables debugging within the script.
  - `set +x` — Disables debugging within the script.

---

## Other Utilities

- `man <command>` — Access the manual for a command.
- `whatis <command>` — Display a one-line description of a command.
- `apropos <keyword>` — Search the manual page descriptions for a keyword.
- `history` — Display the command history.
- `alias <name>=<command>` — Create an alias for a command.
- `unalias <name>` — Remove an alias.
