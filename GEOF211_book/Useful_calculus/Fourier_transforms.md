(Useful_calculus:Fourier Transforms)=
# Fourier transforms

## Superposition of waves
When two or more waves meet, for example when two boats pass each other, their wake waves will overlap in space. The surface displacement (amplitude) will, at any point, be the sum of the surface displacement for the individual waves.

When looking at the ocean surface, the surface elevation can be regarded as the sum of (superposition) of many waves of different frequencies and phases.

Insert figure of individual waves and the superposition

## Time/space domain versus frequency domain - The Fourier Series

A data signal can be represented in either a time/space domain or a frequency domain. 

The time domain represents how the signal (for example air temperature) is changing with time, $t$. The time is running along the horizontal axis and the temperature is in the vertical axis. Mathematically, we would say that the temperature is a function of time, $f(t)$. Similarly, the space domain represents how the signal (for example air temperature) is changing with space or distance, $x$. Then, the resulting function would be $f(x)$. 

To get a meaningful interpretation of the frequency domain, we must first approximate our signal by a superposition of many waves with different frequencies, amplitudes, and phases. The more frequencies we include in the superposition, the better the approximation is.

The amplitude of each wave in the superposition, can be derived from the following equation:

$$
c_n=\frac{1}{T}\int_{-t/2}^{T/2}f(t)e^{-1\frac{2\pi}{T}t}dt
$$ (eq:Fourier_series_amplitude)

The approximated signal is called the Fourier series, and is calculated from:

$$
f(x)=\sum_{n=-\infty}^\infty c_n e^{i 2\pi\frac{n}{T}t}, t\in[-T/2,T/2]
$$ (eq:Fourier_series)

, where T represent a certain Time period of interest.

When we have created our approximated signal, we can calculate the amount of energy (wave amplitude) related to each frequency. The result is a function that displays the energy as a function of frequency. If we let $t\leftarrow \infty$ and include enough wave frequencies to allow $n/T \leftarrow \psi$ we can now write a function of the amount of energy as in terms of each wave. This is how our signal looks in the frequency domain, and this function is called the Fourier transform:

$$
\hat{f(\psi)}=\int_{-\infty}^\infty f(t)e^{-i2\pi\psi t}dt
$$ (eq:Fourier_transform)

Here, the function $\hat{f(\psi)}$ represent energy as a function of the frequency $\psi$. If the signal consisted of just one pure sine wave, the graph of $\hat{f(\psi)}$ would contain a single spike at the frequency of this sine wave.

# Gibbs phenomenon
In practice, we typically cannot include an infinite number of terms in the Fourier series to represent a signal. using a limited number of components works fine for continuous signals, but will produce errors (overshoots and undershoots) near discontinuities and areas wih strong gradients. This is called the Gibbs phenomenon.