(finite-differences:evaluation-truncation)=
# Evaluating the truncation error

To evaluate the effect of the truncation error, we consider the following sinusoidal function

$$
u(t)=U\sin\left( 2\pi\frac{t}{T} \right) = U\sin(\omega t), \quad \omega=\frac{2\pi}{T},
$$

whose first derivative is $U\omega \cos(\omega t)$. In {numref}`figErrors1stDerivative`, the error of the first derivative is shown for the forward, backward, centred and 4th order difference formulas.


```{figure} Errors_FDfirstDerivative_w4th.png
---
height: 400px
name: figErrors1stDerivative
---
Error of the first derivative formulas.
```

As $\omega \Delta t \to 0$, the error of the 4th order formula decreases much faster than those of the centred (2nd order) and forward/backward (1st order) formulas. 



