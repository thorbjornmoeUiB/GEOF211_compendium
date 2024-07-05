# Matrix Stability Analysis

In the matrix method of stability analysis, the numerical solution at every grid point at time step $n+1$ is expressed in terms of the values at time step $n$ as:

$$
\mathbf{u}^{n+1}=F\mathbf{u}^{n},
$$ (eq:matrixStability)

where $\mathbf{u}^{n}=u_{m=0,1,\dotsc,M}^n$ and $F$ is a matrix that represents the finite-difference operator.

Let us consider again the FTCS scheme for the diffusion equation. 

We can write {eq}`eq:FtcsDiffusion` as

$$
u_m^{n+1} = \tau u_{m-1}^{n} + (1-2\tau)u_{m}^{n} + \tau u_{m+1}^{n}, \quad \tau=D\frac{\Delta t}{\Delta x^2},
$$

which, if we take $u_0^n=u_M^n=0$, can be cast in matrix form as:

$$
\begin{bmatrix}
    u_1^{n+1}\\
    u_2^{n+1}\\
    u_3^{n+1}\\
    \vdots\\
    u_{M-1}^{n+1}
\end{bmatrix}
=
\begin{bmatrix}
    1-2\tau &   \tau  &    0    &    0   &  \cdots &   0    &   0    \\
    \tau    & 1-2\tau &  \tau   &    0   &  \cdots &   0    &   0    \\
    0       &   \tau  & 1-2\tau &  \tau  &  \cdots &   0    &   0    \\
    \vdots  &         &         &        &  \vdots &        & \vdots \\
    0       &    0    &    0    &    0   &  \cdots &  \tau  & 1-2\tau
\end{bmatrix}
\begin{bmatrix}
    u_1^{n}\\
    u_2^{n}\\
    u_3^{n}\\
    \vdots\\
    u_{M-1}^{n}
\end{bmatrix}.
$$ (eq:matrixForm)

From {eq}`eq:matrixForm` we can define the recurrence relationship

$$
\mathbf{u}^{n+1}=F\mathbf{u}^{n}=F(F\mathbf{u}^{n-1})= \cdots = (F)^{n+1}\mathbf{u}^{0},
$$ (eq:matrixRecurrence)

which makes it clear that the stability of the scheme is related to the matrix $F$, as $|\mathbf{u}^{n+1}/\mathbf{u}^{n}|=|F|$, where $|F|$ is a norm of $F$. 

A suitable norm of $F$ is the spectral norm:

$$
|F|=\rho(F)^{1/2}
$$

```{margin} Spectral radius
The spectral radius of a square $p \times p$ matrix $F$ is the maximum of the absolute values of the eigenvalues $l_p$ of $F$:

$$
\rho(F)=\mathrm{max} \{|l_1|,|l_2|,\dotsc,l_p|\}
$$ 

```

where $\rho(F)$ is the spectral radius of $F$. 

For $F$ in {eq}`eq:matrixForm`, each eigenvalue $l_p$ and eigenvactor $\mathbf{v}_p$ satisfies

$$
F\mathbf{v}_p = l_p\mathbf{v}_p, \quad p=1,2,\dotsc,M-1.
$$

If the eigenvectors form a complete, linearly independent set, they form a basis with which an arbitrary initial condition $\mathbf{u}_0$ can be expressed as:

$$
\mathbf{u}^0=\sum_{p}\alpha_p\mathbf{v}_p, \quad \alpha_p \text{ constant }.
$$ (eq:basis)

For most cases of common interest, $F$ indeed has a complete set of eigenvectors
```{margin} Eigenvector completeness
For $F$ to have a complete set of eigenvectors, it is sufficient to have all eigenvalues $l_p$ distinct.
```
and we can write:

$$
\mathbf{u}^{n+1}=(F)^{n+1}\mathbf{u}^0=(F)^{n+1}\sum_{p}\alpha_p\mathbf{v}_p\\
   =\sum_{p}\alpha_p(F)^{n+1}\mathbf{v}_p=\sum_{p}\alpha_p(F)^{n}F\mathbf{v}_p,
$$

or

$$
\mathbf{u}^{n+1}=\sum_{p}\alpha_p(l_p)^{n+1}\mathbf{v}_p.
$$

For the scheme to be stable, $\mathbf{u}^{n+1}$ must remain bounded, which implies

$$
|l_p|\leq 1, \quad \text{for all } p.
$$

The effec of a particular $l_p$ in the numerical solution will be:
* Amplifying, if $|l_p|> 1$.
* Neutral, if $|l_p|= 1$.
* Damping, if $|l_p|< 1$.

Returning to the numerical solution of the diffusion equation {eq}`eq:matrixForm`, we write:

$$
F = I + \tau G,
$$

with

$$
G=
\begin{bmatrix}
    -2 &   1  &    0    &    0   &  \cdots &   0    &   0    \\
    1    & -2 &  1   &    0   &  \cdots &   0    &   0    \\
    0       &   1  & -2 &  1  &  \cdots &   0    &   0    \\
    \vdots  &         &         &        &  \vdots &        & \vdots \\
    0       &    0    &    0    &    0   &  \cdots &  1  & -2
\end{bmatrix}
$$

so that $F=f(G)$ and thus $l_p=f(g_p)$, where the $g_p$ are the eigenvalues of G.

Since $G$ is tridiagonal with structure $a,b,c$, the $g_p$ are

$$
g_p = b + 2\sqrt{ac}\cos\frac{p\pi}{M}=-2 + 2\cos\frac{p\pi}{M}, \quad p=1,2,\dotsc,M-1
$$

and the $l_p$ are

$$
l_p = 1-2\tau(1-\cos\frac{p\pi}{M})=1-2\tau(2\sin^2\frac{p\pi}{2M})=1-4\tau\sin^2\frac{p\pi}{2M}),  \quad p=1,2,\dotsc,M-1,
$$

which is the same as {eq}`eq:vonNeumannConditionDifffusion`, leading to the same stability condition as the Von Neumann stability analysis method.




