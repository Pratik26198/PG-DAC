
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

# C++ Concepts and Features

## **1. C++ Program Structure**
A typical C++ program consists of the following components:

1. **Preprocessor Directives**: Begin with `#include` statements for libraries.
   ```cpp
   #include <iostream>
   using namespace std;
   ```

2. **Namespace Declaration**: Defines a scope to avoid name conflicts.
   ```cpp
   using namespace std;
   ```

3. **Function Declaration**: Declare all functions before they are used.
   ```cpp
   int add(int a, int b);
   ```

4. **Main Function**: The entry point of the program.
   ```cpp
   int main() {
       // Your code here
       return 0;
   }
   ```

5. **Other Components**: Function definitions, classes, and member functions.

---

## **2. Advanced C++ Concepts and Features of C++17**

### **Advanced Concepts:**
1. **Lambda Expressions**:
   Inline functions that can capture variables.
   ```cpp
   auto sum = [](int a, int b) { return a + b; };
   cout << sum(5, 3); // Output: 8
   ```

2. **Smart Pointers**:
   Automatic memory management (`unique_ptr`, `shared_ptr`).
   ```cpp
   unique_ptr<int> p = make_unique<int>(10);
   ```

3. **Templates**:
   Write generic and reusable code.
   ```cpp
   template <typename T>
   T add(T a, T b) { return a + b; }
   ```

### **New Features in C++17**:
1. **Structured Bindings**:
   Simplifies access to tuple or struct values.
   ```cpp
   auto [a, b] = make_pair(1, 2);
   cout << a << ", " << b; // Output: 1, 2
   ```

2. **std::optional**:
   Represents optional values.
   ```cpp
   optional<int> value = 42;
   if (value) cout << *value; // Output: 42
   ```

3. **if constexpr**:
   Compile-time branching.
   ```cpp
   if constexpr (sizeof(int) == 4) {
       cout << "32-bit int";
   }
   ```

---

## **3. C++ Tokens**
Tokens are the smallest units in a C++ program. They include:
1. **Keywords**: Reserved words like `int`, `return`.
2. **Identifiers**: Variable, function names.
3. **Literals**: Constants like `5`, `'a'`, `"hello"`.
4. **Operators**: Symbols like `+`, `-`, `*`.
5. **Punctuation**: Symbols like `{}`, `;`.
6. **Comments**: `// Single-line` or `/* Multi-line */`.

---

## **4. Initialization**
Initialization in C++ can be done in several ways:
1. **Direct Initialization**:
   ```cpp
   int a(10);
   ```

2. **Copy Initialization**:
   ```cpp
   int b = 20;
   ```

3. **List Initialization (C++11)**:
   ```cpp
   int c{30};
   ```

4. **Default Initialization**:
   ```cpp
   int d; // Uninitialized
   ```

---

## **5. Static Members**

- **Static Data Members**:
  Shared across all objects of a class.
  ```cpp
  class Counter {
      static int count;
  public:
      static void increment() { count++; }
  };

  int Counter::count = 0; // Definition
  ```

- **Static Member Functions**:
  Can access only static members.
  ```cpp
  Counter::increment();
  ```

---

## **6. Constant Members**
- Declared with `const` to prevent modification.
- Must be initialized using a constructor initializer list.
  ```cpp
  class Circle {
      const double PI;
  public:
      Circle() : PI(3.14159) {}
  };
  ```

---

## **7. Expressions**

- **Arithmetic Expressions**: Combine operators and operands.
  ```cpp
  int result = (a + b) * c;
  ```

- **Relational Expressions**: Compare values.
  ```cpp
  bool isEqual = (a == b);
  ```

- **Logical Expressions**: Combine boolean values.
  ```cpp
  if (a > b && b < c) { ... }
  ```

- **Unary Expressions**: Use single operands.
  ```cpp
  int x = -a;
  ```

---

## **Example Code**
```cpp
#include <iostream>
#include <memory>
#include <optional>
#include <tuple>
using namespace std;

class Demo {
    static int counter;
    const int ID;
public:
    Demo(int id) : ID(id) {
        counter++;
    }
    static int getCounter() {
        return counter;
    }
};

int Demo::counter = 0;

int main() {
    Demo d1(101), d2(102);
    cout << "Static Counter: " << Demo::getCounter() << endl;

    auto [x, y] = make_pair(5, 10);
    cout << "Structured Binding: " << x << ", " << y << endl;

    optional<int> optValue = 42;
    if (optValue) {
        cout << "Optional Value: " << *optValue << endl;
    }

    auto lambdaSum = [](int a, int b) { return a + b; };
    cout << "Lambda Result: " << lambdaSum(10, 20) << endl;

    return 0;
}
```
---

# Operators, Conditional Statements, Looping Statements, and Arrays in C++

## **1. Operators**

### **Arithmetic Operators**
Used to perform basic mathematical operations.

| Operator | Description       | Example          |
|----------|-------------------|------------------|
| `+`      | Addition          | `a + b`          |
| `-`      | Subtraction       | `a - b`          |
| `*`      | Multiplication    | `a * b`          |
| `/`      | Division          | `a / b`          |
| `%`      | Modulus (remainder)| `a % b`         |

#### Example:
```cpp
int a = 10, b = 3;
cout << "Sum: " << a + b << endl;
cout << "Remainder: " << a % b << endl;
```

---

### **Relational Operators**
Used to compare two values.

| Operator | Description      | Example         |
|----------|------------------|-----------------|
| `==`     | Equal to         | `a == b`        |
| `!=`     | Not equal to     | `a != b`        |
| `<`      | Less than        | `a < b`         |
| `>`      | Greater than     | `a > b`         |
| `<=`     | Less than or equal to | `a <= b` |
| `>=`     | Greater than or equal to | `a >= b` |

#### Example:
```cpp
int a = 5, b = 10;
cout << (a < b); // Output: 1 (true)
```

---

### **Logical Operators**
Used for logical expressions.

| Operator | Description      | Example              |
|----------|------------------|----------------------|
| `&&`     | Logical AND      | `(a > 0 && b > 0)`   |
| `||`     | Logical OR       | `(a > 0 || b < 0)`   |
| `!`      | Logical NOT      | `!(a > b)`           |

#### Example:
```cpp
bool x = true, y = false;
cout << (x && y); // Output: 0 (false)
```

---

### **Unary Operators**
Operate on a single operand.

| Operator | Description         | Example          |
|----------|---------------------|------------------|
| `+`      | Unary plus          | `+a`             |
| `-`      | Unary minus         | `-a`             |
| `++`     | Increment           | `++a` or `a++`   |
| `--`     | Decrement           | `--a` or `a--`   |
| `!`      | Logical NOT         | `!a`             |

---

### **Ternary Operator**
Short form for an `if-else` statement.
```cpp
condition ? expression1 : expression2;
```

#### Example:
```cpp
int a = 5, b = 10;
int max = (a > b) ? a : b;
cout << "Max: " << max;
```

---

### **Assignment Operators**
Used to assign values to variables.

| Operator | Description   | Example    |
|----------|---------------|------------|
| `=`      | Assign        | `a = b`    |
| `+=`     | Add and assign| `a += b`   |
| `-=`     | Subtract and assign | `a -= b` |
| `*=`     | Multiply and assign | `a *= b` |
| `/=`     | Divide and assign | `a /= b` |
| `%=`     | Modulus and assign | `a %= b` |

---

## **2. Conditional Statements**

### **if-else Statement**
```cpp
int a = 10;
if (a > 5) {
    cout << "a is greater than 5";
} else {
    cout << "a is less than or equal to 5";
}
```

---

### **else-if Statement**
```cpp
int a = 10;
if (a < 5) {
    cout << "a is less than 5";
} else if (a == 10) {
    cout << "a is 10";
} else {
    cout << "a is greater than 5 but not 10";
}
```

---

### **switch Statement**
```cpp
int choice = 2;
switch (choice) {
    case 1: cout << "Choice is 1"; break;
    case 2: cout << "Choice is 2"; break;
    default: cout << "Invalid choice";
}
```

---

## **3. Looping Statements**

### **for Loop**
```cpp
for (int i = 0; i < 5; i++) {
    cout << i << " ";
}
```

---

### **while Loop**
```cpp
int i = 0;
while (i < 5) {
    cout << i << " ";
    i++;
}
```

---

### **do-while Loop**
```cpp
int i = 0;
do {
    cout << i << " ";
    i++;
} while (i < 5);
```

---

## **4. Jump Statements**

### **break**
Exits the loop prematurely.
```cpp
for (int i = 0; i < 5; i++) {
    if (i == 3) break;
    cout << i << " ";
}
```

### **continue**
Skips the current iteration.
```cpp
for (int i = 0; i < 5; i++) {
    if (i == 3) continue;
    cout << i << " ";
}
```

### **return**
Exits a function and optionally returns a value.
```cpp
int add(int a, int b) {
    return a + b;
}
```

---

## **5. Arrays**

### **Declaration and Initialization**
```cpp
int arr[5] = {1, 2, 3, 4, 5}; // Declaration and initialization
```

### **Accessing Array Elements**
```cpp
cout << arr[0]; // Access first element
```

---

### **1-D Array**
```cpp
int arr[5] = {1, 2, 3, 4, 5};
for (int i = 0; i < 5; i++) {
    cout << arr[i] << " ";
}
```

---

### **2-D Array**
```cpp
int arr[2][3] = {{1, 2, 3}, {4, 5, 6}};
for (int i = 0; i < 2; i++) {
    for (int j = 0; j < 3; j++) {
        cout << arr[i][j] << " ";
    }
    cout << endl;
}
```
---



# Functions in C++

## **1. Different Forms of Functions**
Functions in C++ can take various forms depending on their use case:

### **a. Non-Parameterized Functions**
Functions that do not take any arguments.
```cpp
void display() {
    cout << "Hello, World!";
}
```

### **b. Parameterized Functions**
Functions that accept parameters to perform operations.
```cpp
int add(int a, int b) {
    return a + b;
}
```

### **c. Functions with Default Arguments**
Provide default values to parameters.
```cpp
void greet(string name = "User") {
    cout << "Hello, " << name;
}
```

### **d. Overloaded Functions**
Multiple functions with the same name but different parameters.
```cpp
int multiply(int a, int b) {
    return a * b;
}
double multiply(double a, double b) {
    return a * b;
}
```

### **e. Recursive Functions**
A function that calls itself.
```cpp
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}
```

---

## **2. Function Prototyping**
A function prototype declares a function before defining it, ensuring type safety during calls.

### **Syntax**
```cpp
dataType functionName(parameters);
```

#### Example:
```cpp
int add(int, int); // Function prototype

int main() {
    cout << add(5, 10);
    return 0;
}

int add(int a, int b) { // Function definition
    return a + b;
}
```

---

## **3. Call by Reference**
Passing arguments by reference allows modification of the original values.

### **Syntax**
```cpp
void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}
```

#### Example:
```cpp
int x = 10, y = 20;
swap(x, y);
cout << "x: " << x << ", y: " << y; // Output: x: 20, y: 10
```

---

## **4. Inline Functions**
Inline functions are expanded at the point of invocation to reduce the overhead of function calls.

### **Syntax**
```cpp
inline int square(int x) {
    return x * x;
}
```

#### Example:
```cpp
cout << "Square of 5: " << square(5); // Output: Square of 5: 25
```

### **Advantages**
- Reduces function call overhead.
- Improves performance for small functions.

### **Disadvantages**
- Increases binary size for large functions.

---

## **5. Math Library Functions**
C++ provides a variety of mathematical functions in the `<cmath>` library.

### **Common Math Functions**

| Function       | Description                      | Example             |
|----------------|----------------------------------|---------------------|
| `sqrt(x)`      | Square root                     | `sqrt(25) -> 5`     |
| `pow(x, y)`    | Power (x^y)                    | `pow(2, 3) -> 8`    |
| `abs(x)`       | Absolute value                 | `abs(-10) -> 10`    |
| `ceil(x)`      | Rounds up to the nearest integer | `ceil(2.3) -> 3`    |
| `floor(x)`     | Rounds down to the nearest integer| `floor(2.7) -> 2`   |
| `sin(x)`       | Sine of angle (in radians)      | `sin(PI/2) -> 1`    |
| `cos(x)`       | Cosine of angle (in radians)    | `cos(0) -> 1`       |
| `log(x)`       | Natural logarithm              | `log(1) -> 0`       |

#### Example:
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    cout << "Square root of 25: " << sqrt(25) << endl;
    cout << "2^3: " << pow(2, 3) << endl;
    cout << "Absolute value of -10: " << abs(-10) << endl;
    return 0;
}
```

---

