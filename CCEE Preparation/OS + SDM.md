# Operating System Basics

## What is an Operating System (OS)?

An **Operating System (OS)** is system software that acts as an intermediary between computer hardware and application software. It provides an environment in which application programs can run and facilitates user interaction with the hardware.

### Difference Between OS and Application Software:
| **Feature**           | **Operating System (OS)**                                   | **Application Software**                           |
|------------------------|------------------------------------------------------------|--------------------------------------------------|
| **Purpose**            | Manages hardware resources and provides a platform for application software. | Performs specific tasks for the user.            |
| **Dependency**         | Runs directly on hardware.                                 | Runs on top of the OS.                           |
| **Examples**           | Windows, Linux, macOS                                     | Microsoft Word, Google Chrome, Photoshop        |

### Why is OS Hardware-Dependent?
The OS interacts directly with the hardware via drivers and kernel-level instructions. Since hardware architectures (x86, ARM, etc.) and device capabilities vary, an OS must be designed to utilize the specific features and instruction sets of the target hardware.

---

## Components of an Operating System
1. **Kernel**: The core part of the OS that manages hardware, processes, and system resources.
   - Types: Monolithic Kernel, Microkernel, Hybrid Kernel.
   
2. **Process Management**: Handles the creation, scheduling, and termination of processes.
   
3. **Memory Management**: Manages RAM, virtual memory, and memory allocation.
   
4. **File System**: Manages file storage, retrieval, and metadata.
   
5. **Device Drivers**: Interfaces between hardware and the kernel.
   
6. **User Interface**:
   - **Command-Line Interface (CLI)**: Text-based interface (e.g., Bash, PowerShell).
   - **Graphical User Interface (GUI)**: Visual-based interface (e.g., Windows Explorer).
   
7. **Security & Access Control**: Ensures system protection and user authentication.

---

## Basic Computer Organization for an OS
An OS interacts with various hardware components in the system. Below is a diagram showing basic computer organization:

```
+--------------------+
|      User          |
+--------------------+
         ↓
+--------------------+
| Application Layer  |
+--------------------+
         ↓
+--------------------+
| Operating System   |
+--------------------+
         ↓
+--------------------+
|   Hardware Layer   |
+--------------------+
```

### Key Components:
1. **CPU (Central Processing Unit)**: Executes instructions and processes data.
2. **Memory (RAM)**: Temporarily stores data and instructions.
3. **Storage (HDD/SSD)**: Permanently stores data and programs.
4. **I/O Devices**: Communicates with peripherals like keyboards, monitors, etc.
5. **System Bus**: Transfers data between components.

---

## Examples of Operating Systems and Their Differences

| **Type**                  | **Examples**              | **Features and Purpose**                                                                                       |
|---------------------------|---------------------------|---------------------------------------------------------------------------------------------------------------|
| **Desktop OS**            | Windows, macOS, Linux     | Designed for personal computers with a focus on user-friendly GUIs.                                           |
| **Mobile OS**             | Android, iOS             | Optimized for touchscreens, battery efficiency, and mobile hardware.                                          |
| **Embedded System OS**    | FreeRTOS, VxWorks         | Lightweight OS for embedded systems like IoT devices, appliances, and vehicles.                               |
| **Server OS**             | Windows Server, Ubuntu Server | Designed for servers to handle multiple users, services, and scalability.                                     |
| **Real-Time OS (RTOS)**   | QNX, RTEMS               | Processes inputs within strict time constraints; used in robotics and control systems.                        |
| **Hybrid OS**             | Chrome OS                | Combines desktop and cloud capabilities.                                                                      |

---

## Functions of an OS
1. **Process Management**: Scheduling, multitasking, and handling process priorities.
2. **Memory Management**: Allocation and deallocation of memory spaces.
3. **File Management**: Organizing, storing, and retrieving files efficiently.
4. **Device Management**: Managing input/output devices through drivers.
5. **Security**: User authentication, data protection, and firewall management.
6. **Networking**: Enabling communication over networks.
7. **Error Handling**: Identifying and resolving hardware and software errors.
8. **System Performance Monitoring**: Tracking system performance and resource usage.

---

## User Space and Kernel Space; Modes, Interrupts, and System Calls

### User Space vs Kernel Space:
| **Aspect**        | **User Space**          | **Kernel Space**        |
|-------------------|-------------------------|-------------------------|
| **Access Level**  | Limited privileges      | Full privileges         |
| **Purpose**       | Runs applications       | Manages resources       |
| **Examples**      | Browsers, Text Editors  | Device drivers, Kernel  |

### Modes:
- **User Mode**: Restricted access, used for running applications.
- **Kernel Mode**: Full access to hardware, used for OS operations.

### Interrupts:
- Mechanisms by which hardware signals the CPU for immediate attention.
- Types:
  - **Hardware Interrupts**: Triggered by external devices (e.g., keyboard, mouse).
  - **Software Interrupts**: Triggered by programs via system calls.

### System Calls:
- Interface for applications to request services from the OS.
- Examples:
  - File operations: `open()`, `read()`, `write()`.
  - Process control: `fork()`, `exec()`.

```
```
# Linux Basics

## Introduction to Linux

Linux is a powerful open-source operating system that serves as the backbone for servers, desktops, and embedded systems. It provides a robust environment for managing hardware, running software, and performing tasks efficiently.

---

## Working Basics of the File System

The Linux file system is hierarchical, starting with the **root directory (`/`)**. All files and directories are organized under this root.

### Important Directories in Linux:
| **Directory** | **Purpose**                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `/`           | Root directory. Starting point of the file system hierarchy.               |
| `/home`       | Contains user directories. Example: `/home/user1` for user-specific data.  |
| `/etc`        | Configuration files for the system and software.                           |
| `/bin`        | Essential binaries (commands like `ls`, `cp`, `mv`).                       |
| `/var`        | Variable files like logs and caches.                                       |
| `/tmp`        | Temporary files created by processes.                                      |
| `/dev`        | Device files for accessing hardware (e.g., disks, USBs).                   |

---

## Commands Associated with Files/Directories & Other Basic Commands


| **Command**          | **Description**                                                                                       | **Example**                                         |
|-----------------------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| `ls`                 | Lists files and directories in the current directory.                                                | `ls -al`                                           |
| `pwd`                | Prints the current working directory.                                                                | `pwd`                                              |
| `cd`                 | Changes the current working directory.                                                               | `cd /home/user`                                    |
| `mkdir`              | Creates a new directory.                                                                             | `mkdir new_folder`                                 |
| `mv`                 | Moves or renames files or directories.                                                               | `mv file1 file2`                                   |
| `cp`                 | Copies files or directories.                                                                         | `cp file1 file2`                                   |
| `rm`                 | Removes files or directories.                                                                        | `rm -r folder_name`                                |
| `touch`              | Creates an empty file.                                                                               | `touch newfile.txt`                                |
| `ln`                 | Creates a symbolic or hard link to a file or directory.                                              | `ln -s source_file link_name`                      |
| `clear`              | Clears the terminal screen.                                                                          | `clear`                                            |
| `cat`                | Displays the content of a file.                                                                      | `cat file.txt`                                     |
| `echo`               | Prints text to the terminal or writes it to a file.                                                  | `echo "Hello" > file.txt`                          |
| `less`               | Views file content one screen at a time.                                                             | `less file.txt`                                    |
| `man`                | Displays the manual for a command.                                                                   | `man ls`                                           |
| `uname`              | Shows system information such as kernel name and version.                                            | `uname -a`                                         |
| `whoami`             | Displays the current logged-in user.                                                                 | `whoami`                                           |
| `tar`                | Archives files and directories into a single file.                                                   | `tar -cvf archive.tar folder/`                     |
| `grep`               | Searches for a pattern in a file.                                                                    | `grep "text" file.txt`                             |
| `head`               | Displays the first lines of a file.                                                                  | `head -n 10 file.txt`                              |
| `tail`               | Displays the last lines of a file.                                                                   | `tail -n 10 file.txt`                              |
| `diff`               | Compares two files line by line.                                                                     | `diff file1.txt file2.txt`                         |
| `cmp`                | Compares two files byte by byte.                                                                     | `cmp file1.txt file2.txt`                          |
| `comm`               | Compares two sorted files line by line.                                                              | `comm file1.txt file2.txt`                         |
| `sort`               | Sorts the contents of a file.                                                                        | `sort file.txt`                                    |
| `export`             | Sets environment variables.                                                                          | `export PATH=$PATH:/new/path`                      |
| `zip`                | Compresses files into a `.zip` archive.                                                              | `zip archive.zip file1 file2`                      |
| `unzip`              | Extracts files from a `.zip` archive.                                                                | `unzip archive.zip`                                |
| `ssh`                | Connects to a remote system securely via SSH.                                                        | `ssh user@host`                                    |
| `service`            | Manages services on the system (start, stop, restart).                                               | `service apache2 start`                            |
| `ps`                 | Displays currently running processes.                                                                | `ps aux`                                           |
| `kill` and `killall` | Terminates processes using their PID or name.                                                        | `kill 1234` / `killall process_name`               |
| `df`                 | Displays disk usage of file systems.                                                                 | `df -h`                                            |
| `mount`              | Mounts a filesystem to a directory.                                                                  | `mount /dev/sdb1 /mnt`                             |
| `chmod`              | Changes file or directory permissions.                                                               | `chmod 755 file.txt`                               |
| `chown`              | Changes the ownership of a file or directory.                                                        | `chown user:group file.txt`                        |
| `ifconfig`           | Displays or configures network interfaces.                                                           | `ifconfig eth0`                                    |
| `traceroute`         | Displays the route packets take to a network destination.                                            | `traceroute google.com`                            |
| `wget`               | Downloads files from the internet.                                                                   | `wget http://example.com/file.zip`                 |
| `ufw`                | Manages the firewall (Uncomplicated Firewall).                                                       | `ufw allow 22`                                     |
| `iptables`           | Configures network packet filtering rules.                                                           | `iptables -L`                                      |
| `apt`, `pacman`, `yum`, `rpm` | Package managers for installing and managing software on different distributions.           | `apt install package` / `yum update`              |
| `sudo`               | Executes a command as a superuser.                                                                   | `sudo apt update`                                  |
| `cal`                | Displays a calendar in the terminal.                                                                 | `cal`                                              |
| `alias`              | Creates shortcuts for commands.                                                                      | `alias ll='ls -al'`                                |
| `dd`                 | Copies and converts data at the byte level.                                                          | `dd if=/dev/sda of=backup.img bs=4M`               |
| `whereis`            | Locates binaries, sources, and manuals for a command.                                                | `whereis ls`                                       |
| `whatis`             | Displays a short description of a command.                                                           | `whatis ls`                                        |
| `top`                | Displays real-time system resource usage.                                                            | `top`                                              |
| `useradd`            | Adds a new user to the system.                                                                       | `sudo useradd newuser`                             |
| `passwd`             | Changes the password for a user.                                                                     | `passwd`                                           |



---

### Redirection and Pipes

#### Redirection Operators:
| **Operator** | **Description**                          | **Example**                      |
|--------------|------------------------------------------|----------------------------------|
| `>`          | Redirects output to a file (overwrites). | `echo "Hello" > file.txt`        |
| `>>`         | Appends output to a file.                | `echo "World" >> file.txt`       |
| `<`          | Takes input from a file.                | `cat < file.txt`                 |

#### Pipes (`|`):
- Used to pass the output of one command as input to another.
- **Example**: `cat file.txt | grep "search_term"`

---

## File Permissions and How to Set Them

Linux uses a permission model to manage access to files and directories. Permissions are represented as **rwx** (read, write, execute) for the owner, group, and others.

### Permission Format:
```
-rwxr-xr--  1 user group 1234 Jan 14 10:30 file.txt
```
| **Field**    | **Meaning**                  |
|--------------|------------------------------|
| `-`          | File type (`-` for file, `d` for directory). |
| `rwxr-xr--`  | Permissions (owner, group, others).          |
| `user`       | File owner.                                  |
| `group`      | File group.                                  |

### Setting Permissions with `chmod`:
- **Symbolic Method**: `chmod u+x file.txt` (adds execute permission for the owner).
- **Octal Method**: `chmod 754 file.txt`
  - `7`: Full (rwx).
  - `5`: Read and execute (r-x).
  - `4`: Read-only (r--).

### Changing Ownership with `chown`:
- Syntax: `chown user:group file.txt`

---

## Access Control List (ACL)
ACL provides fine-grained permissions beyond the traditional model.
- **Set ACL**: `setfacl -m u:user1:rw file.txt`
- **View ACL**: `getfacl file.txt`

---

## Network Commands

| **Command**  | **Description**                                  | **Example**                  |
|--------------|--------------------------------------------------|------------------------------|
| `telnet`     | Connects to a remote host using Telnet protocol. | `telnet 192.168.1.1`         |
| `ftp`        | Transfers files using FTP protocol.              | `ftp ftp.example.com`        |
| `ssh`        | Secure shell login to a remote machine.          | `ssh user@hostname`          |
| `sftp`       | Secure file transfer using SSH.                  | `sftp user@hostname`         |
| `finger`     | Displays user information.                       | `finger username`            |

---

## System Variables (e.g., PS1, PS2)

### Common System Variables:
| **Variable** | **Description**                                  |
|--------------|--------------------------------------------------|
| `PS1`        | Primary prompt string. Customizes the shell prompt. |
| `PS2`        | Secondary prompt string (used for multi-line commands). |

### Setting System Variables:
- Temporarily: `export PS1="\u:\w\$ "` (Custom prompt).
- Permanently: Add to `.bashrc` or `.zshrc`.

---

## Flowchart: File System Permission Workflow
```plaintext
          +-----------------------+
          | Check Current Owner   |
          +-----------------------+
                      |
                      v
      +-----------------------------+
      | Change Owner (`chown`)      |
      +-----------------------------+
                      |
                      v
      +------------------------------------+
      | Modify Permissions (`chmod`)      |
      +------------------------------------+
                      |
                      v
       +---------------------------------+
       | Validate Changes (`ls -l`)     |
       +---------------------------------+
```

---

## Code Snippet: Automating Permission Setup
```bash
#!/bin/bash
# Script to set permissions for a directory

DIR_PATH=$1
if [ -d "$DIR_PATH" ]; then
    chmod -R 755 "$DIR_PATH"
    echo "Permissions set to 755 for $DIR_PATH"
else
    echo "Directory does not exist!"
fi
```

# Shell Programming in Linux

## What is a Shell?

A **shell** is a command-line interpreter that provides a user interface for accessing the services of the operating system. It processes commands entered by the user and executes them, either directly or by passing them to the appropriate program.

### Types of Shells in Linux
| **Shell**      | **Description**                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------|
| **Bash**        | Bourne Again Shell, the most widely used shell. Supports scripting and advanced features.       |
| **Zsh**         | Z Shell, similar to Bash but with additional features like themes and plugins.                  |
| **Ksh**         | Korn Shell, combines features of the C Shell and Bourne Shell.                                  |
| **Tcsh**        | T C Shell, an enhanced version of the C Shell with scripting improvements.                      |
| **Fish**        | Friendly Interactive Shell, designed for user-friendliness and simplicity.                      |

---

## Shell Variables

Shell variables are placeholders that store data used by shell scripts and commands.

### Types of Variables
1. **System Variables**: Predefined variables maintained by the shell.
   - Examples: `$HOME`, `$PATH`, `$USER`
2. **User-Defined Variables**: Custom variables created by the user.
   - Example:
     ```bash
     MY_VAR="Hello"
     echo $MY_VAR
     ```

### Scope of Variables
- **Local Variables**: Available within the current shell or script.
- **Environment Variables**: Available to all processes started from the shell.

---

## Wildcard Symbols

Wildcards are symbols used to represent patterns in filenames or strings.

| **Symbol** | **Description**                           | **Example**                |
|------------|-------------------------------------------|----------------------------|
| `*`        | Matches zero or more characters.          | `ls *.txt` (all `.txt` files) |
| `?`        | Matches exactly one character.            | `ls file?.txt`            |
| `[ ]`      | Matches any one character within brackets.| `ls file[1-3].txt`        |

---

## Shell Meta Characters

Meta characters have special meanings in the shell and are used for various operations.

| **Character** | **Description**                                   | **Example**                |
|---------------|---------------------------------------------------|----------------------------|
| `;`           | Separates multiple commands in a single line.    | `ls; pwd`                 |
| `&`           | Executes a command in the background.            | `sleep 10 &`              |
| `|`           | Pipes output of one command to another.          | `ls | grep file`          |
| `>`           | Redirects output to a file (overwrites).         | `echo "data" > file.txt`  |
| `>>`          | Redirects output to a file (appends).            | `echo "more data" >> file.txt` |
| `<`           | Redirects input from a file.                     | `wc < file.txt`           |
| `\`           | Escapes special characters.                      | `echo \$HOME`             |

---

## Command Line Arguments

Command-line arguments allow users to pass inputs to scripts when executing them.

### Example Script
```bash
#!/bin/bash
echo "Script Name: $0"
echo "First Argument: $1"
echo "Second Argument: $2"
echo "All Arguments: $*"
echo "Number of Arguments: $#"
```

### Run the Script
```bash
./script.sh arg1 arg2
```

**Output**:
```
Script Name: ./script.sh
First Argument: arg1
Second Argument: arg2
All Arguments: arg1 arg2
Number of Arguments: 2
```

---

## `read` and `echo` Commands

### `read` Command
Used to take input from the user during script execution.
```bash
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello, $name!"
```

**Run**:
```
$ ./script.sh
Enter your name:
John
Hello, John!
```

### `echo` Command
Used to display messages or output values of variables.
```bash
#!/bin/bash
echo "This is a shell script!"
VAR="Linux"
echo "Welcome to $VAR"
```

**Output**:
```
This is a shell script!
Welcome to Linux
```

---

### Flowchart: Command Execution in Shell

```plaintext
+---------------------+
|  User Enters Command|
+---------------------+
           |
           v
+---------------------+
| Shell Interprets    |
+---------------------+
           |
           v
+-----------------------------+
| Shell Locates Command/Binary|
+-----------------------------+
           |
           v
+---------------------------+
| Execute Command and Output|
+---------------------------+
```

---

### Code Snippet: Using Wildcards and Arguments
```bash
#!/bin/bash
# Script to count .txt files in a directory

read -p "Enter directory path: " DIR
if [ -d "$DIR" ]; then
    COUNT=$(ls $DIR/*.txt 2>/dev/null | wc -l)
    echo "Number of .txt files in $DIR: $COUNT"
else
    echo "Invalid directory!"
fi
```
# Advanced Shell Programming in Linux

## Decision Loops in Shell Programming

### 1. `if-else` Statement
The `if-else` statement is used to execute a block of code based on a condition.

#### Syntax:
```bash
if [ condition ]; then
    # Code to execute if condition is true
else
    # Code to execute if condition is false
fi
```

#### Example:
```bash
#!/bin/bash
read -p "Enter a number: " num
if [ $num -gt 0 ]; then
    echo "Positive number"
else
    echo "Non-positive number"
fi
```

---

### 2. `test` Command
The `test` command is used to evaluate expressions.

#### Example:
```bash
#!/bin/bash
if test $1 -gt 0; then
    echo "$1 is greater than zero"
else
    echo "$1 is less than or equal to zero"
fi
```

---

### 3. Nested `if-else`
Nested `if-else` allows multiple conditions to be checked.

#### Example:
```bash
#!/bin/bash
read -p "Enter your age: " age
if [ $age -lt 18 ]; then
    echo "You are a minor."
elif [ $age -lt 65 ]; then
    echo "You are an adult."
else
    echo "You are a senior citizen."
fi
```

---

### 4. `case` Statement
The `case` statement is used for multiple conditional checks.

#### Syntax:
```bash
case expression in
    pattern1)
        # Code for pattern1
        ;;
    pattern2)
        # Code for pattern2
        ;;
    *)
        # Default case
        ;;
esac
```

#### Example:
```bash
#!/bin/bash
read -p "Enter a day of the week: " day
case $day in
    "Monday")
        echo "Start of the work week!"
        ;;
    "Friday")
        echo "Almost weekend!"
        ;;
    *)
        echo "Have a great day!"
        ;;
esac
```

---

### 5. `while` Loop
The `while` loop runs as long as the condition is true.

#### Syntax:
```bash
while [ condition ]; do
    # Commands
done
```

#### Example:
```bash
#!/bin/bash
count=1
while [ $count -le 5 ]; do
    echo "Count: $count"
    count=$((count + 1))
done
```

---

### 6. `until` Loop
The `until` loop runs as long as the condition is false.

#### Syntax:
```bash
until [ condition ]; do
    # Commands
done
```

#### Example:
```bash
#!/bin/bash
count=1
until [ $count -gt 5 ]; do
    echo "Count: $count"
    count=$((count + 1))
done
```

---

### 7. `for` Loop
The `for` loop iterates over a list of items.

#### Syntax:
```bash
for var in list; do
    # Commands
done
```

#### Example:
```bash
#!/bin/bash
for name in Alice Bob Charlie; do
    echo "Hello, $name!"
done
```

---

## Regular Expressions in Shell

Regular expressions (regex) are patterns used to match text. In shell scripting, regex is often used with tools like `grep`, `sed`, or `awk`.

#### Example: Regex with `grep`
```bash
#!/bin/bash
echo "Enter a string:"
read string
if [[ $string =~ ^[A-Z][a-z]+$ ]]; then
    echo "The string starts with an uppercase letter."
else
    echo "The string does not match the pattern."
fi
```

#### Common Regex Symbols:
| **Symbol**  | **Description**                  | **Example**                     |
|-------------|----------------------------------|----------------------------------|
| `.`         | Matches any single character.   | `a.c` matches `abc`, `aXc`.     |
| `^`         | Matches the start of a line.    | `^abc` matches `abc` at start.  |
| `$`         | Matches the end of a line.      | `xyz$` matches `xyz` at end.    |
| `*`         | Matches zero or more occurrences.| `ab*` matches `a`, `ab`, `abb`. |
| `[ ]`       | Matches any character in brackets.| `[a-c]` matches `a`, `b`, `c`.  |

---

## Arithmetic Expressions

Shell scripting supports arithmetic operations using the `(( ))` syntax or the `expr` command.

#### Example: Using `(( ))`
```bash
#!/bin/bash
a=10
b=5
sum=$((a + b))
echo "Sum: $sum"
```

#### Example: Using `expr`
```bash
#!/bin/bash
a=10
b=5
sum=$(expr $a + $b)
echo "Sum: $sum"
```

---

## More Examples in Shell Programming

### 1. Script to Check Even or Odd
```bash
#!/bin/bash
read -p "Enter a number: " num
if [ $((num % 2)) -eq 0 ]; then
    echo "$num is even."
else
    echo "$num is odd."
fi
```

---

### 2. Script to Find Factorial
```bash
#!/bin/bash
read -p "Enter a number: " num
factorial=1
for ((i = 1; i <= num; i++)); do
    factorial=$((factorial * i))
done
echo "Factorial of $num is $factorial."
```

---

### 3. Script to Display Prime Numbers
```bash
#!/bin/bash
read -p "Enter a number: " num
for ((i = 2; i <= num; i++)); do
    is_prime=1
    for ((j = 2; j < i; j++)); do
        if [ $((i % j)) -eq 0 ]; then
            is_prime=0
            break
        fi
    done
    if [ $is_prime -eq 1 ]; then
        echo "$i is a prime number."
    fi
done
```

---

### 4. Script for File Existence Check
```bash
#!/bin/bash
read -p "Enter the filename: " filename
if [ -e "$filename" ]; then
    echo "File $filename exists."
else
    echo "File $filename does not exist."
fi
```

---

### 5. Script to Monitor Disk Usage
```bash
#!/bin/bash
while true; do
    df -h
    sleep 5
done
```



