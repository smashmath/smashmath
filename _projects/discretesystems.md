---
layout: distill
title: Systems of Linear Difference Equations
date: 2021-12-14
description: Like systems of DEs, but discrete 👀
comments: true
importance: 3
category: works in progress
authors:  
  - name: Grant Fisher
    url: ""
    affiliations:
      name: None
toc:
  - name: Intro
    subsections:
      - name: Solution Behavior
  - name: The Best Solution
  - name: Solution Comparison (2x2)
    subsections:
      - name: Nondefective Repeated
      - name: Rank 1
      - name: Defective
      - name: Complex
      - name: Zero Trace
      - name: Singular
      - name: Distinct
---

# Intro

In differential equations students learn about the system

$$\textbf{x}'(t)=A\textbf{x}(t)$$

But here we will discuss the discrete system

$$\textbf{x}(t+1)=A\textbf{x}(t)$$

Where instead of a continuous function, we get a discrete set of points

$$\textbf{x}(0),\textbf{x}(1),\ldots,\textbf{x}(t),\ldots$$

## Solution Behavior

With systems of DEs, its the sign of the eigenvalues which tells you the behavior. Negative is asymptotically stable (going to zero), positive is unstable, and zero is statically stable.

However, in these discrete systems, it's the *magnitude*. To understand why, we need to know what our solutions even look like!

With systems of DEs, the basic example is

$$x'(t)=ax(t)$$

Which has the solution $$x(t)=ce^{at}$$. Therefore, its the sign of $$a$$ which determines the behavior. However, with the discrete system

$$x(t+1)=ax(t)$$

the solutions are of the form $$\textbf{x}(t)=ca^t$$. So we still get the behavior of asymptotically stable (going to zero), unstable, and types of static stability, but it's not about the sign. I encourage you to try and think about what it could be before reading on! It's an interesting thought, in my opinion.

Repeatedly multiplying a number $$a$$ to some nonzero initial number $$c$$ gets big when $$|
a
| > 1$$, goes to zero when $$|a|<1$$, and has a consistent magnitude when $$|a|=1$$.

But the similarities don't stop there. The solutions are still generally obtained by finding eigenvectors and eigenvalues, just like with DE systems. But instead of having solutions of the form $$\textbf{x}(t)=ce^{\lambda t}\textbf{v}$$, they are of the form $$\textbf{x}(t)=c\lambda^t\textbf{v}$$.

That said, one type of behavior which does not occur for systems of DE's is if $$a=0$$. Solutions of this type start constant, and then immediately disappear after finitely many iterations. For this reason, it is convenient to explicitly  define the function $$0^x$$ in the following way

$$\begin{equation}
0^x=\begin{cases}1,&x=0\\0,&x\neq0\end{cases}
\end{equation}$$

Now, I am not saying that $$0^0=1$$ always. It is indeed an indeterminate form. However, for our purposes, everything is simply cleaner if we take that as fact. Notice that we make the same assumption when we choose to write $$e^x$$ as $$e^x=\sum_{n=0}^\infty\frac{x^t}{n!}$$ rather than $$e^x=1+\sum_{n=1}^\infty\frac{x^t}{n!}$$.

I know which one I prefer. :unamused:

Either way, the most interesting similarity, in my opinion, is the analog for the matrix exponential.

# The Best Solution

In the system

$$\textbf{x}'(t)=A\textbf{x}(t)$$

the best general solution, though not always the most ideal to find, is

$$\textbf{x}(t)=e^{At}\textbf{x}(0)$$

Similarly, for the system

$$\textbf{x}(t+1)=A\textbf{x}(t)$$

the best general solution is

$$\textbf{x}(t)=A^t\textbf{x}_0$$

Now this is the coolest part, in my opinion.

There are formulas for $$A^t$$ which look nearly *identical* to the formulas for [Matrix Exponentials](../2x2ezmatrixexp/){:target="_blank"} that I found. I will compare them here, but first! I would like to let you in on how I found them. I used the method described in [that matrix exponential post](../2x2ezmatrixexp/#another-approach). Basically, solve

$$
\begin{pmatrix}
x(t+1)\\y(t+1)
\end{pmatrix}=
\begin{pmatrix}
0&-\det(A)\\1&\operatorname{tr}(A)
\end{pmatrix}
\begin{pmatrix}
x(t)\\y(t)
\end{pmatrix}\quad
\textbf{x}(0)=
\begin{pmatrix}
1\\0
\end{pmatrix}
$$

Then $$A^n=x(t)I+y(t)A$$ (for 2x2s!).

# Solution Comparison (2x2)

$$\begin{array}{cccccccc}
\textbf{x}'(t)&=&A\textbf{x}(t)&\implies&\textbf{x}(t)&=&e^{At}\textbf{x}(0)\\
\textbf{x}(t+1)&=&A\textbf{x}(t)&\implies&\textbf{x}(t)&=&A^t\textbf{x}_0
\end{array}$$

The following two are quite simple, and we actually used them to find the matrix exponential formula.

## Nondefective Repeated

This occurs when $$A=kI$$.

$$\begin{array}{ccc}
e^{kIt}&=&e^{kt}I\\
(kI)^t&=&k^tI
\end{array}$$

## Rank 1

If $$A$$ is any square matrix of rank one that also has a nonzero trace.

$$\begin{array}{ccccc}
e^{At}&=&\frac{e^{\operatorname{tr}(A)t}A-(A-\operatorname{tr}(A)I)}{\operatorname{tr}(A)}&=&I+\frac{e^{\operatorname{tr}(A)t}-1}{\operatorname{tr}(A)}A\\
A^t&=&\frac{\operatorname{tr}(A)^tA-0^t(A-\operatorname{tr}(A)I)}{\operatorname{tr}(A)}&=&0^tI+\frac{\operatorname{tr}(A)^t-0^t}{\operatorname{tr}(A)}A
\end{array}$$

As you can see, defining $$0^t$$ as we did makes things very convenient, and allows us to take advantage of the underlying similarities between the two system types.

## Defective

If $$A$$ is any $$2\times2$$ matrix with a defective eigenvalue $$k\neq0$$,

$$\begin{array}{ccc}
e^{At}&=&e^{kt}\bigg(I+t\big(A-kI\big)\bigg)\\
A^t&=&k^t\bigg(I+\frac{t}{k}\big(A-kI\big)\bigg)
\end{array}$$

If $$k=0$$, then the solution is kind of... horrifying.

$$\begin{array}{ccc}
e^{At}&=&I+tA\\
A^t&=&0^tI+0^{t-1}A
\end{array}$$

But looking at it, it does *actually* work. At $$t=0$$ it's $$I$$, and at $$t=1$$ it's $$A$$, and then its zero ever after. Which is indeed what happens with this kind of matrix (nilpotent). I'm not writing $$0^t(I+0^{-1}A)$$, though. This is clearly not a case where we can use regular exponent rules.

## Complex

If $$A\in\mathbb{R}^{2\times2}$$ has complex eigenvalues $$a\pm bi=re^{\pm i\theta}$$, then

$$\begin{align*}
e^{At}=&e^{at}\bigg(\cos(bt)I+\frac{\sin(bt)}{b}\big(A-aI\big)\bigg)\\
A^t=&r^t\bigg(\cos(\theta t)I+\frac{\sin(\theta t)}{b}\big(A-aI\big)\bigg)
\end{align*}$$

## Distinct

If $$A$$ has two distinct eigenvalues $$\lambda_1,\lambda_2$$, then

$$\begin{align*}
e^{At}=&\frac{e^{\lambda_2t}(A-\lambda_1I)-e^{\lambda_1t}(A-\lambda_2I)}{\lambda_2-\lambda_1}\\
A^t=&\frac{\lambda_2^t(A-\lambda_1I)-\lambda_1^t(A-\lambda_2I)}{\lambda_2-\lambda_1}
\end{align*}$$
