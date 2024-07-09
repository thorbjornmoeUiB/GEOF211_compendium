(GFD:NavierStokes)=
# Navier-Stokes equation

The Navier-Stokes equation, also known as the equation of motion, describes how velocity change with time as a result of external forces such as gravity, pressure, friction, and Coriolis. Using the Boussinesq approximation, the equation can be expressed:

$$
\begin{align}
x:&\frac{\partial u}{\partial t}+u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}+w\frac{\partial u}{\partial z}&-fv&=-\frac{1}{\rho_0}\frac{\partial p}{\partial x}+\frac{\partial}{\partial x}(A_H\frac{\partial u}{\partial x})+\frac{\partial}{\partial y}(A_H\frac{\partial u}{\partial y})+\frac{\partial}{\partial z}(A_v\frac{\partial u}{\partial z})\\

y:&\,\,\frac{\partial v}{\partial t}+u\frac{\partial v}{\partial x}+v\frac{\partial v}{\partial y}+w\frac{\partial v}{\partial z}&+fu&=-\frac{1}{\rho_0}\frac{\partial p}{\partial y}+\frac{\partial}{\partial x}(A_H\frac{\partial v}{\partial x})+\frac{\partial}{\partial y}(A_H\frac{\partial v}{\partial y})+\frac{\partial}{\partial z}(A_v\frac{\partial v}{\partial z})\\

z:& &0&=-\frac{\partial p}{\partial z}-\rho g\\

\end{align} 
$$ (eq:NavierStokes)
,$\rho_0$ is a refernce density, $g$ is the gravitational acceleration, $f=2\Omega sin\phi$ is the Coriolis parameter, and $A_H$ and $A_V$ are the horizontal and vertical eddy viscosities


