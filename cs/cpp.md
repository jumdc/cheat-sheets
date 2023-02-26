# C++

- [C++](#c)
  - [Introduction](#introduction)
  - [Hello World](#hello-world)
    - [Compile the program](#compile-the-program)
      - [g++](#g)
      - [makefile](#makefile)
  - [Generalites](#generalites)
      - [standard input \& ouput](#standard-input--ouput)
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

#### standard input & ouput 
- standard input (reads from consol): `std::cin`
- standard ouput (writes to console) : `std::cout`
- standard error : `std::cerr`

```cpp
std::cin >> i; // the double arrow follows the direction of the flow i.e from the console TO the variable
std::cout << i << std::end1; // std::end1 puts '\n' at the end and flushes the stream
```

#### arguments' function by values or reference ?
