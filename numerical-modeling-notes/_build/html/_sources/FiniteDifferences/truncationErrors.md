(finite-differences:truncation-error)=
# Truncation Error

The accuracy of the algebraic approximation to $du/dt$ {eq}`eq:discreteDerivative` can be determined with the help of the Taylor series expansion of $u(t)$: 

$$
u(t+\Delta t)=u(t)+\Delta t\frac{du}{dt} + \displaystyle\sum_{p=2}^{\infty} \frac{\Delta t^p}{p!}\frac{d^pu}{dt^p}
$$ (eq:taylorSeries)

Rearranging for $du/dt$, we obtain, using the discretized $t^n$:

$$
\frac{du}{dt} = \frac{u^{n+1}-u^n}{\Delta t} - \displaystyle\sum_{p=2}^{\infty} \frac{\Delta t^{p-1}}{p!}\frac{d^pu}{dt^p}.
$$ (eq:fdExpansion)

The difference between the exact derivative {eq}`eq:exactDerivative` and our algebraic approximation {eq}`eq:discreteDerivative` is the second term of the right hand side of {eq}`eq:fdExpansion`. Expanding this term up to $p=3$, we see its general form:

$$
\frac{\Delta t}{2!}\frac{d^2u}{dt^2}+\frac{\Delta t^2}{3!}\frac{d^3u}{dt^3}+O(\Delta t^3),
$$ (eq:truncationError)

where $O(\Delta t^3)$ represents terms proportional to $\Delta t^3$ and to higher powers of $\Delta t$. 

Expression {eq}`eq:truncationError` is the **truncation error**, which is the error we incurr when we approximate the exact derivative {eq}`eq:exactDerivative` with the algebraic expression {eq}`eq:discreteDerivative`.

The algebraic approximation {eq}`eq:discreteDerivative` can thus be written as:

$$
\frac{du}{dt} = \frac{u^{n+1}-u^n}{\Delta t} + O(\Delta t),
$$ (eq:discreteDeriavtiveError)

where $O(\Delta t)$ represents the truncation error of the approximation, whose first term, the *leading order* term is proportional to $\Delta t$. Since the leading order term is proportional to the first power of $\Delta t$, we say that this approximation is a *first order* approximation to the first derivative. 
