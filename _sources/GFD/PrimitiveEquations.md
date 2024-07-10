(GFD:Primitive Equations)=
# The Primitive equations

### The Navier-stokes equation
The Navier-Stokes equation, also known as the equation of motion, describes how velocity change with time as a result of external forces such as gravity, pressure, friction, and Coriolis. Using the Boussinesq approximation, the equation can be expressed:

$$
\begin{align}
x:&\frac{\partial u}{\partial t}+u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}+w\frac{\partial u}{\partial z}&-fv&=-\frac{1}{\rho_0}\frac{\partial p}{\partial x}+\frac{\partial}{\partial x}(A_H\frac{\partial u}{\partial x})+\frac{\partial}{\partial y}(A_H\frac{\partial u}{\partial y})+\frac{\partial}{\partial z}(A_v\frac{\partial u}{\partial z})\\
y:&\,\,\frac{\partial v}{\partial t}+u\frac{\partial v}{\partial x}+v\frac{\partial v}{\partial y}+w\frac{\partial v}{\partial z}&+fu&=-\frac{1}{\rho_0}\frac{\partial p}{\partial y}+\frac{\partial}{\partial x}(\mathscr{A}_H\frac{\partial v}{\partial x})+\frac{\partial}{\partial y}(\mathscr{A}_H\frac{\partial v}{\partial y})+\frac{\partial}{\partial z}(\mathscr{A}_v\frac{\partial v}{\partial z})\\
z:& &0&=-\frac{\partial p}{\partial z}-\rho g
\end{align} 
$$ (eq:NavierStokes)

,$\rho_0$ is a refernce density, $g$ is the gravitational acceleration, $f=2\Omega sin\phi$ is the Coriolis parameter, $\phi$ is the latitude, and $\mathscr{A}_H$ and $\mathscr{A}_V$ are the horizontal viscosity and vertical eddy diffusivities, respectively.

### The continuity equation

$$
\frac{\partial \rho}{\partial t}+\frac{\partial}{\partial x}(\rho u)+\frac{\partial}{\partial y}(\rho v)+\frac{\partial}{\partial z}(\rho w)=0
$$ (eq:Continuity_main)

For incompressible fluids, we can eliminitate $\rho$ and get the following version:

$$
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}+\frac{\partial w}{\partial z}=0
$$ (eq:Continuity)

### The density equation (energy equation)
$$
\frac{\partial \rho}{\partial t}+u\frac{\partial \rho}{\partial x}+v\frac{\partial \rho}{\partial y}+w\frac{\partial \rho}{\partial z}=\frac{\partial}{\partial x}(\mathscr{A}_H\frac{\partial \rho}{\partial x})+\frac{\partial}{\partial y}(\mathscr{A}_H\frac{\partial \rho}{\partial y})+\frac{\partial}{\partial z}(\mathscr{A}_V\frac{\partial \rho}{\partial z})
$$ (eq:Density)
If the right hand side of the density equation is zero, we have conservation of mass.

You can read more about these equations in {cite:ts}`Cushman-RoisinBeckers2011`, chapter 3.1 and 4.4

### References:

```{bibliography}
```



