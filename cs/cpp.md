# C++

- [C++](#c)
  - [Introduction](#introduction)
  - [Hello World](#hello-world)
    - [Compile the program](#compile-the-program)
      - [g++](#g)
      - [makefile](#makefile)
  - [Generalites](#generalites)
    - [standard input \& ouput](#standard-input--ouput)
    - [loops](#loops)
    - [if statement](#if-statement)
    - [Pointers](#pointers)
    - [1d array](#1d-array)
    - [n-d array](#n-d-array)
      - [arguments' function by values or reference ?](#arguments-function-by-values-or-reference-)

## Introduction

C with classes, it's an enhanced version of `C` created by B. Stroustrup. 
The two main reasons of its sucess : 
- direct mapping of hardware features
- zero-overhead abstractions (high-level abstractions)


## Hello World

- In the file `hello.cpp`: 
```cpp
 #include <iostream>
using namespace std;

int main() {
  std::cout << "Hello World!"; // std : standard output stram
  return 0; // rmsut return an int, 0 means executed without any problem
} 
```

### Compile the program 

#### g++

The compiler name is **g++**.
During execution, the program interacts directly with the os without any virtual machines. 

```bash
g++ -o ./helloworld ./hello.cpp
```

The compiltation creates an executable file, `helloworld` which containe machine code. 

- Execute it : 
```bash
./helloworld
```

#### makefile
`make` is a tool, a shortcut for compilation/execution. 

- The `makefile` : 
```makefile
helloworld: hello.cpp
  g++ -o helloworld hello.cpp
```
In the same directory call : 
```bash
make
```
Make checks the update for us. 


## Generalites

### standard input & ouput 
- standard input (reads from consol): `std::cin`
- standard ouput (writes to console) : `std::cout`
- standard error : `std::cerr`

```cpp
std::cin >> i; // the double arrow follows the direction of the flow i.e from the console TO the variable
std::cout << i << std::end1; // std::end1 puts '\n' at the end and flushes the stream
```


### loops  

```cpp
for (statement 1; statement 2; statement 3) {
  // code block to be executed
}
// example 
for (int i = 0, i < 3 ; i ++){
  // block to be executed
}
```


### if statement

```cpp
if (condition) {
  // block of code to be executed if the condition is true
}
else
{
  // block to be executed if the condition is false
}
```

### Pointers

> Pointers  
> A pointer is a special type of variable that contains a memory address rather than a data value. A pointer is a special type of variable that contains a memory address rather than a data value

We usually say that a pointer "points" to the location it is storing (the "pointee").

```cpp
int *ptr; // Declare integer pointer.
ptr = new int; // Allocate some memory for the integer.
*ptr = 5; // Dereference to initialize the pointee.
*ptr = *ptr + 1; // We are dereferencing ptr in order
                 // to add one to the value stored
                 // at the ptr address.
```

NB : do not forget to initialize the "pointee". 

### 1d array

> An array is a series of elements of the same type placed in contiguous memory locations that can be individually referenced by adding an index to a unique identifier.


```cpp
type name [elements];
```

```cpp
int foo [5];
int foo [5] = { 16, 2, 77, 40, 12071 };
```


### n-d array
```cpp
// This is not allowed!
double MyFunction (double matrix[][], int rows, int columns) {
  ...
}
// This is fine!
double MyFunction (double **matrix, int rows, int columns) {
  return matrix[0][0];
}
```



#### arguments' function by values or reference ?


# Random information
### extension
- .hpp : Header file written in the C++ programming language; may contain data types, constants, and variables; can be inserted into a .CPP source code file using the #include directive; used for storing reusable components of code.
