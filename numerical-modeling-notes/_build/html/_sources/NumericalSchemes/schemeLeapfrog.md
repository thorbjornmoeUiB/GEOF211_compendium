# The Leapfrog Scheme

The leapfrog scheme is obtained by replacing the time and space derivatives of {eq}`eqAdvection` by centred finite differences. After discretizing time and space in $N$ time steps $t^n$ and $M$ grid positions $x_m$, and substiting the partial derivatives with the finite difference approximations, we obtain:

$$
   u_{m}^{n+1} = u_{m}^{n-1} - c\frac{\Delta t}{\Delta x}(u_{m+1}^{n}-u_{m-1}^{n})
$$ (eqLeapfrog)

where $u_{m}^{n} = u(x=x_m,t=t^n)$ is the function value at grid position $m$ and at time step $n$. The increments $\Delta t$ and $\Delta x$ are the time step and grid step (resolution), respectively.

## Consistency, stability and convergence
The scheme truncation error is $O(\Delta t^2,\Delta x^2)$. It is conditionally stable with the stability condition being $c\frac{\Delta t}{\Delta x} \leq 1$. 

```{figure} ../Leapfrog_Domain.png
---
height: 600px
name: leapfrogDomain
---
Domain of influence of the Leapfrog scheme. 
```

The characteristic lines in {numref}`leapfrogDomain` have a slope of $1/c$, while the sides of the triangle have a slope of $\Delta t/\Delta x$. 

The solution $u(c_m,t^n)$ is constant along the characteristic that passes through the point. 
For the scheme to provide meaningful results, the characteristic line must be inside the domain of the scheme, which is only possible if the slope of the characteristic is larger than the slope of the triangle sides. This is true if:

$$
	\frac{1}{c} \ge \frac{\Delta t}{\Delta x} \Leftrightarrow c\frac{\Delta t}{\Delta x} \leq 1.
$$

## Application: propagation of top hat function

To test the scheme, we are going to apply it to the propagation of the top hat signal. The spatial domain is defined as $x \in \left[0,100\right]$, with periodic boundary conditions. 

```{figure} ../Leapfrog_SolutionCFL050.png
---
height: 600px
name: leapfrogSolution
---
The Leapfrog scheme solution after 50 time steps for a *top hat* initial condition, with $\Delta t=2$ and $\Delta x=1$.
```
Observation of the solution {numref}`leapfrogSolution` allows to conclude that:
1. The numerical solution follows the true solution reasonably well, but
2. There are wave-like disturbances in the numerical solution.

The wave-like disturbances appear because the Leapfrog scheme is **dispersive**. This occurs whenever the phase speed of wave-like solutions to the *difference equation* depend on their wavelength, as is the case with the Leapfrog scheme. 


