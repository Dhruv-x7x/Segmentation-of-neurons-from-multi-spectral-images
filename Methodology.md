# Methodology
Size and noise level of brainbow image data prohibit a voxel level approach since the dataset size is so large and individual analysis of each voxel could lead to misinterpretation due to noise. Therefore the strategy used is "(i) a supervoxelization strategy, (ii) explicitly define graph representations on the set of supervoxels, and (iii) design the edge weights to capture the spatio-color relations"

## Hyperspectral imaging
This type of imaging uses bands of wavelenghts beyond the visible range to capture even more information about color. An example of a popular hyperspectral imaging method is **Nonnegative Matrix Factorization**.

### NMF or NNMF
Nonnegative Matrix Factorization is facotrizing a matrix **V** into two matrices, **W** and **H** (say), both of which have only non-negative elements. These matrices have reduced dimensions. 

$$
\mathbf{V_{m x n}} = \mathbf{W_{m x r} H_{r x n}}
$$

**r** can be much smaller than **m** or **n**. This is useful in many applications that don't have negative values such as images. Pixels only contain positive values. When we factorize, what we get is two smaller matrices that are easier to work with computationally. It's like taking a picture of a face and extracting features of the nose, mouth, etc.,

The problem, though, is not that simple. NMF is a **NP-Hard** problem. If we are given the matrices **W** and **H**, it's easy to verify if they are factors of **V**, but its really difficult to find them because there are so many possibilites. It is like how the RSA algorithm works. There is no way to find out the prime factors of an encryption key by factorizing it because the computer would have to try every possible number. There is no faster way to do it. It comes down to a minimization problem. 

$$
min(||V-WH||_F) &emsp; s.t. W,H>0
$$

We minimize the Frobenius Norm, which is the distance between **V** and **WH**. We can apply gradient techniques like gradient descent but this is a non-convex problem. It's convex in **W** or **H** but not both which means that gradient techniques will get stuck in local minima instead of going to the global minima. In other words, the computer will think it found the answer but it is not the correct one. 

But why is it convex in **W** or **H** but not both? To answer that we can consider the case when m = n = 1, the scalar case. 

$$
min(||v - wh||_F) = min(v^2 - 2vwh + w^2h^2)
$$

Let

$$\phi(x) = v^2 - 2vwh + w^2h^2$$

If we look at the gradient and hessian of $\phi(x)$ we can say that the hessian is not always positive semi-definite for all v, x, h $\ge0$. Why can we say this? By looking at the expression of the hessian it's clear that, even though v, w and h are positive, the expressions in the hessian matrix may lead to negative eigen values. Even a single negative eigen value means that the function is concave in that direction and we lose our non-convexity. 

$$
\nabla \phi_x (w, h) = 
\begin{pmatrix}
2hw^2 - 2vw \\
2h^2w - 2vh
\end{pmatrix}
$$

$$
\nabla^2 \phi_x (w, h) = 
\begin{pmatrix}
2w^2 & 4hw - 2v \\
4hw - 2v & 2h^2
\end{pmatrix}
$$

A positive semi-definite matrix is a symmetric matrix **M** such that, 

$$
x^TMx \ge 0
$$

Where **x** is any non-zero vector. This implies all eigen values of M are non-negative. Clearly, if the hessian is not always positive semi-definite we can not guarantee convexity.

Does this mean that the problem is unsolvable? In a way, yes but we can approximate the factors to a reasonable extent. That is, even if we can not find a global minima due to non-convexity, we are satisfied if we can get to a good local minima that is close to the global minima. Even this approximation is very useful in applications to hyperspectral imaging. One way to approximate is **Multiplicative Update**, which is a technique given by *Lee* and *Seung*. 
