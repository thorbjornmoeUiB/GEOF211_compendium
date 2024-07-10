(Prerequisites:Fourier Transforms)=
# Fourier transforms

## Superposition of waves
When two or more waves meet, for example when two different boats pass each other, the waves will overlap in space, and the surface displacement (amplitude) will, at any point, be the sum of the surface displacement for the individual waves.

Insert figure of individual waves and the superposition

## Time domain versus frequency domain - The Fourier Series

A data signal can be represented in either a time domain or a frequency domain. The time domain is typically what you are measuring and what you are used to seeing, e.g., how temperature changes with time, with many local minima and maxima (ADD FIG EXAMPLE). We can approximate this signal by a superposition of many different waves with different frequencies, amplitudes, and phases. The more frequencies we include in the superposition, the better the approximation is. The amplitude of each wave in the superposition, can be derived from the following equation:

$$
c_n=\frac{1}{T}\int_{-t/2}^{T/2}f(x)e^{-12\pi\frac{n}{T}x}dx
$$ (eq:Fourier_series_amplitude)

The approximated signal is called the Fourier series, and is calculated from:

$$
f(x)=\sum_{n=-\infty}^\infty c_n e^{i2\pi\frac{n}{T}x}, x\in[-T/2,T/2]
$$ (eq:Fourier_series)

When we have created our approximated signal, we can calculate the amount of energy (wave amplitude) related to each frequency. The result is a function that dsiplays the energy as a function of frequency. This function is called the Fourier transform:

$$
\hat{f(\k)}=\int_{-\infty}^\infty f(x)e^{-i2\pi\k x}dx
$$ (eq:Fourier_transform)
