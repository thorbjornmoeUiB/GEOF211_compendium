(Useful_calculus:Taylor_Polynomials)=
# Taylor series

Taylor polynomials or Taylor series are approximations of a function near a point $a$. This holds if  $f$ is a function whose $n+1^{th}$ derivative exists on an interval containing the point $a$. The approximation is better the more terms you include and the closer you are to the point $a$. 

$$
f(x)=f(a)+\frac{f'(a)}{1!}(x-a)+\frac{f''(a)}{2!}(x-a)^2+\frac{f'''(a)}{3!}(x-a)^3+...=\sum_{n=0}^{\infty}\frac{f^{(n)}(a)}{n!}(x-a)^n
$$ (eq:Taylor_series)

# McLaurin series
The McLaurin series are special cases of the Tayolor series, where the series are calculated for a region close to origo, setting $a=0$:

$$
f(x)=f(a)+\frac{f'(0)}{1!}x+\frac{f''(0)}{2!}x^2+\frac{f'''(0)}{3!}x^3+...=\sum_{n=0}^{\infty}\frac{f^{(n)}(0)}{n!}x^n
$$ (eq:McLaurin_series)

## Examples of Taylor and McLaurin series
Taylor series for $sin(x)$:

$$
sin(x)= sin(a)+cos(a)(x-a)-\frac{sin(a)(x-a)^2}{2!}-\frac{cos(a)(x-a)^3}{3!}+...=\sum_{n=0}^{\infty}\frac{sin^{(n)}(a)}{n!}(x-a)^n
$$ (eq:Taylor_sine)

McLaurin series for $sin(x)$:

$$
\begin{align}
sin(x)& = sin(0)+cos(0)(x-0)-\frac{sin(0)(x-0)^2}{2!}-\frac{cos(0)(x-0)^3}{3!}+...&=\sum_{n=0}^{\infty}\frac{sin^{(n)}(0)}{n!}(x-0)^n\\
& =x-\frac{x^3}{3!}+\frac{x^5}{5!}-\frac{x^7}{7!}+...=\sum_{n=0}^{\infty}(-1)^n\frac{x^{2n+1}}{(2n+1)!}
\end{align}
$$ (eq:McLaurin_sine)

