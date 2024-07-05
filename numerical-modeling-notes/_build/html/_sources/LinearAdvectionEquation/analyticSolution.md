# The exact equation

The analytic (exact) solution of {eq}`eq:Advection` can be obtained by the method of the separation of variables. We shall assume an initial condition in the form of a simple wave:

```{margin} Euler's formula
Euler's formula 

$$
e^{i\theta}=\cos \theta + i\sin \theta.
$$

is widely used to represent simple oscillatory behaviour. 
```

$$
	u(x,0)=A e^{i k x},
$$ (eq:initialCond)

where $k = 2\pi/\lambda$ is the wave number ($\lambda$ is the wavelength). 

Let the solution to {eq}`eq:Advection` with initial condition {eq}`eq:initialCond` be given by

$$
	u(x,t)=G(t)H(x).
$$ (eq:sepVar)

Substituting in {eq}`eq:Advection`, we have

\begin{align*} 
   \frac{\partial }{\partial t} (G(t)H(x))=& -c \frac{\partial }{\partial x} (G(t)H(x)) \\
   H(x) \frac{\partial G(t)}{\partial t} =& -c G(t) \frac{\partial H(x)}{\partial x} \\
   \frac{1}{G(t)} \frac{\partial G(t)}{\partial t} =& -c \frac{1}{H(x)} \frac{\partial H(x)}{\partial x}, 
\end{align*}

that to be valid for all $(x,t)$ must be equal to a constant $-\alpha$. Integration yields

\begin{align*} 
      \frac{1}{G(t)} \frac{\partial G(t)}{\partial t} =& -\alpha \Leftrightarrow G(t)=A_1e^{-\alpha t} \\
      -c \frac{1}{H(x)} \frac{\partial H(x)}{\partial x}=& -\alpha \Leftrightarrow H(x)=A_2e^{\alpha x/c},
\end{align*}

and we find $u(x,t)=G(t)H(x)=A_1A_2e^{-\alpha t}e^{\alpha x/c}$. 

At $t=0$ we have $u(x,0)=A_1A_2e^{\alpha x/c}$, so we know that $A=A_1A_2$ and $ik = \alpha/c$ and so $\alpha=ikc$. Finally, we can write:

$$
	u(x,t)=Ae^{-ikct}e^{ikcx/c}=Ae^{ik(x-ct)},
$$ (eq:anaSolution)

which is the solution of {eq}`eq:Advection` given the initial condition {eq}`eq:initialCond`. This solution represents the initial condition moving along the positive $x$-direction with translation velocity $c$.
