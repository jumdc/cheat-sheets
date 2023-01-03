# Multiprocessing and multihreading in Python 

Multiprocessing and multithreading are two ways of achieving distributed computing.

- [Multiprocessing and multihreading in Python](#multiprocessing-and-multihreading-in-python)
  - [Multiprocesing](#multiprocesing)
    - [The `pool` method](#the-pool-method)


**Multithreading**
> Multithreading is a CPU feature that allows two or more instructions thread to execute independantly while sharing the same process ressources. 

**Multiprocessing**
> Refers to the ability of a system to run multiple processors concurrently. 
>

## Multiprocesing
Multiprocessing can be implemented via the `multiprocessing` Python built-in library. 

### The `pool` method
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
