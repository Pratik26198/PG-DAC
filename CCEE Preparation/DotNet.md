# Introduction to .NET Framework

The .NET Framework is a software development platform for building and running applications on Windows. It simplifies the development process by providing a common runtime environment and a rich class library.

## Architecture Diagram

```
+----------------------------------------+
|          User Applications             |
+----------------------------------------+
|      Framework Class Library (FCL)     |
+----------------------------------------+
|    Common Language Runtime (CLR)       |
| - Garbage Collection                   |
| - JIT Compilation                      |
| - Exception Handling                   |
+----------------------------------------+
|        Operating System (Windows)      |
+----------------------------------------+
```

## Features of .NET Framework

| **Feature**           | **Description**                                                                 |
|------------------------|---------------------------------------------------------------------------------|
| Common Language Runtime (CLR) | Executes managed code and provides services like garbage collection and JIT.   |
| Base Class Library (BCL)      | Provides core functionalities like file I/O, collections, and data types.     |
| Multi-Language Support        | Supports multiple languages like C#, VB.NET, F#, etc.                        |
| Portability                   | Applications can run on any Windows system with the .NET Framework installed. |

---

# Intermediate Language (IL)

Intermediate Language (IL) is the CPU-independent code generated after compiling .NET source code. IL is stored in assemblies and is converted to native machine code by the **Just-In-Time (JIT) Compiler** at runtime.

## Flowchart of IL Execution

```
Source Code (C#/VB.NET/F#)
        |
        v
   Compiler
        |
        v
Intermediate Language (IL)
        |
        v
      CLR
        |
        v
Native Machine Code (Executed)
```

## Example: IL Code

C# Method:

```csharp
public int Add(int a, int b)
{
    return a + b;
}
```

Generated IL:

```plaintext
.method public hidebysig instance int32 Add(int32 a, int32 b) cil managed
{
    .maxstack 2
    ldarg.1
    ldarg.2
    add
    ret
}
```

---

# Assemblies and Their Structure

An **assembly** is a compiled code library in the .NET Framework, containing Intermediate Language (IL) code, metadata, and resources.

## Assembly Structure Diagram

```
+-----------------------------+
|      Assembly Manifest      | -> Metadata about the assembly (name, version, culture)
+-----------------------------+
|        Metadata             | -> Describes types and members in the assembly
+-----------------------------+
|        IL Code              | -> CPU-independent intermediate language code
+-----------------------------+
|     Embedded Resources      | -> Images, strings, and other resources
+-----------------------------+
```

## Types of Assemblies

| **Type**         | **Description**                                                                |
|-------------------|--------------------------------------------------------------------------------|
| **Executable (EXE)** | Contains the entry point of an application; used for standalone programs.     |
| **Dynamic Link Library (DLL)** | Used for shared components; cannot be executed directly.                     |

---

# Common Language Runtime (CLR)

The **CLR** provides a managed environment for executing .NET applications.

## CLR Components and Functions

| **Component**         | **Description**                                                                 |
|------------------------|---------------------------------------------------------------------------------|
| Just-In-Time Compiler  | Converts IL to native code for execution.                                      |
| Garbage Collector      | Automatically manages memory by cleaning up unused objects.                   |
| Thread Management      | Manages multithreading and task scheduling.                                   |
| Exception Handling     | Provides a structured way to handle runtime errors.                           |

---

# Just-In-Time (JIT) Compilation

The JIT Compiler translates IL into machine code **just before execution**.

## Types of JIT

| **Type**     | **Description**                                                                           |
|--------------|-------------------------------------------------------------------------------------------|
| Pre-JIT      | Compiles the entire IL code into machine code at the application’s startup.               |
| Econo-JIT    | Compiles only necessary code and deallocates it after execution to save memory.           |
| Normal JIT   | Compiles code as it is required, keeping it in memory for subsequent calls.               |

## Diagram: JIT Compilation Process

```
+-------------+         +---------+        +------------+
| IL (from EXE| ---->   |   JIT   | ---->  | Machine Code|
| or DLL)     |         | Compiler|        |            |
+-------------+         +---------+        +------------+
```

---

# Memory Management

Memory in .NET applications is managed by the CLR, which includes:
1. **Heap Allocation**: Allocates memory for reference types.
2. **Garbage Collection**: Frees unused memory.

## Heap Memory Layout

```
+-----------------------+
| Generation 0 (Short)  |
+-----------------------+
| Generation 1 (Medium) |
+-----------------------+
| Generation 2 (Long)   |
+-----------------------+
```

---

# Garbage Collection (GC)

The garbage collector (GC) in .NET reclaims memory that is no longer in use.

## Phases of GC

| **Phase**   | **Description**                                       |
|-------------|-------------------------------------------------------|
| **Mark**    | Identifies objects still in use.                     |
| **Sweep**   | Cleans up memory occupied by unreferenced objects.   |
| **Compact** | Rearranges memory to eliminate fragmentation.        |

## Code Example

```csharp
class Program
{
    static void Main()
    {
        // Allocating memory
        string data = new string('A', 1000);
        
        // Releasing memory
        data = null;
        GC.Collect(); // Forcing garbage collection
    }
}
```

---

# AppDomain Management

An **AppDomain** is an isolated environment where .NET applications run. It provides:
1. **Isolation**: Applications in separate AppDomains cannot interfere with each other.
2. **Security**: Ensures secure execution.
3. **Stability**: Crashes in one AppDomain don’t affect others.

---

# CLS and CTS

| **Term**                  | **Description**                                                                 |
|---------------------------|---------------------------------------------------------------------------------|
| **Common Language Specification (CLS)** | A set of rules for ensuring language interoperability.                  |
| **Common Type System (CTS)**           | Defines a standard set of data types and programming constructs.         |

## Example: CLS Compliance

C# Code:

```csharp
// CLS-Compliant
public class Example
{
    public int Add(int a, int b) => a + b;
}
```

---

# Security in .NET

.NET Framework offers robust security models, including:
1. **Code Access Security (CAS)**: Restricts code based on permissions.
2. **Role-Based Security**: Authorizes users based on roles.
3. **Cryptography**: Provides encryption for sensitive data.

## Example: Role-Based Security

```csharp
[Authorize(Roles = "Admin")]
public IActionResult AdminPage()
{
    return View();
}
```

---

