# The difference equation

We are going to solve equation {eq}`eq:Advection` numerically on discretized time and space. The discretizations are:

$$
	x_m &= m\Delta x, m=0,1,2,...,M \\
	t^n &= n\Delta t, n=0,1,2,...,N,
$$ (eq:Discretization)

where $\Delta t$ is the time step and $\Delta x$ is the grid resolution. The discrete time-space domain is commonly represented as the *t-x diagram* in {numref}`txDiagram`.

```{figure} ./txDiagramCropped.png
---
height: 600px
name: txDiagram
---
The discrete time-space domain represented as a t-x diagram. The numerical solution at time $t^n$ and position $x_m$ is $u_m^n$ and is represented in the diagram in the position ($x_m$,$t^n$).  
```

Using the 2nd order centered formula {eq}`eq:formulaCentred` to replace the exact derivatives in {eq}`eq:Advection`, we get:

$$
	\frac{u_{m}^{n+1} - u_{m}^{n-1}}{2\Delta t } + c \frac{u_{m+1}^{n} - u_{m-1}^{n}}{2\Delta x} = 0.
$$ (eq:diffEquation)

We call {eq}`eq:diffEquation` the *difference equation* resulting from the discretization of {eq}`eq:Advection` by the 2nd order centred formulas for the first derivative. Rearranging the terms of {eq}`eq:diffEquation` we obtain a time marching scheme:

$$
u_{m}^{n+1} = u_{m}^{n-1} - c\frac{\Delta t}{\Delta x}(u_{m+1}^{n}-u_{m-1}^{n}),
$$ (eq:Leapfrog)

known as the *leapfrog* scheme, which is a three-level scheme, because it employs information at time levels $n-1$, $n$ and $n+1$. Since the discretization of {eq}`eq:Advection` was done with 2nd order formulas, the scheme {eq}`eq:Leapfrog` is of 2nd order.
