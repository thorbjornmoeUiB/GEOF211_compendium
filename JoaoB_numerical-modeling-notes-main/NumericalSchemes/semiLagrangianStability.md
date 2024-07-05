# Stability of semi-lagragian schemes

The semi-lagrangian scheme can be written as

$$
U_{m}^{n+1}=\alpha U_{m-p-1}^n + (1-\alpha)U_{m-p}^n. 
$$ (eq:semiLagrangian)

Let us assume a solution like

$$
U_m^n=B^ne^{i\lambda m\Delta x}
$$

and replace it in {eq}`eq:semiLagrangian`. After removing the common term $e^{i\lambda m\Delta x}$, we obtain

$$
\frac{B^{n+1}}{B^n} = \alpha e^{i\lambda (-p-1)\Delta x} + (1-\alpha)e^{i\lambda (-p)\Delta x} \\
= e^{i\lambda (-p)\Delta x}[(1-\alpha)+\alpha e^{-i\lambda\Delta x}].
$$

For the scheme to be stable we need that $|B^{n+1}/B^n|\leq 1$. This can be easily checked:

$$
\left|\frac{B^{n+1}}{B^n}\right|^2 &= |e^{i\lambda (-p)\Delta x}|^2|(1-\alpha)+\alpha e^{-i\lambda\Delta x}|^2 \\
&=|(1-\alpha)+\alpha(\cos \lambda \Delta x-i\sin\lambda\Delta x)|^2 \\
&=1-2\alpha(1-\alpha)[1-\cos\lambda \Delta x].
$$

For all $\theta$, $0\leq 1 - \cos\theta \leq 2$, so in the worst case scenario, we shall have

$$
\left|\frac{B^{n+1}}{B^n}\right|^2 = 1-4\alpha(1-\alpha)=(1-2\alpha)^2\leq 1, \quad 0<\alpha<1.
$$

For $1-\cos\lambda \Delta x=0$, we shall have $|B^{n+1}/B^n|^2=1$. In either case,

$$
\left|\frac{B^{n+1}}{B^n}\right|^2 \leq 1,
$$

so the semi-Lagrangian scheme is unconditionally stable. 

```{figure} stability-semi-lagrangian.png
---
height: 400px
name: fig:stability-semi-lagrangian
---
t-x diagram of the Leapfrog and semi-Lagrangian schemes for the linear advection equation, with $\Delta t=4$, $\Delta x=3$ and $c=2$. 
```

The unconditional stability of the semi-Lagragian scheme comes from the fact that the *physical* domain of dependence of the solution is always contained in the *numerical* domain of dependence of the scheme. Consider the situation in {numref}`fig:stability-semi-lagrangian`, that represents the t-x diagram of a model where the Leafrog scheme and the semi-Lagrangian are employed to solve the linear advection equation .

At time step $n+1$, the Leapfrog scheme is unstable because $\sigma=c\Delta t/\Delta x>1$. This is visible in the diagram because the characteristic line that goes through $x_m^{n+1}$ does not fall within the numerical domain of dependence of the Leapfrog scheme. The characteristics lines are the physical domain of dependence since the solution of the linear advection equation propagates along them. 

For the semi-Lagrangian scheme the situation is different. As the particle moves along the characteristic line, the departure point $x_{\ast}^n$ will always fall on the intersection of the characteristic line with the spatial grid $x_m$ of the previous time step. Since all values of $u_m^n$, the physical domain of dependence will always be between two know values of the solution, which can then be interpolated to find $u_{\ast}^n$.

