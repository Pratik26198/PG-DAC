
# C++ Overview and Getting Started

## Installation and Setup of Development Environment

### Install a Compiler

- **C++ requires a compiler to convert code into machine language.**
- Popular options:
  - GCC (GNU Compiler Collection)
  - Clang
  - Microsoft Visual C++

### Install an IDE/Text Editor

- IDEs:
  - Visual Studio
  - Code::Blocks
  - Eclipse CDT
  - Dev-C++
- Text Editors:
  - Visual Studio Code
  - Sublime Text
  - Atom (requires manual setup for compiling)

### Setup Environment

- **Install GCC** using MinGW for Windows or directly via package managers on Linux/macOS:
  - **Windows**: Download MinGW, configure the PATH variable to include the compiler path.
  - **Linux**: Install GCC/Clang via terminal (`sudo apt install g++` for Ubuntu).
  - **macOS**: Use `brew install gcc`.

### Testing the Installation

1. Open a terminal/command prompt.
2. Run:
   ```bash
   g++ --version
   ```
3. Create a sample program and compile it:
   ```cpp
   // test.cpp
   #include <iostream>
   using namespace std;

   int main() {
       cout << "Hello, C++!" << endl;
       return 0;
   }
   ```
4. Compile and run:
   ```bash
   g++ test.cpp -o test
   ./test
   ```

---

## The Need for C++

### Why C++?

1. **Object-Oriented Programming**:

   - Provides abstraction, encapsulation, inheritance, and polymorphism.
   - Useful for creating reusable and maintainable code.

2. **Performance**:

   - Combines the power of low-level programming (like C) with high-level abstractions.
   - Efficient for systems programming, real-time systems, and games.

3. **Wide Application**:

   - Used in fields like game development, operating systems (e.g., Windows), embedded systems, and IoT.

4. **Portability**:

   - Write code once and compile on multiple platforms with minimal changes.

5. **Standard Libraries**:

   - Offers extensive standard libraries (STL) for data structures, algorithms, and utilities.

---

## Features of C++

1. **Object-Oriented**:

   - Supports OOP principles: classes, objects, inheritance, polymorphism, and abstraction.

2. **Extensibility**:

   - Developers can create new data types using classes.

3. **Portability**:

   - Write once, run anywhere with minimal changes.

4. **Rich Standard Library**:

   - STL (Standard Template Library) offers powerful tools for data manipulation.

5. **High Performance**:

   - Combines the efficiency of C with high-level abstractions.

6. **Low-Level Manipulation**:

   - Supports pointers, memory management, and hardware interaction.

7. **Multithreading Support**:

   - Provides built-in support for concurrent and parallel programming.

8. **Generic Programming**:

   - Use templates to write reusable and type-independent code.

---

## C++ versus C

| Feature                | C          | C++                          |
| ---------------------- | ---------- | ---------------------------- |
| **Programming Type**   | Procedural | Object-Oriented + Procedural |
| **Encapsulation**      | No         | Yes                          |
| **Inheritance**        | No         | Yes                          |
| **Polymorphism**       | No         | Yes                          |
| **Data Hiding**        | No         | Yes                          |
| **Exception Handling** | No         | Yes                          |
| **STL Support**        | No         | Yes                          |
| **Namespaces**         | No         | Yes                          |
| **File Extension**     | `.c`       | `.cpp`                       |

---

## History of C++

### Development

- Created by **Bjarne Stroustrup** at Bell Labs in 1979.
- Initially called "C with Classes."

### Key Milestones

- 1983: Renamed to C++ (increment operator to signify enhancement of C).
- 1985: First official release.
- 1998: ISO standardization (C++98).
- 2011, 2014, 2017, 2020: Major updates introducing modern features (e.g., lambdas, smart pointers, ranges).

### Purpose

- Extend the power of C with object-oriented features and maintain backward compatibility.

---

## Writing Your First C++ Program

### Program Code

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Welcome to the world of C++!" << endl;
    return 0;
}
```

### Explanation

1. **#include **: Includes the library for input and output.
2. **using namespace std**: Simplifies usage of `std` prefix for standard functions.
3. **main()**: Entry point of the program.
4. **cout**: Outputs data to the console.

### Steps to Compile and Run

1. Save the program as `hello.cpp`.
2. Open terminal/command prompt and compile:
   ```bash
   g++ hello.cpp -o hello
   ```
3. Run the program:
   ```bash
   ./hello
   ```
4. Output:
   ```
   Welcome to the world of C++!
   ```

