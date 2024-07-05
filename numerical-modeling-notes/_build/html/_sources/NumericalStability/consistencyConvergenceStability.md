# Consistency, convergence and stability

First, let's clarify the expression "converge to the solution of the exact equation", by defining the error of the numerical approximation.

(definition:errorApproximation)=
:::{admonition} Definition
:class: important
The error of the numerical approximation $u_m^n$, $\epsilon_m^n$, is

$$
\epsilon_m^n = u_m^n - u(m\Delta x,n\Delta t),
$$

where $u_m^n$ is the numerical solution and $u(m\Delta x,n\Delta t)$ is the exact solution at $(x_m,t^n)$.
:::

We can now define more precisely the concepts of boundedness and convergence. Let us consider the following questions:
* What happens to $\epsilon_m^n$ as $\Delta t, \Delta x \to 0$ for fixed $n\Delta t$?
* What happens to $\epsilon_m^n$ as $n\to\infty$ for fixed $\Delta t$ and $\Delta x$?

The first questions leads us to the concepts of *consistency* and *convergence*. 

(definition:consistency)=
:::{admonition} Definition
:class: important
A difference equation is consistent when it approaches the corresponding PDE as $\Delta t, \Delta x \to 0$.
:::

The truncation error of the leapfrog scheme applied to the linear advection equation is:

$$
Tr = \frac{\Delta t^2}{3!}\frac{\partial^3 u}{\partial t^3} + c\frac{\Delta x^2}{3!}\frac{\partial^3 u}{\partial x^3} + \dots
$$

or $Tr = O(\Delta t^2)+O(\Delta x^2)$, which clearly converges to zero as $\Delta t, \Delta x \to 0$. Thus the leapfrog discretization of the linear advection equation is consistent.

(important:truncationErrorsConsistency)=
:::{important}
Numerical schemes with truncation errors with terms $O(\Delta t^p)$ or $O(\Delta x^p)$ are consistent if $p \ge 1$.
:::

But this is not a guarantee that we will obtain meaningful results. We must also demand that, over an interval $n\Delta t$, $\epsilon_m^n \to 0$ as $\Delta t, \Delta x \to 0$. 

(definition:convergence)=
:::{admonition} Definition
:class: important
A numerical solution is convergent if, for fixed $n\Delta t$, $\epsilon_m^n \to 0$ as $\Delta t, \Delta x \to 0$.

If a numerical scheme gives convergent solutions for any initial condition, the numerical scheme is said to be convergent.
:::

The second question leads us to the concept of *numerical stability*. If $u(m\Delta x,n\Delta t)$ is bounded, we can expect $\epsilon_m^n$ to remain bounded if $u_m^n$ remains bounded. 

```{margin} Boundedness
A function $f$ defined on a set $X$ with real or complex values is called bounded if there exists a real number $M$ such that

$$
|f(x)|\le M
$$

for all $x$ in $X$.
```

This leads us to the definition of stability of a numerical scheme:

(definition:stability)=
:::{admonition} Definition
:class: important
A finite-difference scheme is **stable** if its solutions remain uniformly bounded functions of the initial condition, for all sufficiently small $\Delta t$.
:::

```{margin} Uniformly bounded functions
A uniformly bounded family of functions is a family of bounded functions that can all be bounded by the same constant. 
```

(important:stabilityPDE)=
:::{important}
The concept of stability is not directly related to the underlying PDE.
:::

Convergence is not so easily demonstrated as it involves the exact equation, whose solution may not be known. Stability is easier to demonstrate as it involved the finite-difference scheme. Luckily, we can infer convergence from stability in certain cases using the Lax Equivalence Theorem.

(theorem:laxEquivalence)=
:::{admonition} Lax Equivalence Theorem
:class: important
Given a properly posed, linear initial value problem and a finite-difference approximation that satisfies the consistency condition, stability is the necessary and sufficient condition for convergence.
:::

Therefore, if we can show consistency and stability, the convergence of the finite-difference scheme is guaranteed by the Lax Equivalence Theorem.


