---
layout: page
title: The Alpha Method (Generalized Exponential Response Formula)
date: 2021-01-04 
description: Easy particular solutions to nonhomoegenous constant coefficient linear differential equations with simple exponential/trigonometric forcing functions.
comments: true
importance: 1
category: differential equations
---
$$\newcommand{\a}{\alpha }$$
$$\newcommand{\b}{\beta  }$$
$$\newcommand{\ealph}{e^{\a t}}$$
# Basic Overview: The Alpha Method

\
The results of the Alpha Method are so simple, I feel it's necessary I give them outright before the derivation.


If $$p(\a )\neq0$$, then 

\begin{equation} \label{problem}
    p(D)y=B\ealph 
\end{equation}

has the particular solution

$$\begin{equation} 
    y_p=\frac{B\ealph }{p(\a )}
\end{equation}$$

Otherwise, there exists a positive integer $$m$$ such that \eqref{problem} has the particular solution 

$$\begin{equation}
    y_p=\frac{Bt^m\ealph }{p^{(m)}(\a )}
\end{equation}$$

Additionally, a particular solution to

$$\begin{equation}
    p(D)y=B\ealph \cos(\b  t)+C\ealph \sin(\b  t)
\end{equation}$$

Is given by 

$$\begin{equation}
    y_p=B\operatorname{Re}(z_p)+C\operatorname{Im}(z_p)
\end{equation}$$

where $$z_p$$ is obtained by using the alpha method on

$$\begin{equation}
    p(D)z=e^{(\a+i\b)t}
\end{equation}$$

For a more formal and thorough examination of this problem and method, take a look at [this](https://www.overleaf.com/read/xtxskmmnjphy){:target="_blank"}.

# The problem
Here we look for particular solutions differential equations such as

$$\begin{align*}
    &y''+y=10e^{2t} & y''+4y'+4y=e^{-3t}\\
    &y'''-5y'+6y=e^{3t} & y^{(9)}-2y'+y=e^t&\\
    &y''+4y'+3y=\sin(3t) & y''+2y'+26y=e^{-3t}\cos(2t)\\
    &y^{(4)}+4y=\cos(2t) & y''+2y'+2y=e^{-t}\sin(t)
\end{align*}$$

However, these all really have the same form, \eqref{problem}.

Where $$D$$ is the differential operator such that

\begin{equation}
    Dy=y'
\end{equation}

and $$p(x)$$ is the characteristic polynomial.

Take the example, $$y''-5y'+6y$$, which has a characteristic polynomial $$p(x)=x^2-5x+6$$. We could rewrite this with the $$D$$ operator as

\begin{equation}
    D^2y-5Dy+6y
\end{equation}

We can factor out a $$y$$ from the right (not the left because the $$D$$ is not commutative), 
and indeed that is still the characteristic polynomial with $$D$$ instead of $$x$$.

\begin{equation}
    (D^2-5D+6)y=p(D)y
\end{equation}

Not all of these equations look like they have an exponential on the other side, though. Using Euler's Identity, they might as well be. To take two examples of the cases where it's not so obvious,

$$\begin{gather}
    \sin(3t)=\operatorname{Im}(e^{3it})\\
    e^{-3t}\cos(2t)=\operatorname{Re}(e^{(-3+2i)t})
\end{gather}$$

# Real $$\a $$  

  


#### $$\quad p(\a )\neq 0$$

So let's examine the general problem

$$\begin{equation}
    ay''+by'+cy=B\ealph 
\end{equation}$$

First, notice the characteristic polynomial is $$p(x)=ax^2+bx+c$$. Now if we had to guess the form of the solution, a good guess would be some constant times $$\ealph $$ since adding that with its derivatives would give us some scalar multiple of $$\ealph $$.

$$\begin{gather}
    y_p=A\ealph \\
    y_p'=A(\a )\ealph \\
    y_p''=A(\a ^2)\ealph 
\end{gather}$$

When we plug into the differential equation,
$$\begin{gather}
    aA(\a ^2)\ealph +bA(\a )\ealph +cA\ealph =B\ealph \\
    A(a\a ^2+b\a +c)\ealph =B\ealph \\
\end{gather}$$

\begin{equation} \label{Ap(a)=B}
    Ap(\a )\ealph =B\ealph 
\end{equation}

Therefore, as long as $$p(\a )\neq 0$$, a particular solution is

\begin{equation}
    A=\frac{B}{p(\a )}
\end{equation}

So we get as a result, if $$p(\a )\neq 0$$, then \eqref{problem} has the particular solution 

$$\begin{equation} \label{alpha0}
    y_p=\frac{B\ealph }{p(\a )}
\end{equation}$$

This is not restricted to second-order equations. I recommend trying to prove that it works for $$n$$-th order equations as well.

Take the example

$$\begin{equation}
    y''+y=10e^{-2t}
\end{equation}$$

Here $$\a =-2$$, $$B=10$$, and $$p(x)=x^2+1$$. So $$p(\a )=5$$ and $$\frac{B}{p(\a )}=2$$. Therefore,

\begin{equation}
    y_p=2e^{-2t}
\end{equation}

And it can be verified that this is indeed a solution :sunglasses:

However, if $$p(\a )=0$$ then we're in a bit of a pickle, because \eqref{Ap(a)=B} is only true if $$B=0$$. So our solution cannot be of the form $$y_p=A\ealph $$. In other words, $$A\ealph $$ is in the kernel of $$p(D)$$.



#### $$\quad p(\a )=0, \; p'(\a )\neq 0$$

When you run into trouble with linear differential equations, sometimes the solution is multiplying by the independent variable. And indeed, this is *nearly* the solution.

Let's go back to

$$\begin{equation}
    ay''+by'+cy=B\ealph 
\end{equation}$$

But this time, we suppose $$p(\a )=0$$. Now if you plug in $$y_p=A\ealph $$ you'll get zero. If we suppose $$y_p=At\ealph $$, then we get

$$\begin{gather}
    y_p=At\ealph \\
    y_p'=A(\a  t+1)\ealph \\
    y_p''=A(\a ^2t+2\a )\ealph 
\end{gather}$$

Substituting in,

$$\begin{gather}
    aA(\a ^2t+2\a )\ealph +bA(\a  t+1)\ealph +cAt\ealph =B\ealph \\
    A\ealph ((a\a ^2+b\a +c)t+(2a\a +b))=B\ealph \\
    A\ealph (p(\a )t+p'(\a ))=B\ealph 
\end{gather}$$

How curious... This is no coincidence. It has everything to do with (one of the) exponential shift theorems and how that interacts with Taylor series. The linked writeup at the top of this page goes more in depth on exactly how that works.

Since we assumed that $$p(\a )=0$$, we're left with 

$$\begin{equation}
    A\ealph p'(\a )=B\ealph 
\end{equation}$$

Then as long as $$p'(\a )\neq0$$,

$$\begin{equation}
    A=\frac{B}{p'(\a )}
\end{equation}$$

and 

$$\begin{equation} \label{Bt/pprime}
    y_p=\frac{Bt\ealph }{p'(\a )}
\end{equation}$$

Once again, this is not limited to second-order equations. In general,

If $$p(\a )=0$$ but $$p'(\a )\neq 0$$, then \eqref{problem} has the particular solution \eqref{Bt/pprime}.



#### $$\quad p(\a )=p'(\a )=\ldots=p^{(m-1)}(\a )=0,\;\; p^{(m)}(\a )\neq 0$$

You may notice a pattern when comparing $$\frac{Bt\ealph }{p'(\a )}$$ and $$\frac{B\ealph }{p(\a )}$$. You may be hoping that if $$p(\a )=p'(\a )=0$$ but $$p''(\a )\neq 0$$ then

$$\begin{equation}
    y_p=\frac{Bt^2\ealph }{p''(\a )}
\end{equation}$$

Well I have good news :smirk: It's absolutely true. If $$p^{(k)}(\a )$$ keeps equaling zero, you simply have to multiply by $$t$$ and divide by the next derivative instead until it works. Let's take an example:

Find the general solution for

$$\begin{equation}
    y^{(4)}+4y'''+6y''+4y'+y=72e^{-t}
\end{equation}$$

Now they teach you in school to find the homogeneous solution first, and then get the particular solution. But this is why the Alpha Method is so ballin'. By starting with the particular solution, the alpha method sometimes does the rest of the problem for you.

This particular equation is not very difficult. The homogeneous solution can be obtained by inspection if you're familiar with Pascal's Triangle. But let's pretend we aren't.

Now I'm going to go ahead and bust out the Alpha Method \eqref{alpha0} by calculating 

$$\begin{equation}
    y_p=^?\frac{72e^{-t}}{p(-1)}
\end{equation}$$

But when I calculate $$p(-1)$$ I 'mysteriously' get zero... Then that tells me that $$-1$$ is a root of the characteristic polynomial :eyes: So one of my homogeneous solutions is $$y_1=e^{-t}$$. So we didn't completely waste our time.

Alright, so let's go with the derivative and multiply by $$t$$.

$$\begin{equation}
    y_p=^?\frac{72te^{-t}}{p'(-1)}
\end{equation}$$

But oh no $$p'(-1)=0$$ too :weary:

Alas, not all is lost. We at least get a second homogeneous solution $$y_2=te^{-t}$$.

Let's cut to the chase. If we continue trying to use the Alpha Method,

$$\begin{gather}
    p''(-1)=0&\implies &y_3=t^2e^{-t}\\
    p'''(-1)=0&\implies &y_4=t^3e^{-t}
\end{gather}$$

And hey wait a minute, we now have four homogeneous solutions to a fourth-order differential equation. That mean's we have our entire homogeneous solution. :eyes:

$$\begin{equation}
    y_h=c_1e^{-t}+c_2te^{-t}+c_3t^2e^{-t}+c_4t^3e^{-t}
\end{equation}$$

Now lucky for us (though not at all unexpected) $$p^{(4)}(-1)\neq 0$$. That means our solution will be of the form

$$\begin{equation}
    y_p=\frac{72t^4e^{-t}}{p^{(4)}(-1)}
\end{equation}$$

$$\begin{equation}
    y_p=3t^4e^{-t}
\end{equation}$$

Therefore, our general solution is 

$$\begin{equation}
    y_g=3t^4e^{-t}+(c_1+c_2t+c_3t^2+c_4t^3)e^{-t}
\end{equation}$$






# Complex $$\a $$

In my opinion, this is the other area where the Alpha Method shines. Finding particular solutions to problems like this

$$\begin{equation} \label{complex example}
    y^{(4)}+2y'''+3y''+2y'+2y=e^{-t}(6\cos(t)+2\sin(t))
\end{equation}$$

using conventional methods is just atrocious. However, with the Alpha Method, a particular solution is just a bit of algebra.

When dealing with a problem where the forcing function is a $$\sin$$ or $$\cos$$, it can ironically make things simpler to 'complexify' the problem. That is to turn problems like

$$\begin{equation}
    p(D)y=B\ealph \cos(\b  t)+C\ealph \sin(\b t)
\end{equation}$$

into this

$$\begin{equation} \label{complex problem}
    p(D)y=B\operatorname{Re}(e^{(\a +i\b ) t})+C\operatorname{Im}(e^{(\a +i\b ) t})
\end{equation}$$

using Euler's formula.

Okay maybe that doesn't look much easier, but I promise it is. This way you're just doing the regular Alpha Method as we did before. You just have to do some extra complex arithmetic in addition. But I promise it's better than undetermined coefficients almost all of the time.

This is the general idea:

Say you have something like this,

$$\begin{equation} \label{complex case}
    p(D)y=B\ealph \cos(\b  t)+C\ealph \sin(\b  t)
\end{equation}$$

Instead of solving that problem, we solve this one:

$$\begin{equation}
    p(D)z=e^{(\a +i\b ) t}
\end{equation}$$

using the Alpha Method. Nothing is different here, the solution is either

$$\begin{equation}
    z_p=\frac{e^{(\a +i\b ) t}}{p(\a +\b  i)}
\end{equation}$$

or there exists some positive integer $$m$$ such that

$$\begin{equation}
    z_p=\frac{t^me^{(\a +i\b ) t}}{p^{(m)}(\a +\b  i)}
\end{equation}$$

Now the solution to \eqref{complex case} will be

$$\begin{equation}
    y_p=B\operatorname{Re}(z_p)+C\operatorname{Im}(z_p)
\end{equation}$$

And... that's it. Now we can solve \eqref{complex example}.

First, we turn it into

$$\begin{equation}
z^{(4)}+2z'''+3z''+2z'+2z=e^{(-1+i) t}
\end{equation}$$

Now we compute $$p(-1+i)$$ which happens to be... zero. Rats. Well at least we know two homogeneous solutions now to our original differential equation $$y_1=e^{-t}\cos(t)$$ and $$y_2=e^{-t}\sin(t)$$.

$$p'(-1+i)=4+2i$$ however, so we're back in business.

$$\begin{equation}
    z_p=\frac{te^{(-1+i)t}}{4+2i}
\end{equation}$$

This is not particularly helpful, however, since we have a complex number in the denominator. To remedy this, we multiply the numerator and denominator by the conjugate.

$$\begin{equation}
    z_p=\frac{te^{(-1+i)t}}{4+2i}=
\frac{te^{(-1+i)t}(4-2i)}{4^2+2^2}
\end{equation}$$

$$\begin{equation}
    z_p=
\frac{te^{(-1+i)t}(2-i)}{10}
\end{equation}$$

While it may not look like it, this numerator has a product of binomials. Because $$e^{it}=\cos(t)+i\sin(t)$$, we have

$$\begin{equation}
    (\cos(t)+i\sin(t))(2-i)=(2\cos(t)+\sin(t))+i(2\sin(t)-\cos(t))
\end{equation}$$

$$\begin{equation}
    z_p=\frac{1}{10}te^{-t}(2\cos(t)+\sin(t))+i\frac{1}{10}te^{-t}(2\sin(t)-\cos(t))
\end{equation}$$

Now because we have $$6$$ on the $$\cos$$ and $$2$$ on the $$\sin$$ term, \eqref{complex problem} asks us for  

$$\begin{equation}
    y_p=6\operatorname{Re}(z_p)+2\operatorname{Im}(z_p)
\end{equation}$$

$$\begin{equation}
    y_p=te^{-t}(\cos(t)+\sin(t))
\end{equation}$$

And that's it. Yeah, I agree this is the best method.
