# Shapes in numpy

<img width="200" alt="numpy logo" src="https://user-images.githubusercontent.com/62952163/205486279-904df348-9fc8-4d39-97e2-b7152e235e75.png">

## Table of contents
1. [Shape](#shape)
2. [Reshape](#reshape)

## Shapes <a name='shape'></a>


## Reshape <a name='reshape'></a>
Gives a new shape to an array without changing its data : `numpy.reshape(a, newshape, order='C')`.

There exists a similar function : `numpy.ndarray.reshape(shape, order='C')`

### Example 
- __`numpy.ndarray.reshape` and `newshape=-1`__ 

❗ This method on ndarray allows the elements of the shape parameter to be passed in as separate arguments (`a.reshape(10, 11)` is equivalent to `a.reshape((10, 11))`).

If an integer, then the result will be a 1-D array of that length. 
One shape dimension can be -1.
In this case, the value is inferred from the length of the array and remaining dimensions.

```python
import numpy as np

original = np.random.rand(5, 4, 3)
reshaped = original.reshape(original.shape[0], -1)  

# reconstitute the initial shape
new_original = reshaped.reshape(
    reshaped.shape[0], reshaped.shape[1] // original.shape[2], original.shape[2]
    )
```
