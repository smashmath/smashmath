---
layout: page
title: Exact Equations Intuitively(?)
date: 2021-09-09 0
description: i hope
comments: true
importance: 5
category: differential equations
---

We seek to find the solution to the differential equation

$$\begin{equation}
M(x,y)+N(x,y)\frac{dy}{dx}=0
\end{equation}$$

We are hoping that there exists some function $$f(x,y)$$ such that

$$\begin{equation}
\frac{d}{dx}f(x,y)=M(x,y)+N(x,y)\frac{dy}{dx}
\end{equation}$$

Using the multivariable definition of the chain rule to calculate $$\frac{d}{dx}f(x,y)$$,

$$\begin{equation}
\frac{d}{dx}f(x,y)=f_x(x,y)+f_y(x,y)\frac{dy}{dx}
\end{equation}$$

By matching up terms, we see

$$\begin{equation}
M(x,y)=f_x(x,y),\quad N(x,y)=f_y(x,y)
\end{equation}$$

We can use a *very* bodacious result of multivariable calculus that

$$\begin{equation}
f_{xy}(x,y)=f_{yx}(x,y)\implies M_y=N_x
\end{equation}$$

Therefore, if that is so the equation is exact and we may find $$f$$!

We have two options now: We can start by integrating $$M$$ with respect to $$x$$, or $$N$$ with respect to $$y$$. We choose whichever integral looks easier, but we'll assume for now that we are choosing $$M$$.

$$\begin{equation}
f(x,y)=\int M(x,y)\,dx+h(y)
\end{equation}$$

If this is to be truly the $$f$$ we want, then its partial derivative with respect to $$y$$ has to be $$N$$ as we defined above. So we set $$f_y=N$$

$$\begin{equation}
N(x,y)=\frac{\partial}{\partial y}\left(\int M(x,y)\,dx\right)+h'(y)
\end{equation}$$

Now we can solve for $$h'(y)$$ and integrate it to get the correct $$h(y)$$ and then we have our answer $$f(x,y)$$.

We could have instead integrated $$N$$ with respect to $$y$$ to get an $$h(x)$$ and instead find that $$h$$ through the equation

$$\begin{equation}
M(x,y)=\frac{\partial}{\partial x}\left(\int N(x,y)\,dy\right)+h'(x)
\end{equation}$$

In summary,

1. Integrate $$M$$ with respect to $$x$$ and get a function of integration $$h(y)$$
2. Partially differentiate with respect to $$y$$ and set it equal to $$N$$
3. Solve for $$h'(y)$$ and integrate
4. Profit

or

1. Integrate $$N$$ with respect to $$y$$ and get a function of integration $$h(x)$$
2. Partially differentiate with respect to $$x$$ and set it equal to $$M$$
3. Solve for $$h'(x)$$ and integrate
4. Profit

Integrating Factors
-

If $$M_y\neq N_x$$, then it is not exact. But we can make it so (most of the time)! 

As a quick sidenote, if there is a common factor to both $$M$$ and $$N$$, it's possible that that common factor can make it impossible to find an integrating factor using the methods that will be described. Even if the common factor is a simple $$x$$ or $$y$$.

First we suppose there is an integrating factor which is a function of $$x$$, $$\mu(x)$$ giving us

$$\begin{equation}
\mu(x)M(x,y)+\mu(x)N(x,y)\frac{dy}{dx}=0
\end{equation}$$

We set the partials equal,

$$\begin{equation}
\frac{\partial}{\partial y}
\left(\mu(x)M\right)=
\frac{\partial}{\partial x}
\left(\mu(x)N\right)
\end{equation}$$

$$\begin{equation}
\mu(x)M_y=
\mu'(x)N+\mu(x)N_x
\end{equation}$$

Solving for $$\mu'$$,

$$\begin{equation}
\mu'(x)=\frac{M_y-N_x}{N}\mu(x)
\end{equation}$$

So if $$\frac{M_y-N_x}{N}$$ is a function of only $$x$$, then this is an easy first-order equation we can solve to find $$\mu$$. Then we just execute the process detailed in the previous section.

If $$\frac{M_y-N_x}{N}$$ is not a function of only $$x$$, then we instead seek an integrating factor $$\mu(y)$$. Repeating the process above,

$$\begin{equation}
\mu(y)M(x,y)+\mu(y)N(x,y)\frac{dy}{dx}=0
\end{equation}$$

$$\begin{equation}
\mu'(y)M+\mu(y)M_y=
\mu(y)N_x
\end{equation}$$

$$\begin{equation}
\mu'(y)=\frac{N_x-M_y}{M}\mu(y)
\end{equation}$$

If $$\frac{N_x-M_y}{M}$$ is a function only $$y$$, then we can again solve for $$\mu$$ and execute the steps in the first section. If neither of those work... maybe try something else...

The equations for integrating factors in summary,

$$\begin{align}
\mu'(x)&=\frac{M_y-N_x}{N}\mu(x)\\
\mu'(y)&=\frac{N_x-M_y}{M}\mu(y)
\end{align}$$
