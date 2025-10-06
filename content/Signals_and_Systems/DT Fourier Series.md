Recall that periodic functions $x(t) = x(t + T)$ can be represented as a linear combination of complex exponentials. This is the [[Fourier Series]] representation of the periodic function.
$$
x(t) = \sum c_{k} e^{jw_{0}kt}
$$
Complex exponential signals are eigenfunctions of DT LTI systems.
We can approximate with a finite number of terms $N$. We can do this for most signals.
If the signal has finite power our approximation error $\rightarrow 0$ as our $N$ goes to infinity.
We can also guarantee the convergence of the values of the coefficients

#### Gibbs Phenomenon
With finite Fourier approximations, there will be high frequency ringing at sharp discontinuities. 

#### Fourier Series Properties
A function shifted in time does not affect the scaling of the exponentials (the signals are the same) but introduces a phase shift to the power.
$$
x(t - t_{0}) \leftarrow \rightarrow e^{-jw_{o}t_{0}}c_{k}
$$
Scaling a function in time results in higher frequency signals, so the frequencies are scaled.

The magnitude of all of the coefficients
$$
\sum |c_{K}|^2
$$gives the power of the signal. 

>[!question]
>Is the power of the function related to its inner product?

If two signals share the same fundamental frequency they can easily be operated between.

### DT complex exponential signals
In discrete time we write complex signals as $$
x[n] = Cz^n
$$
where $$
n \epsilon \mathbb{Z}
$$
The exponential  signal is when $$
z = e^{j\omega n}
$$
##### Frequency Difference In DT
In CT we have the intuition that our period is $T= \frac{2\pi}{\omega}$ and that with larger $\omega$ the faster our signal will oscillate.

This is not true for  discrete time signals $$
x[n] = e^{j(\omega + 2\pi)n}
$$
$$
= e^{j\omega n}e^{j_{2}\pi n}
$$
which results in the same signal. This means that once the frequency has grown past itself plus 2 pi, the frequency can no longer get any faster. Think of it like the frequency is switching in between the integers, so we cannot see it. So in turn, you get out a slower frequency.

>[!question]
>is the smallest period possible 1 then?

Find the fundamental period of $$
x[n] = \cos{3n}
$$
$$
x[n + N] = \cos{3(n+N)}
$$
$$
x[n+N] = \cos(3n + 3N)
$$
in order for the shifted signal to be equivalent to the original signal, $3N = 2\pi$ which is impossible for N to solve as an integer.
Therefore **the signal is not periodic**

For the signal to be periodic, $$
\omega_{0}N = 2\pi m
$$
$N$ is an integer that solves this equation.
$$
\frac{\omega_{0}}{2\pi} = \frac{m}{N}
$$
Therefore the left hand term must be a rational number.

##### Examples

$$
x[n] = \cos\left( \frac{5\pi n}{6} \right)
$$
$$
\omega_{0} = \frac{5\pi}{6}
$$
$$
\frac{\omega}{2\pi}= \frac{5}{12}
$$
this is a rational so therefore its periodic. It has a fundamental period of 12.

For the harmonics of the signal, we need much fewer complex exponentials because we only need frequencies with pm 2pi

We only need the first $N$ harmonics

>[!question]
>Why no negative terms in the DT case? We previously had signals at the same frequency but negative? This is what allowed us to represent sine functions. Are we just phase shifting our cosines up to pi/2?



$$
x[n] = \sum{c_{k}e^{jk\omega_{0}k}}
$$
The constants out front of the exponents can be found the same as they are in the continuous form. $$
c_{k} = \frac{1}{N}\sum x[n]e^{-jk\omega_{0}n}
$$
Any sum over an interval of length $N$ is acceptable.

### Convergence of DT Fourier Transform

Since the frequency is limited in discrete time, there is no gibb's phenomenon ringing affects.
This indicates that the DT fourier representation converges in its finite dimensional space (we do not need the infinite terms in the infinite dimensional space of the continuous time domain).



See ex 3.12 in textbook

