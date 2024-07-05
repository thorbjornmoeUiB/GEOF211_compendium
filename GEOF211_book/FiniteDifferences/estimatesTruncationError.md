(finite-differences:estimate-truncation)=
# Estimates of the truncation error

To obtain an estimate of the truncation error, we must first estimate the magnitude of the derivatives $du/dt$, $d^2u/dt^2$, $d^3u/dt^3$, and so on. 

Let us consider a signal $u(t)$ such as the following:

```{figure} UTscales.png
---
height: 200px
name: figUTscales
---
Time and space scales of signal $u(t)$.
```

We observe that over time interval $T$ the signal shows a variation of size $U$. These characteristic values may be thought of as the time scale and the magnitude of the variation of $u$ over $T$, respectively. 

Since the derivative of $u(t)$ is the variation $\Delta u$ that occurs over time interval $\Delta t$, we can say that $U$ and $T$ are characteristic values of $\Delta u$ and $\Delta t$ and write

$$
\frac{du}{dt} \approx \frac{U}{T}.
$$ (eq:orderDuDt)

To obtain an estimate of the second derivative, we may assume that the variations in $du/dt$ also occur over the same time scale $T$, as the signal $u$, and write

$$
\frac{d^2u}{dt^2} = \frac{d}{dt} \frac{du}{dt} \approx \frac{U/T}{T} = \frac{U}{T^2}.
$$ (eq:orderDu2Dt2)

For higher order derivatives, the reasoning is the same. 

To estimate the magnitude of the truncation error, we can write that the size of the terms of {eq}`eq:truncationError` will be

$$
\Delta t \frac{U}{T^2}, \quad \Delta t^2 \frac{U}{T^3}, \quad \Delta t^3 \frac{U}{T^4}, \quad \text{etc.}
$$ (eq:magTruncationError)

For small $\Delta t$, we can retain the leading order error term in {eq}`eq:magTruncationError` and write:

$$
\frac{du}{dt}=\frac{u^{n+1}-u^n}{\Delta t} + O\left( \frac{\Delta t}{T}\frac{U}{T}\right).
$$

Now we see that the *order* of the relative error $\varepsilon$, i.e. the difference between the exact derivative and the approximation divided by the magnitude of the derivative, is

$$
O(\varepsilon)=O(\frac{\Delta t}{T}).
$$ 

This implies that to have an acceptable approximation to the derivative $du/dt$, we should have $O(\varepsilon)\ll 1$, which implies that

$$
\frac{\Delta t}{T} \ll 1 \implies \Delta t \ll T.
$$

This condition carries over easily to spatial derivatives, where the equivalent condition is $\Delta x \ll L$, where $L$ is the characteristic length, or *length scale* of the signal. 
