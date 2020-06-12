# matrix multiply
> This is an nbdev tutorial notebook.


```python
%load_ext autoreload
%autoreload 2
```

    The autoreload extension is already loaded. To reload it, use:
      %reload_ext autoreload


This file will become your README and also the index of your documentation.

## Install

`pip install nbdev_tut`

## How to use

In this notebook we will multiply 2 matrices.

# Dot Product

First, lets familiarize ourselves with the dot product, which is an operation defined between 2 one-dimensional vectors of equal length

```python
vector_A = np.array([1,2,3])
print("Vector A is " + np.array2string(vector_A))
vector_B = np.array([3,0,5])
print("Vector B is " + np.array2string(vector_B))
vector_C = np.array([1,2,3, 4])
print("Vector C is " + np.array2string(vector_C))
```

    Vector A is [1 2 3]
    Vector B is [3 0 5]
    Vector C is [1 2 3 4]


For example, of the vectors above, only A·B and B ·A are defined, because C has a different dimension than the other 2

Now that have 2 vectors we know we can "multiply" using the dot product, we will look at how to do it. The dot product of 2 vectors is a **scalar** and is equal to **the sum of the scalar products of numbers in the same positions**.

So to calculate A·B, we would do A[0]\*B[0] + A[1]\*B[1] + A[2]\*B[2]

= 1 \* 3 + 2 \* 0 + 3 \* 5 

= 3 + 0 + 15

= 18

To get the dot product of 2 vectors, we can use dotp(). Let's check our answer!

```python
print(dotp(vector_A, vector_B))
```

    18


# Matrix Product

Now that we know what a dot product is, we can continue to define the matrix product

The matrix product JxK is defined for matrices J and K where the number of **columns** in J is equal to the number of **rows** in K

```python
matrix_J = np.array([[2, 4],[3, 5],[0,1]])
print("J is \n" + np.array2string(matrix_J))
matrix_K = np.array([[1, 3, 2, 5], [0, 4, 0 , 1]])
print("\n K is \n" + np.array2string(matrix_K))
```

    J is 
    [[2 4]
     [3 5]
     [0 1]]
    
     K is 
    [[1 3 2 5]
     [0 4 0 1]]


For example, above, JxK is defined because J has **2 columns** and K has **2 rows.** However, KxJ is not defined because K has **4 columns** while J has **3 rows**.

So how do we calculate the matrix product? Well if M is a matrix with *x* rows and *y* columns, and N is a matrix with *y* rows and *z* columns the product will be a matrix with *x* rows and *z* columns. In the product matrix MxN, the value in the *ith* row and the *jth* column will be the dot product of the *ith* row of M and the *jth* column.

So back to our example JxK, J has 3 rows and K has 4 columns, so JxK will be a matrix with 3 rows and 4 columns.

We won't go through the full calculation because it is lengthy even for small matrices, but we can look at just 1 value in the product matrix. (1,1) in JxK (that is, the value of JxK in the 1st row and the 1st column) will be the dot product of the 1st row of J and the 1st column of K.

JxK[0,0] = J[0,:] · K[:,0]

= [2,4] · [1,0]

= 2\*1 + 4\*0

= 2 + 0

= 2

To get the matrix product we can use mmult(), so let's look at JxK

```python
print(mmult(matrix_J, matrix_K))
```

    [[ 2. 22.  4. 14.]
     [ 3. 29.  6. 20.]
     [ 0.  4.  0.  1.]]


As we can see, like we expected, the resultant matrix has 3 rows and 4 columns, and the element in the 1st column and 1st row is 2
