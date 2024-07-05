# Linear 1-d Gravity Waves

The linear one dimensional gravity wave equations are:

$$
  \frac{\partial \eta}{\partial t} &+ H\frac{\partial u}{\partial x} = 0\\
  \frac{\partial u}{\partial t} &+ g\frac{\partial \eta}{\partial x} = 0
$$ (eq:linearGravityWave)

where $t$ is time, $x$ is the horizontal coordinate, $\eta$ is the free--surface displacement, $u$ is the horizontal velocity, $H$ is the undisturbed fluid depth and $g$ is the acceleration of gravity. 

The equations describe the time evolution of the shape of the free-surface and of the horizontal fluid velocity under the action of gravity, in an one-dimensional domain (unit thickness in the horizontal coordinate $y$, normal to $x$).

The system of equations can be transformed in to a single equation with respect to $\eta$ by taking the time and space derivatives of the first and second equations, respectively. We thus obtain the following second-order equation for the free--surface elevation:

$$
    \frac{\partial^2 \eta}{\partial t^2} = gH\frac{\partial^2 \eta}{\partial x^2}
$$ (eqWave)

The wave equation {eq}`eqWave` has a general solution of the form $\eta(x,t)=E_1(x-ct)+E_2(x+ct)$, which represents two waves propagating in opposite directions with the same phase speed $c=\sqrt{gH}$. 