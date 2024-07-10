(Prerequisites:Complex-numbers)=
# Useful identities for dealing with trigonometry and complex numbers

Here, you can find useful identities regarding trigonometric functions, complex numbers, and the Euler formula. These will be useful later when working on von Neumann stability analysis of finite difference schemes. 

## Trigonometric identities

### Pythagorean indentity
$$
\sin^2 x+\cos^2 x=1
$$ (eq:Trig_pythagoras)

### Sine and cosine additive identities
$$
\sin(x+y)=\sin x\cos y+\cos x\sin y
$$ (eq:Trig_sine_add)

$$
\cos(x+y)=\cos x\cos y-\sin x\sin y
$$ (eq:Trig_cos_add)

### Double angle formulas
$$
\sin(2x)=2\sin x\cos x
$$ (eq:Trig_sine_double)

$$
\cos(2x)=\cos^2 x-\sin^2 x=2cos^2 x-1=1-2\sin^2x
$$ (eq:Trig_cosine_double)

### Half angle formulas
$$
\sin(\frac{x}{2})=\pm \sqrt{\frac{1-\cos x}{2}}
$$ (eq:Trig_sine_half)

$$
\cos(\frac{x}{2})=\pm \sqrt{\frac{1+\cos x}{2}}
$$ (eq:Trig_cosine_half)

## Complex numbers
$$
z=x+iy
$$ (eq:Complex_def)

$$
\abs(z)^2=x^2+y^2
$$ (eq:Complex_norm_squared)

### The triangle inequality
If $z$ and $w$ are two complex numbers:
$$
\abs(z+w)<\abs(z)+\abs(w)
$$ (eq:Complex_triangle_identity)


## The Euler formula and modifications

### Eulers identity
$$
e^{i\pi}+1=0
$$ (eq:Euler_identity)

### Eulers formula
$$
e^{ix}=\cos x+i\sin x
$$ (eq:Euler)

### Cosine exponential form
$$
\frac{e^{ix}+e^{-ix}}{2}=\cos )
$$ (eq:Euler_cos)

### Sine exponential form
$$
\frac{e^{ix}-e^{-ix}}{2i}=\sin x
$$ (eq:Euler_sin)

### Tangent exponential form
$$
\frac{e^{ix}-e^{-1x}}{i(e^{ix}+e^{-1x})}=\tan x
$$ (eq:Euler_tan)

### Complex exponential
$$
e^{x+iy}=e^x(\cos y+i\sin y)
$$ (eq:Euler_complex_exp)

### de Moivre's theorem
$$
(\cos x+i\sin x)^n=\cos nx+i\sin nx
$$ (eq:Euler_sine_add)


