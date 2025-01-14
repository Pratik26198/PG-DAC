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

### File and Directory Commands
| **Command**    | **Description**                                  | **Example**                      |
|----------------|--------------------------------------------------|----------------------------------|
| `ls`           | Lists files and directories.                    | `ls -al`                        |
| `cd`           | Changes directory.                              | `cd /home/user`                 |
| `pwd`          | Prints the current directory.                   | `pwd`                           |
| `mkdir`        | Creates a directory.                            | `mkdir new_folder`              |
| `rmdir`        | Removes an empty directory.                     | `rmdir old_folder`              |
| `cp`           | Copies files or directories.                    | `cp file1 file2`                |
| `mv`           | Moves or renames files.                         | `mv old_name new_name`          |
| `rm`           | Removes files or directories.                   | `rm file` / `rm -r directory`   |
| `find`         | Searches files and directories.                 | `find /home -name "*.txt"`      |
| `touch`        | Creates an empty file.                          | `touch newfile.txt`             |

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


