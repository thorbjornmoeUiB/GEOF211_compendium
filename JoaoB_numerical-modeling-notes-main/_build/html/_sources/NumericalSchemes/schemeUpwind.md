# The Upwind Scheme

Observation of {numref}`leapfrogDomain` indicates that, for $c>0$, information travels from left to right so the grid nodes to the right of $x_m$ do not provide useful information to the solution at $x_m$. In this case, a numerical scheme may be constructed that only uses the information **upwind** from $x_m$:

$$
   u_{m}^{n+1} = u_{m}^{n} - c\frac{\Delta t}{\Delta x}(u_{m}^{n}-u_{m-1}^{n})
$$ (eqUpwind)

where $u_{m}^{n}$, $\Delta t$ and $\Delta x$ have the same meaning as for the Leapfrog scheme.

The upwind scheme {eq}`eqUpwind` depends on the sign of $c$. For $c<0$, the scheme becomes

$$
   u_{m}^{n+1} = u_{m}^{n} - c\frac{\Delta t}{\Delta x}(u_{m+1}^{n}-u_{m}^{n})
$$ (eqDownwind)

as information is travelling from right to left.

## Consistency, stability and convergence
The scheme's truncation error is $O(\Delta t,\Delta x)$, as it used a forward formula for the time derivative and a backward formula for the space derivative (forward if $c<0$) 

### Stability

The stability of the Upwind scheme can be determined by the von Neumann method. Assuming a solution of the form $u_m^n=B^n e^{i\lambda m\Delta x}$ and substituting in the difference equation {eq}`eqUpwind` we obtain

$$
	u_m^{n+1}=\left[1-\sigma \left(1-e^{-i\lambda \Delta x}\right)\right]u_m^n
$$

where $\sigma=c\frac{\Delta t}{\Delta x}$. Therefore, the amplification factor is $G=\left[1-\sigma \left(1-e^{-i\lambda \Delta x}\right)\right]$, whose norm is $|G|^2=1-2\sigma\left(1-\cos\lambda\Delta x\right)\left(1-\sigma\right)$. Depending on the value of sigma we can have the following cases:
1. $\sigma=0 \lor \sigma=1$: $|G|^2=1$ and the scheme is **neutral** (stable).
2. $\sigma<0 \lor \sigma>1$: $|G|^2>1$ and the scheme is **amplifying** (unstable).
3. $\sigma>0 \land \sigma<1$: $|G|^2=1$ and the scheme is **damping** (stable).

Note that case 2 encompasses two distinct situations. If $\sigma < 0$, the upwind formulation {eq}`eqUpwind` is being used in the situation where $c<0$ or {eq}`eqDownwind` is being used in the situation where $c>0$. When this occurs the scheme is referred to as **Downwind**. If $\sigma > 1$, the cause of instability is the same as for the Leapfrog scheme. 

```{figure} ../Upwind_Domain.png
---
height: 600px
name: upwindDomain
---
Domain of influence of the Upwind scheme. 
```
The scheme is conditionally stable with the stability condition being $c\frac{\Delta t}{\Delta x} \leq 1$. Its domain of dependence is shown in {numref}`upwindDomain`. The previously stable solution with $c<0$ is now an unstable solution, because the scheme is working as a *Downwind* scheme.

## Application: propagation of top hat function

To test the scheme, we are going to apply it to the propagation of the top hat signal, as we did with the Leapfrog scheme. 

```{figure} ../Upwind_Solution.png
---
height: 400px
name: upwindSolution
---
The Upwind scheme solution after 50 time steps for a *top hat* initial condition, with $\Delta t=2$ and $\Delta x=1$.
```
Unlike the Leapfrog scheme, the solution with the Upwind scheme ({numref}`upwindSolution`) doesn't show dispersive behaviour. Instead, it presents an excessive smoothing of the abrupt transitions of the initial condition, an effect that is also undesirable. This is characteristic of the Upwind scheme, which is said to be **dissipative** (in excess).

The source of the dissipation can be identified in the Upwind scheme as an artificial term that is added to the linear advection equation {eq}`eqAdvection`

\begin{equation}
	\frac{\partial u}{\partial t} + c  \frac{\partial u}{\partial x} = \color{magenta}\left(1-\sigma \right) c\frac{\Delta x}{2}\frac{\partial^2 u}{\partial x^2} + O(\Delta t^2,\Delta x^2)
\end{equation}

The term has a diffusive character due to the 2nd derivative and therefore it is known as *artifical diffusion* or *numerical diffusion*. 

The coefficient $\left(1-\sigma \right) c\frac{\Delta x}{2}$ of the 2nd derivative is an analog of the physical diffusivity $D$ and can be regarded as an *artificial diffusivity*. 
The impact of the artificial diffusion will depend on its magnitude relative to the physical advection which is the process that is being modeled. This relative importance is measured by a *grid* Peclet number

$$
	\tilde{P}_e=\frac{cL}{c \Delta x (1-\sigma )/2}
$$ 

which should be $\gg1$ so as to minimize the effects of numerical diffusion.


