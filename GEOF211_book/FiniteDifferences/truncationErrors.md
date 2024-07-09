(finite-differences:truncation-error)=
# Truncation Error

The accuracy of the algebraic approximation to $du/dt$ {eq}`eq:discreteDerivative` can be determined with the help of the Taylor series expansion of $u(t)$ around the point $a=t^n$, where $t^n$ is reprecenting a chosen time ste. Note that $u^{n+1}=u(t^{n+1})=u(t^n+\Delta t)$ and $u^{n}=u(t^n)$.


$$
u(t)=u^n+\frac{u'(t^n)}{1!}(t-t^n)+\frac{u''(t^n)}{2!}(t-t^n)^2+\sum_{p=3}^{\infty}\frac{u^{(p)}(t^n)}{p!}(t-t^n)^p
$$ (eq:taylorSeries_v1)

Note that $u'(t^n)$ can also be written $\frac{du}{dt}|_{t^n}$. You will find that some references omit displaying the $|_{t^n}$ in the derivative terms. We will include them here for completeness.

Now, since we are interested in the time step coming after $t^n$ we write out the equation for $t=t^{n+1}$, and note that $(t^{n+1}-t^n)=\Delta t$:

$$
u^{n+1}=u^n+\Delta t\frac{du}{dt}|_{t^n}+\frac{\Delta t^2}{2!}\frac{d^2u}{dt^2}|_{t^n}+\sum_{p=3}^{\infty}\frac{\Delta t^p}{p!}\frac{d^{(p)}u}{dt^p}|_{t^n}
$$ (eq:taylorSeries)

Rearranging for $du/dt$, we obtain:

$$
\frac{du}{dt}|_{t^n}=\frac{u^{n+1}-u^n}{\Delta t}-\displaystyle\sum_{p=2}^{\infty} \frac{\Delta t^{p-1}}{p!}\frac{d^pu}{dt^p}|_{t^n}
$$ (eq:fdExpansion)

The difference between the exact derivative {eq}`eq:exactDerivative` and our algebraic approximation {eq}`eq:discreteDerivative` is the second term of the right hand side of {eq}`eq:fdExpansion`. Expanding this term up to $p=3$, we see its general form:

$$
\frac{\Delta t}{2!}\frac{d^2u}{dt^2}|_{t^n}+\frac{\Delta t^2}{3!}\frac{d^3u}{dt^3}|_{t^n}+O(\Delta t^3),
$$ (eq:truncationError)

where $O(\Delta t^3)$ represents terms proportional to $\Delta t^3$ and to higher powers of $\Delta t$. 

Expression {eq}`eq:truncationError` is the **truncation error**, which is the error we incurr when we approximate the exact derivative {eq}`eq:exactDerivative` with the algebraic expression {eq}`eq:discreteDerivative`.

The algebraic approximation {eq}`eq:discreteDerivative` can thus be written as:

$$
\frac{du}{dt}|_{t^n} = \frac{u^{n+1}-u^n}{\Delta t} + O(\Delta t),
$$ (eq:discreteDeriavtiveError)

where $O(\Delta t)$ represents the truncation error of the approximation, whose first term, the *leading order* term is proportional to $\Delta t$. Since the leading order term is proportional to the first power of $\Delta t$, we say that this approximation is a *first order* approximation to the first derivative. 
