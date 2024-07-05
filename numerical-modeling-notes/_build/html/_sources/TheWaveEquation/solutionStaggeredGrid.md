# Solution on a staggered grid

Solution of the linear gravity wave equation on a staggered grid does not suffer from the spurious mode of the solution on a regular grid. Consider the staggered grid of {numref}`figStaggeredrGrid`.

```{figure} figStaggeredGrid1d.png
---
height: 80px
name: figStaggeredrGrid
---
Staggered grid configuration with variables $u$ and $\eta$ displace halp a grid step.
```

A scheme to solve {eq}`eq:linearGravityWave` on the staggered grid, that also uses time staggering, is the following:

$$
\frac{\eta_m^{n+1} - \eta_m^{n}}{\Delta t} &= -H \frac{u_{m+\frac{1}{2}}^{n} - u_{m-\frac{1}{2}}^{n}}{\Delta x}\\
\frac{u_{m+\frac{1}{2}}^{n+1} - u_{m+\frac{1}{2}}^{n}}{\Delta t} &= -g \frac{\eta_{m+1}^{n+1} - \eta_{m}^{n+1}}{\Delta x}.
$$ (eq:staggeredGridScheme)

To eliminate $u$ from {eq}`eq:staggeredGridScheme`, we use the backward formula for the derivatives, thereby obtaining a 2nd order scheme:

$$
\eta_m^{n+1} - 2\eta_{m}^{n} + \eta_m^{n-1} = gH\frac{\Delta t^2}{\Delta x^2} (\eta_{m+1}^{n+1} -2\eta_{m}^{n+1} + \eta_{m-1}^{n+1}).
$$ (eq:waveStaggered)

For the staggered grid scheme {eq}`eq:waveStaggered`, the spatial difference operator $D$ is

$$
\mathcal{S}(\eta)&=\frac{gH}{\Delta x^2}(e^{ik\Delta x}-2+e^{-ik\Delta x}) \\
                &= -4\frac{gH}{\Delta x^2}\sin^2\frac{k\Delta x}{2} = -\omega^2,
$$

whose null space $\mathcal{S}(\eta)=0$ is

$$
\frac{k\Delta x}{2}=\pi \implies k=\frac{2\pi}{\Delta x}.
$$

This wavenumber is higher than the maximum wave number that a grid with spacing $\Delta x$ can represent, so the staggered grid does not have a spurious mode.

