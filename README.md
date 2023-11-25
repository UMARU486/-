# thoughts about numpy exercises

#### Which are from <https://github.com/rougier/numpy-100>.

#### 5. How to get the documentation of the numpy add function from the command line? (★☆☆)

```python
%run `python -c "import numpy; numpy.info(numpy.add)"`
```

` 用到的时候直接把这行命令复制过去 `

#### 8. Reverse a vector (first element becomes last) (★☆☆)

```python
Z = np.arange(50)
Z = Z[::-1]
print(Z)
```

`Z[]中[]的含义是某种“选定”，这题展示的是一位的切片，实际上“选定”的条件可以更加复杂`


#### 12. Create a 3x3x3 array with random values (★☆☆)

```python
Z = np.random.random((3,3,3))
print(Z)
```
#### 13. Create a 10x10 array with random values and find the minimum and maximum values (★☆☆)
`hint: min, max`

```python
Z = np.random.random((10,10))
Zmin, Zmax = Z.min(), Z.max()
print(Zmin, Zmax)
```
#### 14. Create a random vector of size 30 and find the mean value (★☆☆)
`hint: mean`

```python
Z = np.random.random(30)
m = Z.mean()
print(m)
```
#### 15. Create a 2d array with 1 on the border and 0 inside (★☆☆)
`hint: array[1:-1, 1:-1]`

```python
Z = np.ones((10,10))
Z[1:-1,1:-1] = 0
print(Z)
```
#### 16. How to add a border (filled with 0's) around an existing array? (★☆☆)
`hint: np.pad`

```python
Z = np.ones((5,5))
Z = np.pad(Z, pad_width=1, mode='constant', constant_values=0)
print(Z)

# Using fancy indexing
Z[:, [0, -1]] = 0
Z[[0, -1], :] = 0
print(Z)
```
#### 17. What is the result of the following expression? (★☆☆)
```python
0 * np.nan
np.nan == np.nan
np.inf > np.nan
np.nan - np.nan
np.nan in set([np.nan])
0.3 == 3 * 0.1
```
`hint: NaN = not a number, inf = infinity`

```python
print(0 * np.nan)
print(np.nan == np.nan)
print(np.inf > np.nan)
print(np.nan - np.nan)
print(np.nan in set([np.nan]))
print(0.3 == 3 * 0.1)
```
#### 18. Create a 5x5 matrix with values 1,2,3,4 just below the diagonal (★☆☆)
`hint: np.diag`

```python
Z = np.diag(1+np.arange(4),k=-1)
print(Z)
```
#### 19. Create a 8x8 matrix and fill it with a checkerboard pattern (★☆☆)
`hint: array[::2]`

```python
Z = np.zeros((8,8),dtype=int)
Z[1::2,::2] = 1
Z[::2,1::2] = 1
print(Z)
```
#### 20. Consider a (6,7,8) shape array, what is the index (x,y,z) of the 100th element? (★☆☆)
`hint: np.unravel_index`

```python
print(np.unravel_index(99,(6,7,8)))
```
#### 21. Create a checkerboard 8x8 matrix using the tile function (★☆☆)
`hint: np.tile`

```python
Z = np.tile( np.array([[0,1],[1,0]]), (4,4))
print(Z)
```
#### 22. Normalize a 5x5 random matrix (★☆☆)
`hint: (x -mean)/std`

```python
Z = np.random.random((5,5))
Z = (Z - np.mean (Z)) / (np.std (Z))
print(Z)
```
#### 23. Create a custom dtype that describes a color as four unsigned bytes (RGBA) (★☆☆)
`hint: np.dtype`

```python
color = np.dtype([("r", np.ubyte),
                  ("g", np.ubyte),
                  ("b", np.ubyte),
                  ("a", np.ubyte)])
```
#### 24. Multiply a 5x3 matrix by a 3x2 matrix (real matrix product) (★☆☆)
`hint:`

```python
Z = np.dot(np.ones((5,3)), np.ones((3,2)))
print(Z)

# Alternative solution, in Python 3.5 and above
Z = np.ones((5,3)) @ np.ones((3,2))
print(Z)
```
#### 25. Given a 1D array, negate all elements which are between 3 and 8, in place. (★☆☆)
`hint: >, <`

```python
# Author: Evgeni Burovski

Z = np.arange(11)
Z[(3 < Z) & (Z < 8)] *= -1
print(Z)
```
#### 26. What is the output of the following script? (★☆☆)
```python
# Author: Jake VanderPlas

print(sum(range(5),-1))
from numpy import *
print(sum(range(5),-1))
```
`hint: np.sum`

```python
# Author: Jake VanderPlas

print(sum(range(5),-1))
from numpy import *
print(sum(range(5),-1))
```
#### 27. Consider an integer vector Z, which of these expressions are legal? (★☆☆)
```python
Z**Z
2 << Z >> 2
Z <- Z
1j*Z
Z/1/1
Z<Z>Z
```
`No hints provided...`

```python
Z**Z
2 << Z >> 2
Z <- Z
1j*Z
Z/1/1
Z<Z>Z
```
#### 28. What are the result of the following expressions? (★☆☆)
```python
np.array(0) / np.array(0)
np.array(0) // np.array(0)
np.array([np.nan]).astype(int).astype(float)
```
`No hints provided...`

```python
print(np.array(0) / np.array(0))
print(np.array(0) // np.array(0))
print(np.array([np.nan]).astype(int).astype(float))
```
#### 29. How to round away from zero a float array ? (★☆☆)
`hint: np.uniform, np.copysign, np.ceil, np.abs, np.where`

```python
# Author: Charles R Harris

Z = np.random.uniform(-10,+10,10)
print(np.copysign(np.ceil(np.abs(Z)), Z))

# More readable but less efficient
print(np.where(Z>0, np.ceil(Z), np.floor(Z)))
```
#### 30. How to find common values between two arrays? (★☆☆)
`hint: np.intersect1d`

```python
Z1 = np.random.randint(0,10,10)
Z2 = np.random.randint(0,10,10)
print(np.intersect1d(Z1,Z2))
```
#### 31. How to ignore all numpy warnings (not recommended)? (★☆☆)
`hint: np.seterr, np.errstate`

```python
# Suicide mode on
defaults = np.seterr(all="ignore")
Z = np.ones(1) / 0

# Back to sanity
_ = np.seterr(**defaults)

# Equivalently with a context manager
with np.errstate(all="ignore"):
    np.arange(3) / 0
```
#### 32. Is the following expressions true? (★☆☆)
```python
np.sqrt(-1) == np.emath.sqrt(-1)
```
`hint: imaginary number`

```python
np.sqrt(-1) == np.emath.sqrt(-1)
```
#### 33. How to get the dates of yesterday, today and tomorrow? (★☆☆)
`hint: np.datetime64, np.timedelta64`

```python
yesterday = np.datetime64('today') - np.timedelta64(1)
today     = np.datetime64('today')
tomorrow  = np.datetime64('today') + np.timedelta64(1)
```

