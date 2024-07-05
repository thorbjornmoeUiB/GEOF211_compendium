# The MacCormack Scheme

The MacCormack scheme is another multi-step scheme. It is composed of a *predictor* step and a *corrector* step. It is one of the simplest of the *predictor-corrector* class of numerical schemes. 

The predictor step is used to obtain an estime $\tilde{u}$ of the unknown function $u$ at $t^{n+1}$:

$$
   \tilde{u}_m^{n+1}=u_m^n - c\frac{\Delta t}{\Delta x}\left( u_{m+1}^n - u_m^n \right)
$$

Note the use of a **forward** formula to approximate the spatial derivative. The corrector step uses the estimates $ \tilde{u}^{n+1}$ to approximate the spatial derivative with a **backward** formula:

$$
   u_m^{n+1}=u_m^{n+\frac{1}{2}} - c\frac{\Delta t}{2\Delta x}\left( \tilde{u}_{m}^{n+1} - \tilde{u}_{m-1}^{n+1} \right)
$$

To obtain the solution at $t^{n+\frac{1}{2}}$, we simply average the function at $t^n$ and the estimate at $t^{n+1}$: 

$$
   u_m^{n+\frac{1}{2}} = \frac{u_m^{n} + \tilde{u}_m^{n+1}}{2}
$$

The final scheme is:

$$
u_m^{n+1} = \frac{u_m^{n} + \tilde{u}_m^{n+1}}{2} - c\frac{\Delta t}{2\Delta x}\left( \tilde{u}_{m}^n - \tilde{u}_{m-1}^n \right)
$$

## Consistency, stability and convergence

For the linear advection equation, the MacCormack scheme is equivalent to the Lax-Wendroff scheme, so its properties are the same as those of the latter. 

## Application: propagation of top hat function

The MacCormack scheme applied to the top hat initial condition gives the same solution as the Lax-Wendroff scheme.


