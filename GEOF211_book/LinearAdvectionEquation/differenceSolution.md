# Solution of the difference equation

We shall solve {eq}`eq:diffEquation` analytically to illustrate some aspects of the numerical solution of {eq}`eq:Advection` by the leapfrog scheme {eq}`eq:Leapfrog`. Indeed, while it is equation {eq}`eq:Advection` that we ultimately want to solve, the time marching scheme will effectively solve {eq}`eq:diffEquation`. Thus, by studying the exact solution to {eq}`eq:diffEquation` and how close it is to {eq}`eq:anaSolution`, the exact solution of {eq}`eqAdvection`, we shall be able to say whether or not our time marching method is suitable to the task. 

We assume an exponential solution to {eq}`eq:diffEquation`:

$$
	u_{m}^{n} =B^{n\Delta t}e^{ik m\Delta x}, 
$$ (eq:diffSolution)

where $B$ can be complex. Substituting in {eq}`eq:diffEquation`, we have:

\begin{align*}
        (B^{(n+1)\Delta t} - B^{(n-1)\Delta t})e^{i\mu m\Delta x} &= -c\frac{\Delta t}{\Delta x} B^{n\Delta t}(e^{i\mu (m+1)\Delta x}-e^{i\mu (m-1)\Delta x}) \Leftrightarrow \\
        (B^{\Delta t} - B^{-\Delta t})B^{n\Delta t} e^{i\mu m\Delta x} &= -c\frac{\Delta t}{\Delta x} B^{n\Delta t}e^{i\mu m\Delta x}(e^{i\mu \Delta x}-e^{-i\mu \Delta x}) \Leftrightarrow \\
        (B^{\Delta t} - B^{-\Delta t}) &= -c\frac{\Delta t}{\Delta x} (e^{i\mu \Delta x}-e^{-i\mu \Delta x}). 
\end{align*}

Expanding the circular exponentials, we can write:

\begin{align*}
        (B^{\Delta t} - B^{-\Delta t}) &= -c\frac{\Delta t}{\Delta x} (\cos (\mu \Delta x) +  i\sin (\mu \Delta x) -
        \cos (\mu \Delta x) +  i\sin (\mu \Delta x)) \Leftrightarrow \\
        (B^{\Delta t} - B^{-\Delta t}) &= -c\frac{\Delta t}{\Delta x} (2i\sin (\mu \Delta x))
\end{align*}

and then multiply by $B^{\Delta t}$ to get:

\begin{align*}
        B^{2\Delta t} - 1 &= -c\frac{\Delta t}{\Delta x} (\cos (\mu \Delta x) +  i\sin (\mu \Delta x) -
        \cos (\mu \Delta x) +  i\sin (\mu \Delta x)) \Leftrightarrow \\
        B^{2\Delta t} - 1 &= -2iB^{\Delta t} c\frac{\Delta t}{\Delta x} (\sin (\mu \Delta x))  \Leftrightarrow \\
        B^{2\Delta t}  + & 2i\mu B^{\Delta t} -1 =  0,
\end{align*}

with $\mu = c\frac{\Delta t}{\Delta x} \sin (k \Delta x)$. Solving for $B^{\Delta t}$, we obtain:

$$
	B^{\Delta t}_\pm = -i\mu \pm \sqrt{1-\mu^2}
$$ (eqBRoots)

The roots $B^{\Delta t}_\pm$ will have different behaviours, depending on the magnitude of $|\mu|$. 

### Case 1: $|\mu| \leq 1$

For $|\mu| \leq 1$ we obtain two complex roots that we can express in polar form.

```{margin} Polar form
The polar form of a complex number $z=a+ib$ is $(a^2+b^2)^{1/2}\exp (i\arctan \frac{b}{a})$ 
```
 For $B^{\Delta t}_+$, we have:

\begin{align*}
	B^{\Delta t}_+ &= \left[ (\sqrt{1-\mu^2})^2+(-\mu)^2\right]^{1/2}\exp (i\arctan \frac{-\mu}{\sqrt{1-\mu^2}}) \\
	&= \left[1-\mu^2+\mu^2\right]^{1/2}\exp (i\arctan \frac{-\mu}{\sqrt{1-\mu^2}}) \\
	&= \exp (i\arctan \frac{-\mu}{\sqrt{1-\mu^2}}) \\
	&= \exp (-i\arcsin \mu) \\
	&= e^{-i\alpha},
\end{align*}	

with $\alpha = \arcsin \mu$, while for $B^{\Delta t}_{-}$, we obtain a similar expression:

\begin{equation}
	B^{\Delta t}_{-}= e^{i(\alpha+\pi)}.
\end{equation}

With the roots of $B^{\Delta t}$, we can return to {eq}`eq:diffSolution` and write:

$$
	u_{m}^{n} =\left[ De^{-i\alpha n} + Ee^{-i(\alpha+\pi) n} \right]e^{i\mu m\Delta x} 
$$ (eq:diffSolution2)

as the sum of the solutions for each root of $B^{\Delta t}$, since {eq}`eqAdvection` is linear. The constants $D$ and $E$ are to be found through the initial condition. 

At the initial time, $n=0$, and {eq}`eq:diffSolution2` becomes

$$
	u_{m}^{0} =\left( D + E \right) e^{i\mu m\Delta x},
$$

from which we conclude that $A=D+E$. For subsequent times ($n\ge1$), we have:

\begin{align}
	u_{m}^{n} &= \left[ De^{-i\alpha n} + Ee^{-i(\alpha+\pi) n} \right]e^{i\mu m\Delta x} \\
	&= De^{i\mu (m\Delta x - \alpha n/ \mu)} + Ee^{-i\pi}e^{i\mu (m\Delta x + \alpha n/ \mu)} \\
	&= (A-E)e^{i\mu (m\Delta x - \alpha n/ \mu)} + (-1)^{n}Ee^{i\mu (m\Delta x + \alpha n/ \mu)}.
\end{align}

The solution of {eq}`eq:diffEquation` can thus be seen to have two waves, whereas the solution to the exact equation {eq}`eqAdvection` had only one wave. 

```{note}
The two waves arise from the two roots $B^{\Delta t}_\pm$. In general, a $p$-th order scheme will introduce additional wave solutions when it is applied to a $(p-1)$-th order equation. 

An additional consequence of the use of a 2nd order scheme to solve a first order equation is that we need one additional initial condition.
```

By using the initial condition, we were able to find the value of $D$, but the value of $E$ is still to be found. We can find $E$ by marching the solution \label{eqn:diffEquationSolution2} to the first time step $n=1$. But we can't use {eq}`eq:Leapfrog`, because we don't have the value of $u^{-1}_m$. 

Instead, we have to use a two-time level like the forward scheme (Euler), that approximates the time derivative by a first-order forward formula:

$$
	u_{m}^{n+1} = u_{m}^{n} - c\frac{\Delta t}{2\Delta x}(u_{m+1}^{n}-u_{m-1}^{n}).
$$ (eq:eulerForward)

Using the initial condition $u_{m}^{0}=A e^{i \mu m\Delta x}$, we have:

\begin{align*}
	u_{m}^{1} &= Ae^{i \mu m\Delta x} - c\frac{\Delta t}{2\Delta x}A e^{i \mu m\Delta x}(e^{i \mu \Delta x}-e^{-i \mu m\Delta x}) \\
	&= Ae^{i \mu m\Delta x} \left[1 - c\frac{\Delta t}{2\Delta x}(e^{i \mu \Delta x}-e^{-i \mu m\Delta x})\right] \\
	&= A \left[1 - ic\frac{\Delta t}{2\Delta x}\sin \mu\Delta x \right]e^{i \mu m\Delta x}\\
	&= A \left[1 - i\mu \right]e^{i \mu m\Delta x}\\
	&=A \left[1 - i\sin \alpha \right]e^{i \mu m\Delta x},
\end{align*}

which is the solution at $n=1$. Now we can solve for $E$:

\begin{align*}
	A \left[1 - i\sin \alpha \right]e^{i \mu m\Delta x} &= (A-E)e^{i\mu (\Delta x - \alpha/ \mu)} - Ee^{i\mu (\Delta x + \alpha/ \mu)}\Leftrightarrow \\
	A \left[1 - i\sin \alpha \right]e^{i \mu m\Delta x} &= e^{i \mu m\Delta x} \left[(A-E)e^{-i\alpha} - Ee^{i\alpha}\right]\Leftrightarrow \\
	A \left[1 - i\sin \alpha \right] &=  (A-E)e^{-i\alpha} - Ee^{i\alpha} \Leftrightarrow \\
	A \left[1 - i\sin \alpha \right] &=  (A-E)e^{-i\alpha} - Ee^{i\alpha} \Leftrightarrow \\
	A - A\cos \alpha &= -E (2\cos \alpha) \Leftrightarrow \\
	E &= \frac{A(\cos \alpha -1)}{2\cos \alpha}.
\end{align*}

We can now write the full solution of the difference equation {eq}`eq:diffEquation` as: 

$$
	u_{m}^{n} = A \frac{1+\cos \alpha}{2\cos \alpha}e^{i\mu (m\Delta x - \alpha n/ \mu)} + (-1)^{n+1}A \frac{1-\cos \alpha}{2\cos \alpha}e^{i\mu (m\Delta x + \alpha n/ \mu)}.
$$ (eq:solutionDiffEquation)

This solution is composed of two wave forms of different amplitudes and that travel in opposite senses. 

When we compare with {eq}`eq:anaSolution`, that we write below in a discrete version at $(x_m,t^n)$

$$
	u(x_m,t^n)=Ae^{i\mu (m\Delta x-cn\Delta t)},
$$

we see that the first waveform is similar to the exact solution, while the second waveform travels in the opposite direction of the exact 
solution. This second waveform is clearly an artifact introduced by the discretization of {eq}`eqAdvection` and is a source of errors.

### Case 2: $|\mu| \gt 1$