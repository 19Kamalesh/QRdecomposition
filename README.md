# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)

Initialization:Initialize matrix $Q$ of the same shape as $A$ with zeros.Initialize a square matrix $R$ of size $n \times n$ (where $n$ is the number of columns in $A$) with zeros.Iterative Orthogonalization:For each column $j$ in matrix $A$:Set vector $v$ equal to the $j$-th column of $A$.Orthogonalize $v$ against all previous columns $Q[:, i]$ (for $i < j$):Calculate the projection coefficient $R[i, j] = \text{dot\_product}(Q[:, i], A[:, j])$.Subtract the projection from $v$: $v = v - R[i, j] \times Q[:, i]$.Normalize the resulting vector $v$:Calculate the norm $R[j, j] = ||v||$.Store the orthonormal vector in the $Q$ matrix: $Q[:, j] = v / R[j, j]$.Result:The matrix $Q$ contains the orthonormal basis.The matrix $R$ contains the coefficients, forming an upper triangular structure.

## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: KAMALESHWARAN S
RegisterNumber: 212225040165
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np

def qr_decomposition(A):
    A = np.array(A, dtype=float)
    m, n = A.shape
    Q = np.zeros((m, n))
    R = np.zeros((n, n))
    
    for j in range(n):
        v = A[:, j]
        for i in range(j): 
            R[i, j] = np.dot(Q[:, i], A[:, j])
            v = v - R[i, j] * Q[:, i]
            
        R[j, j] = np.linalg.norm(v)
        Q[:, j] = v / R[j, j]
        
    return Q, R 

A = np.array(eval(input()))
Q, R = qr_decomposition(A)
print("The Q Matrix is\n", Q)
print("The R Matrix is\n", R)




```

## Output
```
<img width="1333" height="919" alt="image" src="https://github.com/user-attachments/assets/130d5c4d-ad0d-4d29-a638-010eb6d46f00" />

```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
