### LTI Systems and Time Domain POV
The sifting property tells us that all signals can be expressed as a sum of weighted delta functions over the space.

Since complex exponentials are the eigenfunctions of LTI systems we can find the frequency response of a signal which describes the weight assigned to each complex exponential. 

It is a convolution $$
x(t) = e^{j\omega t}
$$
$$
x(t)*h(t) = \int e^{j\omega t}e^{-j\omega \tau}h(\tau)d\tau = e^{j\omega t}H(j\omega)
$$
### Classification
We will be working in the domain of LTI filters for convenience and how common they are.

$$
H(j\omega) \begin{cases}
1,  & |\omega| \leq \omega_{c} \\
0,  & |\omega| > \omega_{c}
\end{cases}
$$
This describes a filter that only passes signals within the cutoff frequency, as a low pass filter. It does not scale or shift the passed signals.

Filters can be used to amplify and shape signals, attenuate signals, and shift signals in time. Filters apply their frequency response $H(j\omega)$ and modify the fourier coefficients of the input signal.

**Frequency Shaping and Frequency Selection** only depend on the magnitude of the frequency response $|H(j\omega)|$.
**Frequency Shaping** change the phase of parts of the signal. A delay system is an example of that.

>[!fizz fact]
> LTI Filters never change the frequency of the input signals. They only scale the Fourier coefficients of the Fourier series of the input function.

>[!Example]
$$
h(t) = \delta(t-t_{0})
$$
$$
H(j\omega) = e^{-j\omega t_{0}}
$$
This is the frequency response of a delay system. It is an "all pass filter".

>[!Example]
> **Moving Average**
> A moving average is a type of low pass filter of the form
$$
y[n]=\frac{1}{2M+1}\sum_{i=-M}^{M} x[n+i]
$$
The impulse response of this filter is 
$$
y[n]=\frac{1}{2M+1}\sum_{i=-M}^{M}\delta[n+i]
$$
Which is a train of deltas from $-M$ to $M$ each with area $\frac{1}{2M+1}$
> Since this is a filter we are interested in the frequency response of the filter which we fill have to do a [[Fourier Transform]] to find.
> $$
H(j\omega)= \sum_{n=-\infty}^{\infty} e^{ -j\omega n }h[n]
$$


Some types of frequency selective filters are high pass, low pass and band-pass.

>[! Fizz Fact]
>The decibel is a measure of power ratio from input output.
> $$
10\log_{10}(|H(j\omega))|^2)
$$

#### Frequency Shaping Filters

These types of frequencies do not eliminate any frequencies but change their strength. An equalizer is an example of this. Like when I want to turn up my bass, I am increasing the amplification of lower frequency signals.

### Filters in Practice
An example of a low pass filter is a low pass RC circuit. It is an LTI system. It can be modeled with a constant coefficient differential equation.

$$
\text{Input } v_{s} = e^{j\omega t} \qquad \text{Output } v_{c} = H(j\omega)v_{s}
$$
Where $$
i_{r} = \frac{v_{s} - v_{c}}{R}
$$
$$
i_{c} = \frac{Cd(v_{c})}{dt}
$$
Solving this equation we find that $$
H(j\omega) = \frac{1}{1-j\omega RC}
$$
Plotting the frequency response you can see that it is a low pass.
Making the RC product larger makes the frequency cutoff much sharper at the cost of its step response. 

Making the filter more selective in frequency, it becomes slower in time. The trade-off between the frequency and time is actually a instance of the [[Heisenberg Uncertainty Principle]]

## DT Filters
There are two main categories of filters:
- infinite impulse response
- Finite impulse response

### Infinite Impulse Response
>[!Example]
> Consider the system with an infinite impulse response
>$$
h[n] = a^n u[n]
$$

If we hold $|a| < 1$ we can make a high pass and low pass filter depending on the sign of a. This impulse response decays but never reaches zero

### Finite Impulse Response
The impulse response of the system eventually reaches zero.
Unstable systems cannot have a finite impulse response.


