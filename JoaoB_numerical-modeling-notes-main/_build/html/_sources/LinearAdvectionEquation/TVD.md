# Total Variation Diminishing Schemes

## TVD (Total Variation Diminishing) Schemes

TVD (Total Variation Diminishing) schemes are a class of numerical methods used for solving partial differential equations (PDEs) when strong gradients, shocks or discontinuities are present in the solution. The ability to preserve strong gradients in the numerical solution is especially important in the context of frontal advection. 

Higher-order methods, such as the leapfrog scheme (LINK!), are capable of retaining strong gradients in the solution but are prone to spurious oscillations or under/overshoots in the solution that create new (unphysical) extrema. The upwind scheme (LINK!) does not create new extrema (is monotone), but it is only first-order accurate and diffusive, which causes strong gradients to be smeared out. 

Godunov's theorem (REF) states that any linear monotone scheme can be at most first order accurate, so we cannot find a higher-order linear scheme that is also monotone. This implies that we must forego monotonicity if we want to preserve strong gradients in the numerical solution, when considering linear schemes. On the other hand, if we allow some degree of nonlinearity, we may have both monotonicity and the preservation of strong gradients. 

TVD schemes provide this, because they allow for monotonic nonlinear schemes, whenever there are artificial extrema being introduced in the numerical solution. Otherwise, the scheme remains higher order. 

Adaptive schemes such as these are based on the concept of total variation of the solution, which measures the amount of variation in the numerical solution over a given interval. The total variation should be conserved in order to prevent spurious oscillations or overshoots that can occur with higher order methods.

## TVD Scheme Theory

TVD schemes achieve conservation of total variation by using a limiter function to restrict the amount of numerical diffusion introduced by the scheme. The limiter function is designed to detect the presence of discontinuities or shocks in the solution and to reduce the amount of diffusion introduced in these regions. By reducing the amount of numerical diffusion, TVD schemes are able to preserve sharp gradients and discontinuities in the solution while maintaining stability.

Let us consider a 1-d spatial grid $x_m=m\Delta x$ and time steps $t^n=n\Delta t$. The total variation of the numerical solution $u_m$ at time step $n$ is:

$$
TV=\sum_{m}|u_{m+1}^n - u_m^n|
$$

A scheme is said to be TVD (total variation diminishing) if:

$$
TV^{n+1} \leq TV^n.
$$

Let's assume a scheme that can be expressed as:

$$
u_m^{n+1}=u_m^n-a_{m-\frac{1}{2}}(u_{m}^n - u_{m-1}^n) + b_{m+\frac{1}{2}}(u_{m+1}^n - u_{m}^n)
$$

If we write REF at $m+1$ and subtract, we obtain a marching expression for the variation at $m$:

$$
|u_{m+1}^{n+1}-u_m^{n+1}| \leq |(1-a_{m+\frac{1}{2}}-b_{m+\frac{1}{2}})(u_{m+1}^n - u_{m}^n)| + |b_{m+\frac{3}{2}}(u_{m+2}^n - u_{m+1}^n)|+|a_{m-\frac{1}{2}}(u_{m}^n - u_{m-1}^n)|
$$

Taking the summation of REF!!, and assuming periodic boundaries to shift the indices in the second and third terms, we obtain

$$
\sum_{m}|u_{m+1}^{n+1}-u_m^{n+1}| \leq \sum_{m}|(1-a_{m+\frac{1}{2}}-b_{m+\frac{1}{2}})(u_{m+1}^n - u_{m}^n)| + \sum_{m}|b_{m+\frac{1}{2}}(u_{m+1}^n - u_{m}^n)|+\sum_{m}|a_{m+\frac{1}{2}}(u_{m+1}^n - u_{m}^n)|
$$

If $a_{m+\frac{1}{2}}$ and $b_{m+\frac{1}{2}}$ fullfill the following conditions

1. $a_{m+\frac{1}{2}} \ge 0$
2. $b_{m+\frac{1}{2}} \ge 0$
3. $a_{m+\frac{1}{2}} + b_{m+\frac{1}{2}} \leq 1$

we can write REF!!! as

$$
\sum_{m}|u_{m+1}^{n+1}-u_m^{n+1}| \leq \sum_{m}(1-a_{m+\frac{1}{2}}-b_{m+\frac{1}{2}})|(u_{m+1}^n - u_{m}^n)| + \sum_{m}b_{m+\frac{1}{2}}|(u_{m+1}^n - u_{m}^n)|+\sum_{m}a_{m+\frac{1}{2}}|(u_{m+1}^n - u_{m}^n)|\leq\sum_{m}|(u_{m+1}^n - u_{m}^n)|
$$

which is the TVD condition (REF). Therefore, this scheme will be TVD if those three conditions are verified.

## TVD Scheme example

One example of a TVD scheme is the Total Variation Diminishing Upwind Scheme (TVDUS) applied to the linear advection equation.

The TVDUS scheme can be expressed mathematically as:

$$
u_m^{n+1} = u_m^{n} - \frac{\Delta t}{\Delta x}(f_{m+\frac{1}{2}}-f_{m-\frac{1}{2}})
$$

where $u_m^{n+1}$ is the value of the solution at grid point $m$ and time $n+1$, $u_m^n$ is the value of the solution at grid point $m$ and time $n$, $f_{m+\frac{1}{2}}$ is the numerical flux at the interface between grid points $m$ and $m+1$, and $f_{m-\frac{1}{2}}$ is the numerical flux at the interface between grid points $m$ and $m-1$. The fluxes $f_{m+\frac{1}{2}}$ and $f_{m-\frac{1}{2}}$ are modified by the weighting function $/phi$, e.g. for $f_{m-\frac{1}{2}}$:

$$
f_{m-\frac{1}{2}}=f_{m-\frac{1}{2}}^L+\phi_{m-\frac{1}{2}}(f_{m-\frac{1}{2}}^H-f_{m-\frac{1}{2}}^L).
$$

Here, $f_{m-\frac{1}{2}}^L$ is the low order flux, given by:

$$
f_{m-\frac{1}{2}}^L = cu_{m-1}^{n}.
$$

This is a first-order upwind flux that is dissipative. The higher order scheme is defined as:

$$
f_{m-\frac{1}{2}}^H = cu_{m-1}^{n} + c\frac{1-\sigma}{2}(u_{m}^n - u_{m-1}^n),
$$

where $\sigma=c\Delta t/\Delta x$ is the CFL number. When the solution is smooth, $\phi \approx 1$ and when under/overshoots occur $\phi \to 0$ to activate the low order flux and its dissipative character with the goal of suppressing the spurious oscillations. The weighting function $\phi$ is called a **flux limiter** because it has the role of limiting the higher-order component of the flux to prevent unphysical oscillations.

Assuming $\phi > 0$ and $\sigma \leq 1$, we can replace the flux formulas in the TVDUS scheme to obtain:

$$
u_m^{n+1} = u_m^{n} - \sigma\left[ 1-\phi_{m-\frac{1}{2}}\frac{1-\sigma}{2}+\phi_{m+\frac{1}{2}}\frac{1-\sigma}{2}\frac{u_{m+1}^n - u_{m}^n}{u_{m}^n - u_{m-1}^n} \right](u_{m}^n - u_{m-1}^n),
$$

which is of the form $u_m^{n+1}=u_m^n-a_{m-\frac{1}{2}}(u_{m}^n - u_{m-1}^n)$, with

$$
a_{m-\frac{1}{2}}=\sigma\left[ 1-\phi_{m-\frac{1}{2}}\frac{1-\sigma}{2}+\phi_{m+\frac{1}{2}}\frac{1-\sigma}{2}\frac{u_{m+1}^n - u_{m}^n}{u_{m}^n - u_{m-1}^n} \right].
$$

Since $b_{m+\frac{1}{2}}=0$, the TVD condition becomes $0 \leq a_{m-\frac{1}{2}} \leq 1$. 

Let 

$$
r_{m+\frac{1}{2}}=\frac{u_{m}^n - u_{m-1}^n}{u_{m+1}^n - u_{m}^n}.
$$

If $u$ varies linearly, $r_{m+\frac{1}{2}}=1$. If there is a local extremum, $r_{m+\frac{1}{2}}<0$. If the latter occurs, we require $\phi_{m+\frac{1}{2}}=0$ too avoid the local extrema.

Returning to the TVD condition, we must have:

$$
0 \leq \sigma + \frac{\sigma(1-\sigma)}{2}\left[ \frac{\phi_{m+\frac{1}{2}}}{r_{m+\frac{1}{2}}}-\phi_{m-\frac{1}{2}}\right]\leq 1.
$$

If $\phi_{m+\frac{1}{2}}=0$, we must have

$$
\phi_{m-\frac{1}{2}} \leq frac{2}{1-\sigma}.
$$

For $\phi_{m-\frac{1}{2}}=0$, we must have

$$
\frac{\phi_{m+\frac{1}{2}}}{r_{m+\frac{1}{2}}} \leq \frac{2}{\sigma}.
$$

Since these two conditions must be valid for all $m$, we may drop the index and write

$$
\phi \leq frac{2}{1-\sigma} \quad \mathrm{and} \quad \frac{\phi}{r} \leq \frac{2}{\sigma}.
$$

Since $0 \leq \sigma \leq 1$, in the worst case scenario we shall have

$$
\phi \leq 2 \quad \mathrm{and} \quad \frac{\phi}{r} \leq 2.
$$

Furthermore, when $r\approx 1$ the solution is smooth and we should have $\phi=1$. In order for the scheme to be TVD, we must select a function $\phi(r)$ that verifies these conditions. Some flux limiter functions are:

1. Van Leer: $\phi=\frac{r+|r|}{1+|r|}$.
2. minmod: $\phi=\mathrm{max}(0,\mathrm{min}(1,r))$.
3. Superbee: $\phi=\mathrm{max}(0,\mathrm{min}(1,2r),\mathrm{min}(2,r))$.
4. MC: $\phi=\mathrm{max}(0,\mathrm{min}(2r,(1+r)/2,2))$.



