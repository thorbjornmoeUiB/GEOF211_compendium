# Analysis of the solution of the difference equation

In our study of the finite difference approximations to the derivative, we found that in general, when $\Delta t$ and $\Delta x$ approach zero, the errors in the approximations of the derivatives also approach zero. Therefore, since our difference equation is written with the finite difference approximations, we can ask ourselves if we will have the error of the difference equation, i.e. the difference between {eq}`eq:solutionDiffEquation` and {eq}`eq:anaSolution`, also approach zero when $\Delta t, \Delta x \to 0$.

First, let $\Delta x \to 0$. We will have:
\begin{align*}%\label{eqn:anaSol2}
	\sigma & = c\frac{\Delta t}{\Delta x} \sin (\mu \Delta x) \\
	& = c\mu \Delta t \frac{\sin (\mu \Delta x)}{\mu \Delta x} \\
	& = c\mu \Delta t,
\end{align*}
since $\lim_{\Delta x\to0}\frac{\sin (\mu \Delta x)}{\mu \Delta x}=1$. Then, consider that $\Delta t$ is small, so that $\alpha=\arcsin c\mu\Delta t \approx c\mu\Delta t$. Thus in the limit of small $\Delta t$ and $\Delta x$, we will have
\begin{align*}%\label{eqn:anaSol2}
	A \frac{1+\cos \alpha}{2\cos \alpha}e^{i\mu (m\Delta x - \alpha n/ \mu)}  &= A \frac{1+\cos \alpha}{2\cos \alpha}e^{i\mu (m\Delta x -  n c\mu\Delta t/ \mu)} \\ &= A \frac{1+\cos \alpha}{2\cos \alpha}e^{i\mu (m\Delta x -  cn \Delta t)},
\end{align*}
and we recover the waveform {eq}`eq:anaSolution`, written in the discrete grid positions $m\Delta x$ and time steps $n \Delta t$. Furthermore, if we allow $\Delta t \to 0$, we will have $\alpha = 0$ and

$$
	\frac{1+\cos \alpha}{2\cos \alpha} = 1, \frac{1-\cos \alpha}{2\cos \alpha} = 0,
$$ (eq:amplitude)

which means that in the limit of $\Delta t, \Delta x \to 0$ we recover the true solution as the second waveform of {eq}`eq:solutionDiffEquation` vanishes.

The existence of the two waveforms {eq}`eq:solutionDiffEquation` as solution of the difference equation {eq}`eq:diffEquation` is obviously problematic. The two waveforms correspond to two **modes**:

1. The **physical mode** (first waveform of {eq}`eq:solutionDiffEquation`) that approaches the true solution as $\Delta t, \Delta x \to 0$.

2. The **computational mode** (second waveform of {eq}`eq:solutionDiffEquation`), that is *spurious* (unphysical) and vanishes when $\Delta t, \Delta x \to 0$. This mode is a source of errors (in addition to the truncation errors), and we note further that it changes sign every time step (due to $(-1)^{n+1}$) and travels in the opposite direction to the physical mode.


## Amplitude

The exact solution of {eq}`eq:Advection` with the initial condition given by {eq}`eq:initialCond` is characterized by the amplitude $A$, the wavenumber $k$ and the phase speed $c$. We are interested in how well will the numerical solution represent these parameters. 

Starting with the amplitude, we know that for small $\alpha$ we will have {eq}`eq:amplitude`, so the amplitude of the physical model will $\to A$ and the amplitude of the computational model will 
$\to 0$. 

Since small $\alpha$ implies small $\sigma$, for fixed $c\Delta t/\Delta x$, it implies small $k\Delta x = 2\pi\Delta x/L$, which will occur when $\Delta x \ll L$. 

Therefore, for the amplitude of the physical mode to approach the amplitude $A$ of the true solution, we must choose a $\Delta x$ much smaller than the wavelength $L$, or in other words, we should have as many grid points as possible to resolve one wavelength. 

```{note}
Since $\Delta t$ and $\Delta x$ are choices of the numerical modeler, we can always choose $\Delta t$ to maintain $c\Delta t/\Delta x$ constant when $\Delta x$ changes. In fact, this "freedom" in the choice of the time step is one of the ways to maintain the stability of the numerical scheme as the grid resolution changes.
```

## Phase speed

With respect to the phase speed $c$, if we compare the exact solution of {eq}`eq:Advection` with the solution {eq}`eq:solutionDiffEquation` of the difference equation, we observe that the counterpart of $ct$ is $n\alpha/\mu$. This quantity is:

$$
	\frac{n\alpha}{\mu} = \frac{n\alpha\Delta t}{\mu\Delta t} =  \frac{\alpha t}{\mu\Delta t} = c^\prime t,
$$

where:

$$
	c^\prime = \frac{\alpha}{\mu\Delta t} = \frac{\arcsin\left[ \left( c\Delta t/\Delta x \right) \sin \mu\Delta x
	  \right]}{\mu\Delta t}
$$

is the phase speed of the solution {eq}`eq:solutionDiffEquation` of the difference equation. We shall now see how does $c^\prime$ compares with the phase speed $c$ of the true solution.

First, if $c\Delta t/\Delta x = 1$, we'll have $c^\prime/c = 1$, because
\begin{equation}
	c^\prime = \frac{\arcsin\left(\sin \mu\Delta x
	  \right)}{\mu\Delta t} = \frac{\mu\Delta x}{\mu\Delta t} = \frac{\Delta x}{\Delta t} = c.
\end{equation}
This means that when $c\Delta t/\Delta x = 1$ there are no errors in the phase speed of the numerical solution.

In the general case, we'll have

$$
\frac{c'}{c}=1-\frac{1}{6}\left[ \Delta x^2 -c \Delta t\right]\mu^2.
$$

So larger $\Delta t$ will increase $c'/c$ and larger $\Delta x$ will make $c'/c$ decrease, with this later effect dominating. In whichever case, $c'/c < 1$, and $c'<c$ so the speed of the finite difference wave is always less than the speed of the exact wave. 

In addition, as $\Delta x/L \to 0$, $c' \to c$. This means that waves with large $L$ have smaller phase speed errors. So, if the initial field has many wavelengths, it will be distorted as the numerical integration proceeds, with the shorter waves being delayed wrt the larger waves. This phenomenon is called *computational dispersion*.

## Group velocity

The group velocity is the velocity at which energy propagates. It is given by

$$
\nu=\frac{d(\mu c)}{d\mu}=-L^2\frac{d}{dL}\left(\frac{c}{L}\right).
$$

In the linear advection equation, $c$ is constant so

$$
\nu=-L^2\frac{d}{dL}\left(\frac{c}{L}\right)=-cL^2\frac{d}{dL}\left(\frac{1}{L}\right)=-cL^2\left(-\frac{1}{L^2}\right)=c.
$$

and the energy propagates at the same speed as the waveform. For {eq}`eq:solutionDiffEquation`, we have

$$
\nu'=\frac{d(\mu c')}{d\mu}=\frac{d}{d\mu}\left\{\frac{\mu \sin^{-1}\left[ c\frac{\Delta t}{\Delta x} \sin \mu\Delta x\right]}{\mu\Delta t} \right\},
$$

which gives

$$
\nu'=c \frac{\cos\mu\Delta x}{\left[1-\left( c\frac{\Delta t}{\Delta x} \sin\mu\Delta x\right)^2\right]^{1/2}}.
$$

First, lets look at the case when $c\Delta t/\Delta x = 1$. In this case, we have

$$
\nu'=c \frac{\cos\mu\Delta x}{\left[1-\sin^2\mu\Delta x\right]^{1/2}}=c \frac{\cos\mu\Delta x}{\cos\mu\Delta x}=c,
$$

and {eq}`eq:solutionDiffEquation` has the same group velocity as the exact solution. 

When $c\Delta t/\Delta x < 1$, if $\mu$ is small (small wavenumber, long wavelengths), $\sin \mu\Delta x \to 0$ and $\cos \mu\Delta x \to 1$, which results in $\nu'=c$. 

If $\mu$ is large however (short wavelengths), we shall have large errors in the group velocity, e.g. for:

1. $L=4\Delta x$: $\mu\Delta x=\pi/2$ and

$$
\nu'=c \frac{\cos \pi/2}{\left[1-\left( c\frac{\Delta t}{\Delta x} \sin(\pi/2) \right)^2\right]^{1/2}}=0.
$$ 

2. $L=2\Delta x$: $\mu\Delta x=\pi$ and

$$
\nu'=c \frac{\cos \pi}{\left[1-\left( c\frac{\Delta t}{\Delta x} \sin\pi\right)^2\right]^{1/2}}=-c.
$$ 

Therefore, the energy of the $4\Delta x$ wavelength becomes stationary and the energy of the $2\Delta x$ wavelength travels *upstream*. Since we should have $\Delta x \ll \mathbf{L}$ in our model, these wavelengths will most likely be noise in our model.
