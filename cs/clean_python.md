# Cleaner is better :snake:

- [Cleaner is better :snake:](#cleaner-is-better-snake)
  - [Pep8](#pep8)
    - [*Import order*, Imports should be grouped in the following order:](#import-order-imports-should-be-grouped-in-the-following-order)
    - [Formatter](#formatter)
      - [**Black**](#black)
    - [Linting](#linting)
      - [Why using linting ?](#why-using-linting-)
      - [**Pylint**](#pylint)
  - [`*args` \& `**kwargs`](#args--kwargs)
  - [logging](#logging)
    - [Basic configurations](#basic-configurations)
  - [Multiprocessing and multihreading](#multiprocessing-and-multihreading)
    - [Multiprocesing](#multiprocesing)
  - [Memory management in Python](#memory-management-in-python)



## Pep8
[Pep8](https://peps.python.org/pep-0008/) is the style guide for Python code. It provides guidelines to write readable code.

Here are a few tips to help write clean code.
### *Import order*, Imports should be grouped in the following order:
  - Standard library imports.
  - Related third party imports.
  - Local application/library specific imports.
  - 
### Formatter

> Code formatters make sure the codebase stays in a consistent style without any manual work. 
#### **Black**
Black can be considered as the de-facto formatter for Python projects. 

  - Install the latest version   
  `pip install black`
  - Run it on one or more files  
   `black {source_file_or_directory}`
    
### Linting

> Linting is performed while the source code is written and before it's compiled, i.e linting is a pre-build check also called **static code analysis**. 

#### Why using linting ?
Regularly checking code with linting ensures consistensy accross the codebase. It minimizes the probability of small errors. 
It checks for errors, enforces a conding standard and can make suggestion about how the code should be refactored.

#### **Pylint**
> Pylint analyses your code without running it. 

- Install  
`pip install pylint`

- Use  
`pylint {file_name}`

## `*args` & `**kwargs`
Both are arguments which allows a function to accept an arbitrary number of arguments.

- `args` : arguments (non keywords arguments)
pass iterable objects like list, tuple, set, etc. as arguments in the function call.
- `kwargs` : keyword arguments
pass dictionary type objects as arguments in the function call.

> When to use ? We use *args and **kwargs as an argument when we are unsure about the number of arguments to pass in the functions.


## logging
The `logging` module in Python provides a default logger that allows to get started without much configuration. 

:exclamation: by default `debug()`and `default()`do not get logged. 

### Basic configurations 

Use the method : `basicConfig(**`_`kwargs`_`)`
Basic __parameters__ : 
-   `level`: The root logger will be set to the specified severity level.
-   `filename`: This specifies the file.
-   `filemode`: If  `filename`  is given, the file is opened in this mode. The default is  `a`, which means append.
-   `format`: This is the format of the log message.

__Example__ : 
```python
import logging

logging.basicConfig(format='%(asctime)s - %(message)s', level=logging.INFO)
logging.info('Admin logged in')
```
output : 
```bash
2018-07-11 20:12:06,288 - Admin logged in
```

## Multiprocessing and multihreading
Multiprocessing and multithreading are two ways of achieving distributed computing.

**Multithreading**
> Multithreading is a CPU feature that allows two or more instructions thread to execute independantly while sharing the same process ressources. 

**Multiprocessing**
> Refers to the ability of a system to run multiple processors concurrently. 

### Multiprocesing
Multiprocessing can be implemented via the `multiprocessing` Python built-in library. 

- The `pool` method
It allows the user to define the number of workers and distribute all processes to available processors in a First-In-First-Out schefule. 

`pool` method is used to break a function into multiple small parts using `map` or `startmap` running the same function with different argument. 
 NB : whereas `process` method is used to run different functions. 

Example : 
```python
import multiprocessing as mp
 
def my_func(x):
  print(x**x)
 
def main():
  pool = mp.Pool(mp.cpu_count())
  result = pool.map(my_func, [5,9,8])
 
if __name__ == "__main__":
  main()
```

Output 
```python
3125
387420489
16777216
```

## Memory management in Python
[Source](https://stackabuse.com/basics-of-memory-management-in-python/)

Memory management is the process of efficiently allocating, de-allocating, and coordinating memory so that all the different processes run smoothly and can optimally access different system resources.   

In Python, the memory manager is responsible for these kinds of tasks by periodically running to clean up, allocate, and manage the memory. Unlike C, Java, and other programming languages, Python manages objects by using reference counting. This means that the memory manager keeps track of the number of references to each object in the program. When an **object's reference count drops to zero**, which means the object is no longer being used, the garbage collector (part of the memory manager) automatically frees the memory from that particular object.

> The garbage collector is a cyclic garbage collector, which means that it periodically checks for objects in the program that are no longer being used by the program. It then automatically frees up the memory used by those objects.