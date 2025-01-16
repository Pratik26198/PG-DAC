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
class Program
{
    static void Main()
    {
        BaseClass baseObj = new BaseClass();
        baseObj.Display(); // Calls BaseClass.Display

        DerivedClass derivedObj = new DerivedClass();
        derivedObj.Display(); // Calls DerivedClass.Display

        BaseClass baseRefDerived = new DerivedClass();
        baseRefDerived.Display(); // Calls BaseClass.Display due to method hiding
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
# Interfaces in C#

### **What are Interfaces?**
An interface in C# defines a contract that classes or structs can implement. Interfaces specify what a class must do but not how it does it.

#### Key Features:
- Interfaces cannot have fields or implementation.
- A class can implement multiple interfaces.
- Interface members are public and abstract by default.

---

## **Implementing an Interface**
To implement an interface, a class must provide definitions for all the members declared in the interface.

#### Example:
```csharp
public interface IShape
{
    double GetArea();
}

public class Circle : IShape
{
    public double Radius { get; set; }

    public double GetArea()
    {
        return Math.PI * Radius * Radius;
    }
}

class Program
{
    static void Main()
    {
        Circle circle = new Circle { Radius = 5 };
        Console.WriteLine($"Area: {circle.GetArea()}");
    }
}
```

---

## **Explicitly Implementing an Interface**
Explicit implementation is used when a class implements multiple interfaces, and there is a possibility of naming conflicts.

#### Example:
```csharp
public interface IWalk
{
    void Move();
}

public interface IRun
{
    void Move();
}

public class Person : IWalk, IRun
{
    void IWalk.Move()
    {
        Console.WriteLine("Walking");
    }

    void IRun.Move()
    {
        Console.WriteLine("Running");
    }
}

class Program
{
    static void Main()
    {
        Person person = new Person();
        ((IWalk)person).Move(); // Output: Walking
        ((IRun)person).Move(); // Output: Running
    }
}
```

---

## **Inheritance in Interfaces**
Interfaces can inherit from other interfaces, allowing a derived interface to inherit members from the base interface.

#### Example:
```csharp
public interface IVehicle
{
    void Start();
}

public interface ICar : IVehicle
{
    void Drive();
}

public class Sedan : ICar
{
    public void Start()
    {
        Console.WriteLine("Car started");
    }

    public void Drive()
    {
        Console.WriteLine("Driving");
    }
}

class Program
{
    static void Main()
    {
        Sedan sedan = new Sedan();
        sedan.Start(); // Output: Car started
        sedan.Drive(); // Output: Driving
    }
}
```

---

## **Default Interface Methods**
C# 8.0 introduced **default interface methods**, allowing interfaces to provide a default implementation for its members.

#### Example:
```csharp
public interface ILogger
{
    void Log(string message);

    // Default implementation
    void LogError(string message)
    {
        Console.WriteLine($"Error: {message}");
    }
}

public class ConsoleLogger : ILogger
{
    public void Log(string message)
    {
        Console.WriteLine($"Log: {message}");
    }
}

class Program
{
    static void Main()
    {
        ILogger logger = new ConsoleLogger();
        logger.Log("This is a log message.");
        logger.LogError("This is an error message.");
    }
}
```

---

# Operator Overloading

### **What is Operator Overloading?**
Operator overloading allows you to redefine or "overload" the behavior of operators for user-defined types.

#### Key Points:
- Only certain operators can be overloaded.
- The `operator` keyword is used.
- Overloading does not change the precedence or associativity of operators.

#### Example:
```csharp
public class Complex
{
    public double Real { get; set; }
    public double Imaginary { get; set; }

    public Complex(double real, double imaginary)
    {
        Real = real;
        Imaginary = imaginary;
    }

    // Overloading the + operator
    public static Complex operator +(Complex c1, Complex c2)
    {
        return new Complex(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);
    }

    public override string ToString()
    {
        return $"{Real} + {Imaginary}i";
    }
}

class Program
{
    static void Main()
    {
        Complex c1 = new Complex(1, 2);
        Complex c2 = new Complex(3, 4);
        Complex result = c1 + c2;
        Console.WriteLine(result); // Output: 4 + 6i
    }
}
```

---

### **Operators That Can Be Overloaded**

| **Operator**  | **Description**       |
|---------------|-----------------------|
| `+`           | Addition              |
| `-`           | Subtraction           |
| `*`           | Multiplication        |
| `/`           | Division              |
| `==`          | Equality              |
| `!=`          | Inequality            |
| `<`           | Less than             |
| `>`           | Greater than          |

### **Operators That Cannot Be Overloaded**

| **Operator**  | **Description**       |
|---------------|-----------------------|
| `=`           | Assignment            |
| `.`           | Member access         |
| `?:`          | Ternary conditional   |
| `new`         | Object creation       |
| `typeof`      | Type information      |

---

# Reference and Value Types in C#

C# has two main types of data:
1. **Value Types**: Store the actual data.
2. **Reference Types**: Store a reference to the memory location where the data is stored.

---

## **Value Types**

Value types are stored on the stack, and variables directly contain their values. Examples include:
- Primitive types (`int`, `float`, `bool`, etc.)
- `struct`
- `enum`

### **Structs**
Structs are lightweight data types that group related variables.

#### Example:
```csharp
public struct Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y)
    {
        X = x;
        Y = y;
    }
}

class Program
{
    static void Main()
    {
        Point p = new Point(3, 4);
        Console.WriteLine($"Point: ({p.X}, {p.Y})");
    }
}
```

---

### **Enums**
Enums represent a set of named constants.

#### Example:
```csharp
public enum Days
{
    Sunday,
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday
}

class Program
{
    static void Main()
    {
        Days today = Days.Monday;
        Console.WriteLine(today); // Output: Monday
    }
}
```

---

## **Reference Types**
Reference types store the reference (or address) of the data, which is allocated on the heap. Examples include:
- Classes
- Delegates
- Arrays

---

# **`out` and `ref` Keywords**

### **`ref` Keyword**
Allows passing variables by reference so that changes affect the original variable.

#### Example:
```csharp
class Program
{
    static void Increment(ref int number)
    {
        number++;
    }

    static void Main()
    {
        int value = 5;
        Increment(ref value);
        Console.WriteLine(value); // Output: 6
    }
}
```

---

### **`out` Keyword**
The `out` keyword is used to return multiple values from a method.

#### Example:
```csharp
class Program
{
    static void GetValues(out int a, out int b)
    {
        a = 10;
        b = 20;
    }

    static void Main()
    {
        GetValues(out int x, out int y);
        Console.WriteLine($"x: {x}, y: {y}");
    }
}
```

---

# Nullable Types

### **Nullable Value Types**
Allow value types to hold `null` using the `?` operator.

#### Example:
```csharp
class Program
{
    static void Main()
    {
        int? age = null;
        Console.WriteLine(age ?? 0); // Output: 0

        age = 25;
        Console.WriteLine(age ?? 0); // Output: 25
    }
}
```

---

### **Nullable Reference Types**
Introduced in C# 8.0, nullable reference types help avoid `null` reference exceptions.

#### Example:
```csharp
#nullable enable
class Program
{
    static void PrintName(string? name)
    {
        if (name != null)
        {
            Console.WriteLine(name);
        }
    }

    static void Main()
    {
        PrintName("John");
        PrintName(null); // Safely handled
    }
}
```

---

# **`??` and `??=` Operators**

### **`??` Operator**
The null-coalescing operator returns the left-hand operand if it is not `null`; otherwise, it returns the right-hand operand.

#### Example:
```csharp
string? name = null;
Console.WriteLine(name ?? "Unknown"); // Output: Unknown
```

### **`??=` Operator**
Assigns the right-hand operand to the left-hand operand only if the left-hand operand is `null`.

#### Example:
```csharp
string? name = null;
name ??= "Default";
Console.WriteLine(name); // Output: Default
```

---

# Working with Arrays

### **Single-Dimensional Arrays**
A simple list of elements of the same type.

#### Example:
```csharp
int[] numbers = { 1, 2, 3, 4 };
foreach (int number in numbers)
{
    Console.WriteLine(number);
}
```

---

### **Multi-Dimensional Arrays**
Arrays with rows and columns.

#### Example:
```csharp
int[,] matrix = { { 1, 2 }, { 3, 4 } };
Console.WriteLine(matrix[0, 1]); // Output: 2
```

---

### **Jagged Arrays**
An array of arrays with different lengths.

#### Example:
```csharp
int[][] jaggedArray = new int[2][];
jaggedArray[0] = new int[] { 1, 2 };
jaggedArray[1] = new int[] { 3, 4, 5 };
Console.WriteLine(jaggedArray[1][2]); // Output: 5
```

---

### **Array Class Members**
| **Member**    | **Description**                               |
|---------------|-----------------------------------------------|
| `Length`      | Gets the total number of elements.            |
| `Sort`        | Sorts the elements in the array.              |
| `IndexOf`     | Finds the index of a specific element.        |
| `Reverse`     | Reverses the order of elements.               |

#### Example:
```csharp
int[] numbers = { 3, 1, 4, 1, 5 };
Array.Sort(numbers);
Array.Reverse(numbers);
foreach (int number in numbers)
{
    Console.WriteLine(number);
}
```

---

# Indices and Ranges

### **Indices**
Indices provide a way to access elements from the end using the `^` symbol.

#### Example:
```csharp
int[] numbers = { 10, 20, 30, 40 };
Console.WriteLine(numbers[^1]); // Output: 40
```

### **Ranges**
Ranges allow you to specify a subset of elements using the `..` operator.

#### Example:
```csharp
int[] numbers = { 10, 20, 30, 40 };
int[] subset = numbers[1..3];
foreach (int number in subset)
{
    Console.WriteLine(number);    //20 30

}
```

---

# Indexers

### **What are Indexers?**
Indexers allow objects to be indexed like arrays.

#### Example:
```csharp
public class SampleCollection
{
    private string[] data = new string[10];

    public string this[int index]
    {
        get { return data[index]; }
        set { data[index] = value; }
    }
}

class Program
{
    static void Main()
    {
        var collection = new SampleCollection();
        collection[0] = "Hello";
        Console.WriteLine(collection[0]); // Output: Hello
    }
}
```
# Generics in C#

## **Generic Classes**
Generic classes provide a way to create classes that can work with any data type without specifying the type at the time of creation.

#### Example:
```csharp
public class Box<T>
{
    public T Content { get; set; }
}

class Program
{
    static void Main()
    {
        Box<int> intBox = new Box<int> { Content = 42 };
        Box<string> stringBox = new Box<string> { Content = "Hello" };

        Console.WriteLine(intBox.Content);  // Output: 42
        Console.WriteLine(stringBox.Content); // Output: Hello
    }
}
```

---

## **Generic Methods**
Generic methods allow you to define a method with type parameters.

#### Example:
```csharp
public class Utilities
{
    public T GetDefault<T>()
    {
        return default(T);
    }
}

class Program
{
    static void Main()
    {
        Utilities util = new Utilities();
        int defaultInt = util.GetDefault<int>();
        string defaultString = util.GetDefault<string>();

        Console.WriteLine(defaultInt);    // Output: 0
        Console.WriteLine(defaultString); // Output: (null)
    }
}
```

---

## **Generic Constraints**
Constraints specify restrictions on the types that can be used as arguments for a generic type or method.

### **Common Constraints:**
| **Constraint**      | **Description**                                         |
|---------------------|---------------------------------------------------------|
| `where T : class`   | T must be a reference type.                             |
| `where T : struct`  | T must be a value type.                                 |
| `where T : new()`   | T must have a parameterless constructor.                |
| `where T : BaseClass` | T must inherit from `BaseClass`.                       |
| `where T : Interface` | T must implement the specified interface.              |

#### Example:
```csharp
public class Repository<T> where T : class, new()
{
    public T Create()
    {
        return new T();
    }
}

class Program
{
    static void Main()
    {
        Repository<StringBuilder> repo = new Repository<StringBuilder>();
        StringBuilder sb = repo.Create();
        Console.WriteLine(sb.GetType()); // Output: System.Text.StringBuilder
    }
}
```

---

# Collections in C#

## **Generic Collections**
Generic collections provide type safety and are part of the `System.Collections.Generic` namespace.

| **Collection**       | **Description**                                      |
|----------------------|------------------------------------------------------|
| `List<T>`            | Dynamic array with type safety.                      |
| `Dictionary<TKey, TValue>` | Key-value pair collection.                      |
| `Queue<T>`           | FIFO (First In, First Out) collection.               |
| `Stack<T>`           | LIFO (Last In, First Out) collection.                |
| `HashSet<T>`         | Collection of unique elements.                       |

### Example:
```csharp
List<int> numbers = new List<int> { 1, 2, 3 };
numbers.Add(4);
foreach (int number in numbers)
{
    Console.WriteLine(number);
}
```

---

## **Non-Generic Collections**
Non-generic collections are part of the `System.Collections` namespace and do not provide type safety.

| **Collection**       | **Description**                                      |
|----------------------|------------------------------------------------------|
| `ArrayList`          | Dynamic array that can store objects of any type.    |
| `Hashtable`          | Key-value pair collection.                          |
| `Queue`              | FIFO collection for objects.                        |
| `Stack`              | LIFO collection for objects.                        |

### Example:
```csharp
ArrayList list = new ArrayList();
list.Add(1);
list.Add("two");
list.Add(3.0);
foreach (var item in list)
{
    Console.WriteLine(item);
}
```

---

# **ICollection, IList, and IDictionary Examples**

### **ICollection**
Defines size, enumerators, and sync methods for collections.

#### Example:
```csharp
ICollection<int> collection = new List<int> { 1, 2, 3 };
foreach (int item in collection)
{
    Console.WriteLine(item);
}
```

### **IList**
Supports indexed access to elements.

#### Example:
```csharp
IList<string> list = new List<string> { "A", "B", "C" };
list[1] = "D";
foreach (string item in list)
{
    Console.WriteLine(item);
}
```

### **IDictionary**
Key-value pair collection.

#### Example:
```csharp
IDictionary<int, string> dictionary = new Dictionary<int, string>
{
    { 1, "One" },
    { 2, "Two" }
};
foreach (var pair in dictionary)
{
    Console.WriteLine($"Key: {pair.Key}, Value: {pair.Value}");
}
```

---

# Iterating Collections Using `foreach`

`foreach` loops provide an easy way to iterate over collections.

#### Example:
```csharp
List<string> names = new List<string> { "Alice", "Bob", "Charlie" };
foreach (string name in names)
{
    Console.WriteLine(name);
}
```

---

# Using Tuples to Pass Multiple Values to a Function

Tuples allow returning multiple values from a method.

### **Example:**
```csharp
public static (int Sum, int Product) Calculate(int a, int b)
{
    return (a + b, a * b);
}

class Program
{
    static void Main()
    {
        var result = Calculate(3, 4);
        Console.WriteLine($"Sum: {result.Sum}, Product: {result.Product}");
    }
}
```

---
# Delegates in C#

### **What are Delegates?**
A delegate is a type-safe function pointer that allows methods to be passed as parameters.

#### Key Features:
- Delegates are reference types.
- They allow methods to be assigned to variables.
- They can point to static or instance methods.

#### Example:
```csharp
public delegate void GreetDelegate(string name);

class Program
{
    static void Greet(string name)
    {
        Console.WriteLine($"Hello, {name}!");
    }

    static void Main()
    {
        GreetDelegate greet = Greet;
        greet("Alice"); // Output: Hello, Alice!
    }
}
```

---

## **Calling Methods Using Delegates**
Delegates allow calling methods dynamically at runtime.

#### Example:
```csharp
public delegate int MathOperation(int a, int b);

class Program
{
    static int Add(int x, int y) => x + y;
    static int Multiply(int x, int y) => x * y;

    static void Main()
    {
        MathOperation operation = Add;
        Console.WriteLine(operation(3, 4)); // Output: 7

        operation = Multiply;
        Console.WriteLine(operation(3, 4)); // Output: 12
    }
}
```

---

## **Uses of Delegates**
- Event handling.
- Callbacks in asynchronous programming.
- Passing methods as arguments to other methods.
- Defining custom behavior in frameworks.

---

## **Multicast Delegates**
Multicast delegates can point to multiple methods. They execute methods in the order they were added.

#### Example:
```csharp
public delegate void Notify();

class Program
{
    static void Notify1() => Console.WriteLine("Notification 1");
    static void Notify2() => Console.WriteLine("Notification 2");

    static void Main()
    {
        Notify notifications = Notify1;
        notifications += Notify2;

        notifications();
        // Output:
        // Notification 1
        // Notification 2
    }
}
```

---

## **Action, Func, Predicate Delegates**

### **Action Delegate**
Represents a delegate that takes parameters but does not return a value.

#### Example:
```csharp
Action<string> greet = name => Console.WriteLine($"Hello, {name}!");
greet("Alice"); // Output: Hello, Alice!
```

### **Func Delegate**
Represents a delegate that takes parameters and returns a value.

#### Example:
```csharp
Func<int, int, int> add = (a, b) => a + b;
Console.WriteLine(add(3, 4)); // Output: 7
```

### **Predicate Delegate**
Represents a delegate that takes one parameter and returns a boolean value.

#### Example:
```csharp
Predicate<int> isPositive = number => number > 0;
Console.WriteLine(isPositive(5));  // Output: True
Console.WriteLine(isPositive(-1)); // Output: False
```

---

# Anonymous Methods
Anonymous methods allow you to define a delegate inline without declaring a separate method.

#### Example:
```csharp
public delegate void Print(string message);

class Program
{
    static void Main()
    {
        Print print = delegate(string message)
        {
            Console.WriteLine(message);
        };

        print("Hello, Anonymous Method!");
    }
}
```

---

# Lambdas
Lambdas are shorthand syntax for writing inline functions and are commonly used with delegates.

### **Syntax:**
```csharp
(parameters) => expression
```

#### Example:
```csharp
Func<int, int, int> multiply = (x, y) => x * y;
Console.WriteLine(multiply(3, 4)); // Output: 12
```

---

## **Lambdas in LINQ**
Lambdas are widely used in LINQ for querying collections.

#### Example:
```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(n => n % 2 == 0);

foreach (var num in evenNumbers)
{
    Console.WriteLine(num); // Output: 2, 4
}
```

---
# Error Handling in C#

Error handling in C# is primarily achieved through exceptions, which provide a structured way to handle runtime errors.

---

## **Checked & Unchecked Statements**

### **Checked**
The `checked` keyword ensures that arithmetic operations and conversions that exceed their limits throw an `OverflowException`.

#### Example:
```csharp
class Program
{
    static void Main()
    {
        int max = int.MaxValue;
        try
        {
            int result = checked(max + 1);
        }
        catch (OverflowException ex)
        {
            Console.WriteLine("Overflow detected: " + ex.Message);
        }
    }
}
```

### **Unchecked**
The `unchecked` keyword disables overflow checking for arithmetic operations and conversions.

#### Example:
```csharp
class Program
{
    static void Main()
    {
        int max = int.MaxValue;
        int result = unchecked(max + 1);
        Console.WriteLine(result); // Output: -2147483648 (wrapped around)
    }
}
```

---

## **The try, catch, finally Blocks**

### **Structure**
- **`try`**: Defines the block of code to test for exceptions.
- **`catch`**: Defines the block to handle exceptions.
- **`finally`**: Defines a block that executes regardless of whether an exception occurs.

#### Example:
```csharp
class Program
{
    static void Main()
    {
        try
        {
            int result = 10 / 0;
        }
        catch (DivideByZeroException ex)
        {
            Console.WriteLine("Error: " + ex.Message);
        }
        finally
        {
            Console.WriteLine("Execution completed.");
        }
    }
}
```

### **Multiple Catch Blocks**
You can use multiple `catch` blocks to handle different types of exceptions.

#### Example:
```csharp
try
{
    int[] numbers = { 1, 2 };
    Console.WriteLine(numbers[5]);
}
catch (IndexOutOfRangeException ex)
{
    Console.WriteLine("Index error: " + ex.Message);
}
catch (Exception ex)
{
    Console.WriteLine("General error: " + ex.Message);
}
```

---

## **Dos & Don’ts of Exception Handling**

### **Dos**:
1. Handle exceptions at appropriate levels in your application.
2. Use specific exception types in `catch` blocks.
3. Log exceptions for debugging purposes.
4. Clean up resources in the `finally` block or with `using` statements.

### **Don’ts**:
1. Avoid catching generic exceptions like `Exception` unless necessary.
2. Do not suppress exceptions without logging them.
3. Avoid using exceptions for flow control.
4. Never catch exceptions you can’t handle.

---

## **User-Defined Exception Classes**
You can define custom exception classes by inheriting from `System.Exception`.

#### Example:
```csharp
public class InvalidAgeException : Exception
{
    public InvalidAgeException(string message) : base(message)
    {
    }
}

class Program
{
    static void ValidateAge(int age)
    {
        if (age < 18)
        {
            throw new InvalidAgeException("Age must be 18 or above.");
        }
    }

    static void Main()
    {
        try
        {
            ValidateAge(15);
        }
        catch (InvalidAgeException ex)
        {
            Console.WriteLine("Error: " + ex.Message);
        }
    }
}
```

---

# Events in C#

Events provide a way to notify subscribers when something occurs. They are based on delegates and follow the publisher-subscriber model.

## **Declaring and Raising Events**

### **Steps to Declare an Event:**
1. Define a delegate.
2. Declare an event using the delegate.
3. Raise the event in the class.

#### Example:
```csharp
// Step 1: Define a delegate
public delegate void NotifyEventHandler(string message);

// Step 2: Declare an event
public class EventPublisher
{
    public event NotifyEventHandler Notify;

    public void RaiseEvent()
    {
        // Step 3: Raise the event
        Notify?.Invoke("Event has been raised!");
    }
}

class Program
{
    static void Main()
    {
        EventPublisher publisher = new EventPublisher();

        // Subscribe to the event
        publisher.Notify += (message) => Console.WriteLine(message);

        publisher.RaiseEvent(); // Output: Event has been raised!
    }
}
```

---

## **Handling Events**

### Example:
```csharp
public class Alarm
{
    public event Action AlarmTriggered;

    public void TriggerAlarm()
    {
        Console.WriteLine("Alarm is being triggered...");
        AlarmTriggered?.Invoke();
    }
}

class Program
{
    static void Main()
    {
        Alarm alarm = new Alarm();

        // Subscribe to the event
        alarm.AlarmTriggered += () => Console.WriteLine("Alarm Received!");

        alarm.TriggerAlarm();
        // Output:
        // Alarm is being triggered...
        // Alarm Received!
    }
}
```

---
# Advanced Topics in C#

## **Anonymous Types**
Anonymous types allow you to create objects without explicitly defining a class.

### **Key Features:**
- Properties are defined inline.
- Read-only properties.
- Type is determined at compile-time.

### **Example:**
```csharp
var student = new { Name = "Alice", Age = 21 };
Console.WriteLine($"Name: {student.Name}, Age: {student.Age}");
```

---

## **Extension Methods**
Extension methods allow you to add new methods to an existing type without modifying its source code.

### **Key Features:**
- Defined as `static` methods.
- The first parameter specifies the type it extends, prefixed with `this`.

### **Example:**
```csharp
public static class StringExtensions
{
    public static bool IsNullOrEmpty(this string str)
    {
        return string.IsNullOrEmpty(str);
    }
}

class Program
{
    static void Main()
    {
        string text = "Hello";
        Console.WriteLine(text.IsNullOrEmpty()); // Output: False
    }
}
```

---

## **Partial Classes**
Partial classes allow a class definition to be split across multiple files. Useful in large projects for better organization.

### **Key Features:**
- All parts must use the `partial` keyword.
- Combined into a single class during compilation.

### **Example:**
**File 1:**
```csharp
public partial class Person
{
    public string FirstName { get; set; }
}
```
**File 2:**
```csharp
public partial class Person
{
    public string LastName { get; set; }
}
```
**Usage:**
```csharp
class Program
{
    static void Main()
    {
        Person person = new Person { FirstName = "Alice", LastName = "Johnson" };
        Console.WriteLine($"{person.FirstName} {person.LastName}");
    }
}
```

---

## **Partial Methods**
Partial methods allow the declaration of a method in one part of a partial class, and optional implementation in another part.

### **Key Features:**
- Must have `partial` keyword.
- No access modifiers (implicitly private).
- If unimplemented, the method is removed at compile-time.

### **Example:**
**File 1:**
```csharp
public partial class Logger
{
    partial void Log(string message);

    public void Process()
    {
        Log("Processing started");
    }
}
```
**File 2:**
```csharp
public partial class Logger
{
    partial void Log(string message)
    {
        Console.WriteLine(message);
    }
}
```

---

## **LINQ to Objects**
LINQ (Language Integrated Query) to Objects allows querying in-memory collections using a SQL-like syntax.

### **Example:**
```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
var evenNumbers = from n in numbers
                  where n % 2 == 0
                  select n;

foreach (var number in evenNumbers)
{
    Console.WriteLine(number); // Output: 2, 4
}
```

---

## **Writing LINQ Queries**
LINQ queries can be written in two styles:

1. **Query Syntax**:
   ```csharp
   var query = from n in numbers
               where n > 2
               select n;
   ```

2. **Method Syntax**:
   ```csharp
   var query = numbers.Where(n => n > 2);
   ```

---

## **Deferred Execution**
In LINQ, queries are not executed until the data is enumerated.

### **Example:**
```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
var query = numbers.Where(n => n > 2);

// Numbers modified before enumeration
numbers[2] = 10;

foreach (var number in query)
{
    Console.WriteLine(number); // Output: 10, 4, 5
}
```

---

## **LINQ Methods**
LINQ provides a rich set of methods for querying data.

| **Method**   | **Description**                             |
|--------------|---------------------------------------------|
| `Where`      | Filters elements based on a condition.      |
| `Select`     | Projects each element into a new form.      |
| `OrderBy`    | Sorts elements in ascending order.          |
| `OrderByDescending` | Sorts elements in descending order.  |
| `GroupBy`    | Groups elements by a key.                  |
| `Join`       | Joins two collections based on a key.       |
| `Aggregate`  | Performs an accumulation operation.         |

### **Example:**
```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
var doubled = numbers.Select(n => n * 2);

foreach (var number in doubled)
{
    Console.WriteLine(number); // Output: 2, 4, 6, 8, 10
}
```

---

## **PLINQ (Parallel LINQ)**
PLINQ extends LINQ by executing queries in parallel to improve performance.

### **Example:**
```csharp
int[] numbers = Enumerable.Range(1, 10).ToArray();
var evenNumbers = numbers.AsParallel()
                         .Where(n => n % 2 == 0);

foreach (var number in evenNumbers)
{
    Console.WriteLine(number);
}
```

---
# Advanced Topics in C#

## **Creating a Shared Assembly**
A shared assembly is an assembly that can be used by multiple applications. It is typically stored in the Global Assembly Cache (GAC).

### **Steps to Create a Shared Assembly**:
1. **Create the Assembly**:
   ```csharp
   public class SharedLibrary
   {
       public void PrintMessage()
       {
           Console.WriteLine("This is a shared library");
       }
   }
   ```

2. **Sign the Assembly**:
   - Generate a strong name key file:
     ```bash
     sn -k SharedLibrary.snk
     ```
   - Add the key to the assembly:
     ```csharp
     [assembly: AssemblyKeyFile("SharedLibrary.snk")]
     ```

3. **Compile the Assembly**:
   ```bash
   csc /target:library /out:SharedLibrary.dll SharedLibrary.cs
   ```

4. **Install in GAC** (Windows only):
   ```bash
   gacutil -i SharedLibrary.dll
   ```

---

## **Creating Custom Attributes**
Custom attributes allow developers to add metadata to code elements like classes, methods, and properties.

### **Steps to Create a Custom Attribute**:
1. Create a class derived from `System.Attribute`.
2. Apply the attribute to code elements.

### **Example:**
```csharp
[AttributeUsage(AttributeTargets.Class | AttributeTargets.Method)]
public class DeveloperAttribute : Attribute
{
    public string Name { get; }
    public string Date { get; }

    public DeveloperAttribute(string name, string date)
    {
        Name = name;
        Date = date;
    }
}

[Developer("Alice", "2025-01-16")]
public class ExampleClass
{
    public void Display()
    {
        Console.WriteLine("Example class");
    }
}
```

---

## **Using Reflection to Explore an Assembly**
Reflection allows you to inspect assemblies, types, and their members at runtime.

### **Example:**
```csharp
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        Assembly assembly = Assembly.GetExecutingAssembly();
        Console.WriteLine("Types in the assembly:");

        foreach (Type type in assembly.GetTypes())
        {
            Console.WriteLine($"Type: {type.Name}");

            foreach (MethodInfo method in type.GetMethods())
            {
                Console.WriteLine($"  Method: {method.Name}");
            }
        }
    }
}
```

---

## **Using Reflection to Load an Assembly Dynamically**
You can load assemblies dynamically at runtime using `Assembly.Load` or `Assembly.LoadFrom`.

### **Example:**
```csharp
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        Assembly assembly = Assembly.LoadFrom("SharedLibrary.dll");
        Type type = assembly.GetType("SharedLibrary");

        object instance = Activator.CreateInstance(type);
        MethodInfo method = type.GetMethod("PrintMessage");

        method.Invoke(instance, null);
    }
}
```

---

## **Files I/O and Streams**
File I/O in C# is used to perform read and write operations on files, directories, and streams.

### **Working with Drives, Directories, and Files**
#### **Listing Drives**:
```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        foreach (var drive in DriveInfo.GetDrives())
        {
            Console.WriteLine($"Drive: {drive.Name}, Type: {drive.DriveType}");
        }
    }
}
```

#### **Working with Directories**:
```csharp
string path = "./TestDirectory";

// Create directory
Directory.CreateDirectory(path);

// Check if directory exists
if (Directory.Exists(path))
{
    Console.WriteLine("Directory created");
}

// Delete directory
Directory.Delete(path);
```

#### **Working with Files**:
```csharp
string filePath = "./test.txt";

// Create and write to file
File.WriteAllText(filePath, "Hello, File I/O!");

// Read from file
string content = File.ReadAllText(filePath);
Console.WriteLine(content);
```

---

## **Reading and Writing Files**

### **Using FileStream**:
#### **Writing to a File**:
```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        string filePath = "./file.txt";

        using (FileStream fs = new FileStream(filePath, FileMode.Create))
        {
            byte[] data = System.Text.Encoding.UTF8.GetBytes("Hello, FileStream!");
            fs.Write(data, 0, data.Length);
        }
    }
}
```

#### **Reading from a File**:
```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        string filePath = "./file.txt";

        using (FileStream fs = new FileStream(filePath, FileMode.Open))
        {
            byte[] data = new byte[fs.Length];
            fs.Read(data, 0, data.Length);
            Console.WriteLine(System.Text.Encoding.UTF8.GetString(data));
        }
    }
}
```

---

### **Using StreamReader and StreamWriter**

#### **Writing to a File**:
```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        using (StreamWriter writer = new StreamWriter("./output.txt"))
        {
            writer.WriteLine("Hello, StreamWriter!");
        }
    }
}
```

#### **Reading from a File**:
```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        using (StreamReader reader = new StreamReader("./output.txt"))
        {
            string content = reader.ReadToEnd();
            Console.WriteLine(content);
        }
    }
}
```

---
# Advanced Topics in C#: Threading and Tasks

## **Threading in C#**
Threading allows you to perform multiple tasks simultaneously, enabling parallel execution of code.

---

### **ThreadStart and ParameterizedThreadStart**
Threads are created using the `Thread` class and can execute methods defined by `ThreadStart` or `ParameterizedThreadStart` delegates.

#### **ThreadStart Example:**
```csharp
using System;
using System.Threading;

class Program
{
    static void PrintNumbers()
    {
        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine(i);
            Thread.Sleep(500); // Pause for 500ms
        }
    }

    static void Main()
    {
        Thread thread = new Thread(new ThreadStart(PrintNumbers));
        thread.Start();
    }
}
```

#### **ParameterizedThreadStart Example:**
```csharp
using System;
using System.Threading;

class Program
{
    static void PrintMessage(object message)
    {
        Console.WriteLine(message);
    }

    static void Main()
    {
        Thread thread = new Thread(new ParameterizedThreadStart(PrintMessage));
        thread.Start("Hello, Thread!");
    }
}
```

---

### **ThreadPool**
The `ThreadPool` class manages a pool of worker threads that can execute tasks efficiently.

#### **Example:**
```csharp
using System;
using System.Threading;

class Program
{
    static void TaskCallback(object state)
    {
        Console.WriteLine($"Task executed by Thread {Thread.CurrentThread.ManagedThreadId}");
    }

    static void Main()
    {
        ThreadPool.QueueUserWorkItem(TaskCallback);
        Console.WriteLine("Task queued");
        Thread.Sleep(1000); // Wait for thread pool task to complete
    }
}
```

---

### **Synchronizing Critical Data**
When multiple threads access shared resources, synchronization is required to avoid data corruption.

#### **Using `lock`:**
```csharp
class Program
{
    private static int counter = 0;
    private static readonly object lockObject = new object();

    static void Increment()
    {
        lock (lockObject)
        {
            counter++;
            Console.WriteLine(counter);
        }
    }

    static void Main()
    {
        Thread t1 = new Thread(Increment);
        Thread t2 = new Thread(Increment);
        t1.Start();
        t2.Start();
    }
}
```

#### **Using `Monitor`:**
```csharp
class Program
{
    private static int counter = 0;
    private static readonly object monitorObject = new object();

    static void Increment()
    {
        Monitor.Enter(monitorObject);
        try
        {
            counter++;
            Console.WriteLine(counter);
        }
        finally
        {
            Monitor.Exit(monitorObject);
        }
    }

    static void Main()
    {
        Thread t1 = new Thread(Increment);
        Thread t2 = new Thread(Increment);
        t1.Start();
        t2.Start();
    }
}
```

#### **Using `Interlocked`:**
```csharp
using System;
using System.Threading;

class Program
{
    private static int counter = 0;

    static void Increment()
    {
        Interlocked.Increment(ref counter);
        Console.WriteLine(counter);
    }

    static void Main()
    {
        Thread t1 = new Thread(Increment);
        Thread t2 = new Thread(Increment);
        t1.Start();
        t2.Start();
    }
}
```

---

## **Working with Tasks**
Tasks simplify the management of parallelism and asynchronous programming in C#.

---

### **Calling Functions with and Without Return Values**

#### **Task Without Return Value:**
```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task PrintMessageAsync()
    {
        await Task.Delay(1000);
        Console.WriteLine("Hello from Task");
    }

    static void Main()
    {
        Task task = PrintMessageAsync();
        task.Wait();
    }
}
```

#### **Task With Return Value:**
```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task<int> CalculateSumAsync(int a, int b)
    {
        await Task.Delay(500);
        return a + b;
    }

    static async Task Main()
    {
        int result = await CalculateSumAsync(5, 10);
        Console.WriteLine($"Result: {result}");
    }
}
```

---

### **Using `async` and `await`**
`async` and `await` make it easier to write asynchronous code.

#### **Example:**
```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task ProcessAsync()
    {
        Console.WriteLine("Starting process...");
        await Task.Delay(2000);
        Console.WriteLine("Process completed.");
    }

    static async Task Main()
    {
        await ProcessAsync();
    }
}
```

---

## **Using the Task Parallel Library (TPL)**
The Task Parallel Library (TPL) simplifies writing parallel code by providing high-level abstractions.

### **Example:**
#### **Parallel For:**
```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static void Main()
    {
        Parallel.For(0, 10, i =>
        {
            Console.WriteLine($"Processing {i} on Thread {Task.CurrentId}");
        });
    }
}
```

#### **Parallel ForEach:**
```csharp
using System;
using System.Collections.Generic;
using System.Threading.Tasks;

class Program
{
    static void Main()
    {
        var numbers = new List<int> { 1, 2, 3, 4, 5 };
        Parallel.ForEach(numbers, number =>
        {
            Console.WriteLine($"Processing {number} on Thread {Task.CurrentId}");
        });
    }
}
```

---
