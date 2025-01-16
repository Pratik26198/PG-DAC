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
# .NET Framework, .NET Core, Mono, Xamarin Differences

## Key Differences

| Feature                | .NET Framework                       | .NET Core                           | Mono                               | Xamarin                            |
|------------------------|--------------------------------------|-------------------------------------|------------------------------------|------------------------------------|
| **Purpose**            | Windows-based applications           | Cross-platform, modern applications | Cross-platform, lightweight CLR   | Mobile app development (iOS, Android) |
| **Platform Support**   | Windows                              | Windows, macOS, Linux               | Cross-platform                     | Mobile devices                     |
| **Performance**        | Moderate                             | High                                | Moderate                          | Optimized for mobile              |
| **Open Source**        | No                                   | Yes                                 | Yes                               | Yes                                |
| **Deployment Model**   | System-wide installation             | Side-by-side deployment             | Embedded in apps                  | Embedded in apps                  |

## Architecture Diagram

```
.NET Ecosystem:
+-------------------------+
|   Applications          |
|   - Desktop             |
|   - Mobile              |
|   - Cloud               |
|   - IoT                 |
+-------------------------+
|  .NET Framework | .NET Core | Xamarin | Mono |
+-------------------------+
|        CLR and BCL       |
+-------------------------+
|   Platform-Specific APIs |
+-------------------------+
```

---

# Versions of .NET Framework

## Milestones in .NET Framework Versions

| **Version** | **Release Year** | **Key Features**                                         |
|-------------|------------------|---------------------------------------------------------|
| 1.0         | 2002             | Initial release, CLR, ASP.NET, ADO.NET                  |
| 2.0         | 2005             | Generics, Nullable types                                |
| 3.0         | 2006             | WPF, WCF, WWF, CardSpace                                |
| 3.5         | 2007             | LINQ, Lambda Expressions                               |
| 4.0         | 2010             | Dynamic Language Runtime, PLINQ                        |
| 4.5         | 2012             | Async Programming, .NET for Windows Store apps         |
| 4.7         | 2017             | .NET Standard support, Performance improvements        |
| 4.8         | 2019             | Last full version of the Framework                     |

---

# Managed and Unmanaged Code

### Managed Code
- Code executed under the control of the CLR.
- Benefits:
  - Garbage collection.
  - Type safety.
  - Exception handling.

**Example:**
```csharp
class Program
{
    static void Main()
    {
        Console.WriteLine("Hello, Managed Code!");
    }
}
```

### Unmanaged Code
- Code executed outside the CLR environment.
- Typically written in languages like C or C++.
- Requires explicit memory management.

**Example:**
```c
#include <stdio.h>
int main()
{
    printf("Hello, Unmanaged Code!");
    return 0;
}
```

| **Feature**       | **Managed Code**                        | **Unmanaged Code**                    |
|-------------------|-----------------------------------------|---------------------------------------|
| **Memory**        | Managed by CLR (Garbage Collection)     | Explicitly managed by the programmer  |
| **Platform**      | Cross-platform (via CLR)                | Platform-dependent                   |
| **Development**   | Simplified with .NET features           | Requires low-level programming        |

---

# Introduction to Visual Studio

### What is Visual Studio?
Visual Studio is an Integrated Development Environment (IDE) by Microsoft, providing tools for developing, debugging, and deploying .NET applications.

## Features
1. **Code Editor**: Supports IntelliSense and code navigation.
2. **Debugger**: Built-in debugging tools for breakpoints and watch variables.
3. **Designer**: GUI design tools for Windows and web apps.
4. **Integrated Testing**: Unit testing and test-driven development support.
5. **Extensions**: Integration with Git, NuGet, and more.

### Common Workflows
1. Create a new project.
2. Write and edit code.
3. Debug and test the application.
4. Build and deploy the project.

---

# Using ILDASM

### What is ILDASM?
The **Intermediate Language Disassembler (ILDASM)** is a tool provided by the .NET SDK for viewing the contents of .NET assemblies.

### Features
- View the **manifest**, **metadata**, and **IL code**.
- Analyze **type definitions** and **resources**.

### Steps to Use ILDASM
1. Open **Developer Command Prompt**.
2. Run `ILDASM` command.
3. Load the `.exe` or `.dll` file into the tool.

### Example: Viewing IL Code
1. Compile the following C# code:
    ```csharp
    public class Program
    {
        public static void Main()
        {
            System.Console.WriteLine("Hello, ILDASM!");
        }
    }
    ```
2. Use `ILDASM` to inspect the generated assembly:
   ```plaintext
   .method public hidebysig static void Main() cil managed
   {
       .entrypoint
       ldstr "Hello, ILDASM!"
       call void [mscorlib]System.Console::WriteLine(string)
       ret
   }
   ```

---

