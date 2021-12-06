---
layout: page
title: A Different Perspective of Diagonalization
date: 2020-11-02
description: An (atttempt at an) intuitive approach to similar matrix decomposition.
comments: true
importance: 5
category: linear algebra
---
$$\newcommand{\Re}{\operatorname{Re}}$$
$$\newcommand{\Im}{\operatorname{Im}}$$

Diagonalization
=

While this works for any dimension matrix, this will be of the example where the matrix is a $$2\times2$$.

Suppose $$A$$ is a $$2\times2$$ matrix with eigenvectors $$v_1,v_2$$ associated with eigenvalues $$\lambda_1,\lambda_2$$ respectively. By definition of an eigenvector, this would imply that for any scalars $$c_1,c_2$$.

\begin{equation}
A(c_1v_1+c_2v_2)=\lambda_1c_1v_1+\lambda_2c_2v_2
\end{equation}

Say we apply $$A$$ a second time...

$$\begin{gather}
A(A(c_1v_1+c_2v_2))=A((\lambda_1c_1)v_1+(\lambda_2c_2)v_2)\\
A^2(c_1v_1+c_2v_2)=\lambda_1(\lambda_1c_1)v_1+\lambda_2(\lambda_2c_2)v_2\\
A^2(c_1v_1+c_2v_2)=\lambda_1^2c_1v_1+\lambda_2^2c_2v_2\\
\end{gather}$$

We could easily repeat this as many times as we wanted. So it is also the case that

\begin{equation}\label{exp}
A^n(c_1v_1+c_2v_2)=\lambda_1^nc_1v_1+\lambda_2^nc_2v_2
\end{equation}

Since for those vectors, the transformation $$A$$ is just simple scaling, in the situation where we have to repeatedly apply $$A$$ to some vector $$w$$, it would clearly be preferable to get that vector in terms of $$v_1$$ and $$v_2$$. This seems like a job for change of basis...

So let us define the eigenbasis
$$\begin{equation}
B=\{v_1,v_2\}
\end{equation} $$

The change of basis matrix $$P_{\varepsilon\leftarrow B}$$ (where $$\varepsilon$$ is the standard basis $$\varepsilon=\{e_1,e_2\}$$), then is 

$$\begin{equation}
P_{\varepsilon\leftarrow B}=\begin{bmatrix}v_1&v_2\end{bmatrix}
\end{equation}$$

By extension,

\begin{equation}\label{inv change}
P_{B\leftarrow\varepsilon}=(P _{\varepsilon\leftarrow B})^{-1}
\end{equation}

So now suppose that

\begin{equation}
w=c_1v_1+c_2v_2 
\end{equation}

This tells us that the coordinate vector of $$w$$ with respect to the eigenbasis $$B$$, $$(w)_B$$, is

$$\begin{equation}
(w)_B=\begin{bmatrix}c_1\\c_2\end{bmatrix}
\end{equation}$$

We know from \eqref{exp} then that

\begin{equation}
A^nw=A^n(c_1v_1+c_2v_2)=\lambda_1^nc_1v_1+\lambda_2^nc_2v_2
\end{equation}

So

$$\begin{equation}
(A^nw)_B=\begin{bmatrix}\lambda_1^nc_1\\\lambda_2^nc_2\end{bmatrix}
\end{equation}$$

But that's also the transformation

$$\begin{equation}
(A^nw)_B=\begin{bmatrix}\lambda_1^nc_1\\\lambda_2^nc_2\end{bmatrix}=\begin{bmatrix}\lambda_1^n&0\\0&\lambda_2^n\end{bmatrix}\begin{bmatrix}c_1\\c_2\end{bmatrix}
\end{equation}$$

If we call the diagonal matrix
$$D=\begin{bmatrix}\lambda_1&0\\0&\lambda_2\end{bmatrix}$$, then we get

\begin{equation}
(A^nw)_B=D^n(w)_B
\end{equation}

We're so close now. Next, we change back to the standard basis by applying $$P_{\varepsilon\leftarrow B}$$ to both sides,

\begin{equation}
P_{\varepsilon\leftarrow B}(A^nw) _{B} = P _{\varepsilon\leftarrow B}D^n
(w) _B
\end{equation}

\begin{equation}\label{close}
A^nw=P _{\varepsilon\leftarrow B}D^n(w) _B
\end{equation}

To get things entirely in terms of the standard basis, we start by rewriting 

\begin{equation}
(w) _B=P _{B\leftarrow\varepsilon}(w) _{\varepsilon}
\end{equation}

Using \eqref{inv change} and the fact that $$(w) _{\varepsilon}=w$$ (by definition of the standard basis), 

\begin{equation}
(w) _B=(P _{\varepsilon\leftarrow B})^{-1}w
\end{equation}

we substitute into \eqref{close}

\begin{equation}
A^nw=P _{\varepsilon\leftarrow B}D^n(P _{\varepsilon\leftarrow B})^{-1}w
\end{equation}

If we just denote $$P _{\varepsilon\leftarrow B}$$ as $$P$$, then we finally get

\begin{equation}
A^nw=PD^nP^{-1}w
\end{equation}

General Decomposition
=

In general, if we know how a matrix $$A$$ acts on a basis, then we may either construct or decompose it via a $$PDP^{-1}$$ decomposition.

Complex Eigendecomposition of Real Matrices
-

Let's take the example of a real $$2\times2$$ with complex eigenvalues. Suppose $$A$$ is such a matrix with a complex eigenvalue $$a+bi$$, where $$b\neq0$$, associated with a complex eigenvector $$v$$.

\begin{equation} \label{complex eigenvector}
Av=(a+bi)v
\end{equation}

Let's get a bit more specific by decomposing $$v$$ into its real and imaginary parts.

$$\begin{gather}
A(\Re(v)+i\Im(v))=(a+bi)(\Re(v)+i\Im(v))\\
A\Re(v)+i(A\Im(v))=(a\Re(v)-b\Im(v))+i(b\Re(v)+a\Im(v))
\end{gather}$$

We can equate the real and imaginary parts on both sides,

\begin{equation}
A\Re(v)=a\Re(v)-b\Im(v),\quad A\Im(v)=b\Re(v)+a\Im(v)
\end{equation}

Now we know that $$\{\Re(v),\Im(v)\}$$ is a basis of $$\mathbb{R}^2$$ because if they were linearly dependent, then $$\Im(v)=k\Re(v)$$. That would change \eqref{complex eigenvector} into

\begin{equation}
A(1+ki)\Re(v)=(a+bi)(1+ki)\Re(v)
\end{equation}

Dividing by the common $$1+ki$$,

\begin{equation}
A\Re(v)=(a+bi)\Re(v)
\end{equation}

This implies a contradiction since the imaginary part of the left side is zero due to $$A$$ being real, but the right is not if $$b\neq0$$. Therefore, 

$$\begin{equation} \label{complex basis}
B=\{\Re(v),\Im(v)\} \text{ is a basis for } \mathbb{R}^2
\end{equation}$$

It then follows that 

$$\begin{equation}
P=\begin{bmatrix}\Re(v)&\Im(v)\end{bmatrix}
\end{equation}$$

is invertible.

Well, we know how $$A$$ acts on the basis $$B$$ \eqref{complex basis}:

$$\begin{equation}
(A\Re(v))_B=\begin{bmatrix}a\\-b\end{bmatrix},\quad (A\Im(v))_B=\begin{bmatrix}b\\a\end{bmatrix}
\end{equation}$$

So our matrix $$D$$ is then,

$$\begin{equation}
D=\begin{bmatrix}a&b\\-b&a\end{bmatrix}
\end{equation}$$

So our eigendecomposition of $$A$$ is

$$\begin{equation}
A=\begin{bmatrix}\Re(v)&\Im(v)\end{bmatrix}\begin{bmatrix}a&b\\-b&a\end{bmatrix}\begin{bmatrix}\Re(v)&\Im(v)\end{bmatrix}^{-1}
\end{equation}$$

It can be verified that the eigenvalues of this particular $$D$$ are $$\lambda=a\pm bi$$.
