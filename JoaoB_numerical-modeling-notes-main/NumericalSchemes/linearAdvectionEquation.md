# The linear 1-d advection equation

The linear 1-d advection equation is a simple model for the advection process. It models the propagation of a function $u$ in one dimensionsal space $x$ with speed $c$. 

$$
	\frac{\partial u}{\partial t} + c  \frac{\partial u}{\partial x} = 0
$$ (eqAdvection)

Function $u$ is a generic function that may be viewed as a geophysical quantity of interest such as temperature. The propagation speed $c$ can be viewed as the speed with which a particular feature of the quantity of intereste moves across $x$, such as the speed at which a temperature front moves in space or, if temperature is represented by a wavelike function, $c$ may be regarded as the phase speed of the wavelike function. 

The general solution of {eq}`eqAdvection` is the initial condition $u(x,t=0)=u0$ translating in space: $u(x,t)=u0(x-ct)$.
