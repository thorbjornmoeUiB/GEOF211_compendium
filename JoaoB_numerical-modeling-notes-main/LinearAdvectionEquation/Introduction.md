(linearadvection:intro)=
# The linear advection equation

The linear advection equation is a first order partial differential equation that represents, in a simple form, the process of advection in the atmosphere and ocean. The equation

$$
\frac{\partial u}{\partial t} + a \frac{\partial u}{\partial x} = 0, c>0
$$(eq:Advection)

models the transport of a signal $u(x,t)$ in 1-d space with velocity $a$, that may also be interpreted as a phase speed of a wave that propagates in the positive $x$-direction. Equation {eq}`eq:Advection` is similar to the first two terms of the momentum equations (e.g. {cite:t}`Cushman-RoisinBeckers2011`, p. 106), that represent the nonlinear advection of momentum by the motions of the fluid. 

Its simplicity and its closeness to the equations that govern fluid flow make it an attractive model with which to study the solution of partial differential equations with numerical methods. 

The simplicity of {eq}`eq:Advection` makes possible obtaining an analytic solution and also solve the associated difference equations, allowing a direct comparison of the analytic and numerical solutions.
 
```{tableofcontents}
```
