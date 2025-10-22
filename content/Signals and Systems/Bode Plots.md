Bode plots are useful plots to describe the [[Magnitude and Phase Response]] of a systems [[Frequency Response]]. One of the plot maps the power of the signal $\to$ $\left| H(j\omega) \right|^{2}$, but usually on a log10 scale.

## Plotting First Order Systems
### Magnitude Plot
1. Find the magnitude of the frequency response
2. Apply $20\log_{10}\left| H(j\omega) \right|$
3. Apply the bode approximation at the pole $\to$ gives two lines with a meeting point at $\frac{1}{\tau}$, the location of the pole

### Phase angle plot



## Second Order Systems

>[!Example]
> What is the frequency response of the [[Systems Described By Differential Equations|System described by a differential equation]]
>  $$
 y'' + 2\zeta \omega_{n}y' + \omega_{n}^{2}y= \omega_{n}^{2}x$$
 > Find the frequency response by taking the [[Fourier Transform]] of the equation.
 > $$
 \begin{align} \\
 H(j\omega) = \frac{\omega_{n}^{2}}{(j\omega)^{2}+2\zeta \omega_{n}(j\omega) + \omega_{n}^{2}} \\
 \end{align}$$
 > Finding the poles in the denominator require the polynomial to be factored. Nature of the poles in the denominator depend on $\zeta$.
 >  Case $\zeta=1$:
 >  $$
 H(j\omega) = \frac{\omega_{n}^{2}}{(j\omega+\omega_{n})^{2}}$$
 