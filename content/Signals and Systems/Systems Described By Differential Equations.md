## Constant Coefficent ODE
If the system can be described in this form:
$$
\sum_{k=0}^{N} \alpha_{k}\times \frac{d^{k}y(t)}{dt^{k}}=\sum_{k=0}^{M} \beta_{k}\times \frac{d^{k}x(t)}{dt^{k}}
$$
Where $y$ is the signal that is output and $x$ is the input signal.
To give the system some initial conditions, we assume that the system is intially at rest, and the system is [[Causal]].

If we were interested in the [[Frequency Response]] of the system, we can take the [[Fourier Transform]]  of the linear superposition of signals.

We can use the differentiation [[Fourier Transform Properties]] to only require the fourier transform of $y,x$.

$$
Y(j\omega)\sum_{k=0}^{N} \alpha_{k}(j\omega)^{k}=X(j\omega)\sum_{k=0}^{M} \beta_{k}(j\omega)^{k}
$$
The we can easily identify the frequency response:
$$
H(j\omega)=\frac{Y(j\omega)}{X(j\omega)}
$$
