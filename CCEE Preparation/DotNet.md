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
# Console Applications and Class Libraries in .NET Core

## **Console Applications**

### What are Console Applications?
Console applications are command-line programs that run in a console window (Command Prompt, PowerShell, or Terminal). These applications interact with users through text input and output.

### Features of Console Applications:
1. Lightweight and straightforward.
2. Typically used for utility programs or testing purposes.
3. No graphical user interface (GUI).

### Code Example:
```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Welcome to Console Application!");
        Console.Write("Enter your name: ");
        string name = Console.ReadLine();
        Console.WriteLine($"Hello, {name}!");
    }
}
```

### How to Create a Console Application in .NET Core:
1. Open a terminal.
2. Run the following commands:
   ```bash
   dotnet new console -n MyConsoleApp
   cd MyConsoleApp
   dotnet run
   ```

---

## **Class Libraries**

### What are Class Libraries?
Class libraries are reusable sets of code (usually in the form of `.dll` files) that can be referenced by multiple projects.

### Features of Class Libraries:
1. Promotes code reuse.
2. Provides encapsulation and modular design.
3. Does not have an entry point (`Main` method).

### Code Example:
```csharp
namespace MyLibrary
{
    public class Greeting
    {
        public string SayHello(string name)
        {
            return $"Hello, {name}!";
        }
    }
}
```

### How to Create a Class Library in .NET Core:
1. Open a terminal.
2. Run the following commands:
   ```bash
   dotnet new classlib -n MyClassLibrary
   ```
3. Reference the library in another project using:
   ```bash
   dotnet add reference ../MyClassLibrary/MyClassLibrary.csproj
   ```

---

# C# Basics

### Key Elements of C#:
1. **Case-Sensitive**: C# distinguishes between uppercase and lowercase.
2. **Object-Oriented**: Supports principles like encapsulation, inheritance, and polymorphism.
3. **Type-Safe**: Prevents operations on incompatible data types.

### Basic Structure of a C# Program:
```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```

---

# Project References and Using

### What is a Project Reference?
A project reference links one project to another, allowing the referencing project to use the classes, methods, and other components of the referenced project.

### Adding a Reference:
```bash
dotnet add reference ../MyClassLibrary/MyClassLibrary.csproj
```

### Using Directive:
The `using` directive imports namespaces into your program, allowing you to access their classes and methods.

Example:
```csharp
using MyLibrary;

class Program
{
    static void Main()
    {
        var greeting = new Greeting();
        Console.WriteLine(greeting.SayHello("Alice"));
    }
}
```

---

# Classes in C#

### Definition:
A class is a blueprint for creating objects. It encapsulates data and behavior.

### Example:
```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public void Introduce()
    {
        Console.WriteLine($"Hi, I am {Name} and I am {Age} years old.");
    }
}
```

---

# Data Types in .NET and CTS Equivalents

| **C# Type**      | **CTS Equivalent**       | **Description**                     |
|------------------|--------------------------|-------------------------------------|
| `int`            | `System.Int32`           | 32-bit signed integer               |
| `string`         | `System.String`          | Sequence of Unicode characters      |
| `bool`           | `System.Boolean`         | Represents true or false            |
| `double`         | `System.Double`          | 64-bit floating-point number        |
| `object`         | `System.Object`          | Base type for all objects           |

---

# Methods in C#

### **Method Overloading**
Method overloading allows multiple methods with the same name but different parameters.

Example:
```csharp
public class Calculator
{
    public int Add(int a, int b) => a + b;
    public double Add(double a, double b) => a + b;
}
```

### **Optional Parameters**
Allows parameters to have default values if not provided by the caller.

Example:
```csharp
public void PrintMessage(string message = "Default Message")
{
    Console.WriteLine(message);
}
```

### **Named Parameters and Positional Parameters**
Named parameters allow specifying arguments by name.

Example:
```csharp
PrintMessage(message: "Hello!");
```

### **Using `params`**
Allows passing a variable number of arguments to a method.

Example:
```csharp
public void PrintNumbers(params int[] numbers)
{
    foreach (var number in numbers)
    {
        Console.WriteLine(number);
    }
}
```

### **Local Functions**
A method defined inside another method. Useful for helper logic.

Example:
```csharp
public void ProcessData()
{
    void Log(string message)
    {
        Console.WriteLine(message);
    }

    Log("Processing started...");
    // Processing logic
    Log("Processing completed.");
}
```

---

# Properties in C#

### **Get and Set Accessors**
Properties in C# are used to encapsulate fields and provide controlled access to them through `get` and `set` accessors.

Example:
```csharp
public class Person
{
    private string name;

    public string Name
    {
        get { return name; }
        set { name = value; }
    }
}

class Program
{
    static void Main()
    {
        Person person = new Person();
        person.Name = "Alice";
        Console.WriteLine(person.Name);
    }
}
```

### **Readonly Properties**
Readonly properties allow data to be read but not modified.

Example:
```csharp
public class Circle
{
    public double Radius { get; }

    public Circle(double radius)
    {
        Radius = radius;
    }
}

class Program
{
    static void Main()
    {
        Circle circle = new Circle(10);
        Console.WriteLine(circle.Radius);
    }
}
```

### **Using Property Accessors to Create Readonly Properties**
You can use a `get` accessor without a `set` to make a property readonly.

Example:
```csharp
public class Square
{
    public double Side { get; }
    public double Area => Side * Side; // Read-only property using expression body

    public Square(double side)
    {
        Side = side;
    }
}
```

---

# Constructors

### **What are Constructors?**
Constructors are special methods used to initialize objects. They are called automatically when an object is created.

### **Features of Constructors:**
- Have the same name as the class.
- Do not have a return type.

Example:
```csharp
public class Car
{
    public string Model { get; }

    public Car(string model)
    {
        Model = model;
    }
}

class Program
{
    static void Main()
    {
        Car car = new Car("Tesla");
        Console.WriteLine(car.Model);
    }
}
```

---

# Object Initializer

Object initializers allow you to set property values when creating an object without using a constructor explicitly.

Example:
```csharp
public class Book
{
    public string Title { get; set; }
    public string Author { get; set; }
}

class Program
{
    static void Main()
    {
        Book book = new Book
        {
            Title = "1984",
            Author = "George Orwell"
        };
        Console.WriteLine($"{book.Title} by {book.Author}");
    }
}
```

---

# Destructors

### **What is a Destructor?**
Destructors are methods used to clean up resources before an object is garbage collected. They have the same name as the class but are prefixed with a `~` symbol.

### **Key Points:**
- Called automatically when the object is no longer accessible.
- Cannot have parameters or be called explicitly.

Example:
```csharp
public class Resource
{
    ~Resource()
    {
        Console.WriteLine("Destructor called to release resources.");
    }
}

class Program
{
    static void Main()
    {
        Resource resource = new Resource();
    }
}
```

---

# Discussion on IDisposable

### **What is IDisposable?**
The `IDisposable` interface provides a mechanism for releasing unmanaged resources manually. It is commonly used with the `using` statement to ensure proper cleanup.

### **Implementing IDisposable**
To implement `IDisposable`, you need to define the `Dispose` method.

Example:
```csharp
public class FileManager : IDisposable
{
    private bool disposed = false;

    public void OpenFile()
    {
        Console.WriteLine("File opened.");
    }

    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    protected virtual void Dispose(bool disposing)
    {
        if (!disposed)
        {
            if (disposing)
            {
                // Release managed resources here
            }

            // Release unmanaged resources here
            disposed = true;
        }
    }

    ~FileManager()
    {
        Dispose(false);
    }
}

class Program
{
    static void Main()
    {
        using (FileManager manager = new FileManager())
        {
            manager.OpenFile();
        }
    }
}
```

### **Using `using` Statement**
The `using` statement ensures the `Dispose` method is called automatically.

Example:
```csharp
using (FileManager manager = new FileManager())
{
    manager.OpenFile();
}
```

---
# Static Members of a Class

### **Static Fields**
Static fields are shared among all instances of a class. They belong to the class itself rather than any specific instance.

#### Example:
```csharp
public class Counter
{
    public static int Count = 0;

    public Counter()
    {
        Count++;
    }
}

class Program
{
    static void Main()
    {
        Counter c1 = new Counter();
        Counter c2 = new Counter();
        Console.WriteLine(Counter.Count); // Output: 2
    }
}
```

---

### **Static Methods**
Static methods can be called without creating an instance of the class.

#### Example:
```csharp
public class MathUtility
{
    public static int Add(int a, int b)
    {
        return a + b;
    }
}

class Program
{
    static void Main()
    {
        int result = MathUtility.Add(5, 10);
        Console.WriteLine(result); // Output: 15
    }
}
```

---

### **Static Properties**
Static properties provide controlled access to static fields.

#### Example:
```csharp
public class Configuration
{
    private static string applicationName = "MyApp";

    public static string ApplicationName
    {
        get { return applicationName; }
        set { applicationName = value; }
    }
}

class Program
{
    static void Main()
    {
        Console.WriteLine(Configuration.ApplicationName);
        Configuration.ApplicationName = "NewApp";
        Console.WriteLine(Configuration.ApplicationName);
    }
}
```

---

### **Static Constructors**
Static constructors initialize static fields or perform actions that only need to occur once.

#### Example:
```csharp
public class Logger
{
    public static string LogPath;

    static Logger()
    {
        LogPath = "DefaultPath";
        Console.WriteLine("Static constructor called.");
    }
}

class Program
{
    static void Main()
    {
        Console.WriteLine(Logger.LogPath);
    }
}
```

---

# Static Classes

### **What are Static Classes?**
Static classes cannot be instantiated and contain only static members. They are used for grouping related methods and properties.

#### Example:
```csharp
public static class MathHelper
{
    public static int Multiply(int a, int b)
    {
        return a * b;
    }
}

class Program
{
    static void Main()
    {
        Console.WriteLine(MathHelper.Multiply(3, 4));
    }
}
```

---

# Static Local Functions

Static local functions are defined inside a method and cannot access instance members of the containing class.

#### Example:
```csharp
class Program
{
    static void Main()
    {
        int result = AddNumbers(5, 10);
        Console.WriteLine(result);

        static int AddNumbers(int a, int b)
        {
            return a + b;
        }
    }
}
```

---

# Inheritance

### **Access Specifiers**
Access specifiers control the visibility of members in a class hierarchy.

| **Access Specifier** | **Description**                                      |
|-----------------------|-----------------------------------------------------|
| `public`             | Accessible everywhere.                              |
| `protected`          | Accessible in the same class and derived classes.   |
| `private`            | Accessible only within the same class.              |
| `internal`           | Accessible within the same assembly.                |
| `protected internal` | Accessible within the same assembly or derived classes. |

---

### **Constructors in a Hierarchy**
Constructors in a base class are called before those in the derived class.

#### Example:
```csharp
public class Animal
{
    public Animal()
    {
        Console.WriteLine("Animal constructor");
    }
}

public class Dog : Animal
{
    public Dog()
    {
        Console.WriteLine("Dog constructor");
    }
}

class Program
{
    static void Main()
    {
        Dog dog = new Dog();
    }
}
```

---

### **Overloading in Derived Class**
Derived classes can have overloaded methods with different parameter lists.

#### Example:
```csharp
public class BaseClass
{
    public void Print(string message)
    {
        Console.WriteLine(message);
    }
}

public class DerivedClass : BaseClass
{
    public void Print(string message, int number)
    {
        Console.WriteLine($"{message} - {number}");
    }
}

class Program
{
    static void Main()
    {
        DerivedClass obj = new DerivedClass();

        // Calls the Print method from BaseClass (because of 1 argument)
        obj.Print("Hello from BaseClass");

        // Calls the Print method from DerivedClass (because of 2 arguments)
        obj.Print("Hello from DerivedClass", 42);
    }
}

```

---

### **Hiding Members with `new`**
The `new` keyword hides a member of the base class.

#### Example:
```csharp
public class BaseClass
{
    public void Display()
    {
        Console.WriteLine("Base Display");
    }
}

public class DerivedClass : BaseClass
{
    public new void Display()
    {
        Console.WriteLine("Derived Display");
    }
}
```

---

### **Overriding Members**
The `override` keyword is used to redefine a virtual method in a derived class.

#### Example:
```csharp
public class BaseClass
{
    public virtual void Greet()
    {
        Console.WriteLine("Hello from BaseClass");
    }
}

public class DerivedClass : BaseClass
{
    public override void Greet()
    {
        Console.WriteLine("Hello from DerivedClass");
    }
}
```

---

### **Sealed Methods**
The `sealed` keyword prevents further overriding of a method.

#### Example:
```csharp
public class BaseClass
{
    public virtual void Show()
    {
        Console.WriteLine("Base Show");
    }
}

public class DerivedClass : BaseClass
{
    public sealed override void Show()
    {
        Console.WriteLine("Derived Show");
    }
}
```

---

### **Abstract Classes and Methods**
Abstract classes cannot be instantiated and can include abstract methods that must be implemented in derived classes.

#### Example:
```csharp
public abstract class Shape
{
    public abstract double GetArea();
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double GetArea()
    {
        return Width * Height;
    }
}
```

---

### **Sealed Classes**
A sealed class cannot be inherited.

#### Example:
```csharp
public sealed class FinalClass
{
    public void Display()
    {
        Console.WriteLine("This is a sealed class.");
    }
}
```
