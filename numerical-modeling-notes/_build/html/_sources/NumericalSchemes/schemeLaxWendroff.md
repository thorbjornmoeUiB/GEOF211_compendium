# The Lax-Wendroff Scheme

The Lax-Wendroff scheme can be derived in several ways. We shall derive it from a *multi-step* perspective. The idea is to compute $u_m^{n+1}$ using not the time derivative at $t=n\Delta t$, but that at the *half-step* $t=n\Delta t + \Delta t/2=(n+1/2)\Delta t$

$$
	u_m^{n+1}=u_m^n+\Delta t\left(-c\frac{\partial u}{\partial x}\mid_{m,n+1/2}\right)
$$

To obtain the spatial derivative at the half-time step, we must have the function values at $t^{n+1/2}$, or

$$
	u_m^{n+1/2}=u_m^n+\frac{\Delta t}{2}\left(-c\frac{\partial u}{\partial x}\mid_{m,n}\right).
$$

The Lax-Wendroff method thus involves two steps:

 **1:** First, compute $\frac{\partial u}{\partial x}\mid_{m,n+1/2}$ using central differences, that involve the *mid-points* $m+1/2$ and $m-1/2$:

$$
	u_{m-1/2}^{n+1/2}=\frac{1}{2}(u_m^n+u_{m-1}^n)-c\frac{\Delta t}{2\Delta x}(u_m^n-u_{m-1}^n)
$$
$$
	u_{m+1/2}^{n+1/2}=\frac{1}{2}(u_{m+1}^n+u_{m}^n)-c\frac{\Delta t}{2\Delta x}(u_{m+1}^n-u_{m}^n)
$$
 **2:** Compute $u_m^{n+1}$ using the spatial derivative at $n+1/2$:

$$
	u_{m}^{n+1}=u_m^n-c\frac{\Delta t}{2\Delta x}(u_{m+1/2}^{n+1/2}-u_{m-1/2}^{n+1/2})
$$

## Consistency, stability and convergence

The scheme is 2nd order in time and space. To determine its stability we can express the scheme as:

$$
	u_m^{n+1} = \alpha u_{m-1}^n + \beta u_m^n + \gamma u_{m+1}^n
$$

with 

\begin{align}
	\alpha &= \frac{\sigma}{2}(\sigma + 1),\\
	\beta &= 1- \sigma^2, \\
	\gamma &= \frac{\sigma}{2}(\sigma - 1)
\end{align}

Assuming a solution of the type $B^n e^{i\lambda m \Delta x}$, the amplification factor is 

$$
	G=(1+\sigma^2(\cos \lambda \Delta x - 1)) - i\sigma \sin \lambda \Delta x
$$

which has a norm 

$$
	|G|^2 = 1-\sigma^2(1-\sigma^2)(1 - \cos \lambda \Delta x)^2.
$$

For the method to be stable, the condition is $|G|^2 \leq 1$ which provides the following stability condition

$$
	1-\sigma^2 \ge 0 \Leftrightarrow \sigma = \frac{c\Delta t}{\Delta x} \leq 1.
$$

which is the well-known CFL condition.

## Application: propagation of top hat function

As before, we apply the Lax-Wendroff scheme to the top hat initial condition.

```{figure} ../LaxWendroff_Solution.png
---
height: 400px
name: laxWendroffSolution
---
The Lax-Wendroff scheme solution after 50 time steps for a *top hat* initial condition, with $\Delta t=2$ and $\Delta x=1$.
```
The Lex-Wendroff scheme ({numref}`laxWendroffSolution`) avoids the excessive numerical diffusion of the Upwind scheme, but oscillations are still visible at the sharp transitions of the top hat function. These oscillations are known as the Gibbs phenomenon.
