(Useful_calculus:Fourier Transforms)=
# Fourier transforms

## Superposition of waves
When two or more waves meet, for example when two boats pass each other, their wake waves will overlap in space. The surface displacement (amplitude) will, at any point, be the sum of the surface displacement for the individual waves.

When looking at the ocean surface, the surface elevation can be regarded as the sum of (superposition) of many waves of different frequencies and phases.

Insert figure of individual waves and the superposition

## Time domain versus frequency domain - The Fourier Series

A data signal can be represented in either a time domain or a frequency domain. 

The time domain represents how the signal (for example air temperature, $T$) is changing with time, $t$. The time is running along the horizontal axis and the temperature is in the vertical axis. Mathematically, we would say that the temperature is a function of time, $T(t)$. 

To get a meaningful interpretation of the frequency domain, we must first approximate this signal by a superposition of many waves with different frequencies, amplitudes, and phases. The more frequencies we include in the superposition, the better the approximation is.

The amplitude of each wave in the superposition, can be derived from the following equation:

$$
c_n=\frac{1}{T}\int_{-t/2}^{T/2}f(x)e^{-12\pi\frac{n}{T}x}dx
$$ (eq:Fourier_series_amplitude)

The approximated signal is called the Fourier series, and is calculated from:

$$
f(t)=\sum_{n=-\infty}^\infty c_n e^{i2\pi\frac{n}{T}t}, t\in[-T/2,T/2]
$$ (eq:Fourier_series)

When we have created our approximated signal, we can calculate the amount of energy (wave amplitude) related to each frequency. The result is a function that displays the energy as a function of frequency. This is how our signal looks in the frequency domain, and this function is called the Fourier transform:

$$
\hat{f(\t)}=\int_{-\infty}^\infty f(t)e^{-i2\pi\k t}dt
$$ (eq:Fourier_transform)

Here, the function $\hat{f(\k)}$ represent energy as a function of wave number $k$, defined as $1/L$, where L is the wavelength.

If the signal consisted of just one pure sine wave, the graph of $\hat{f(\k)}$ would contain a single spike at the frequency of this sine wave.