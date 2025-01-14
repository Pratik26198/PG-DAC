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


