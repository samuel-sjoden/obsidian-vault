[[Fourier Series]] is used to represent a superposition of periodic signals with the synthesis equation:
$$
x(t)=\sum_{k=-\infty}^{\infty} c_{k}e^{ jk\omega t }
$$
This a sum of a signal with fundamental frequency $\omega_{0}$ and its harmonics could be form, with a countably infinite sum could represent periodic signals.

To represent aperiodic signals, we need the fourier transform. It is a further generalization of the fourier series. 

**Inverse and Forward Fourier Transform**
$$
\boxed{x(t)=\frac{1}{2\pi}\int X(j\omega)e^{ j\omega t } \, d\omega }
$$
$$
\boxed{X(j\omega)=\int x(t)e^{ -j\omega t }dt}
$$
Is an unaccountably infinite sum of different frequencies. 

### Going From Series to Transform
The fourier series coefficients can be visualized as a discrete time signal, which do not have to be a periodic function. One could imagine a smooth function connecting the coefficients to give a continuous expression $c_{k}=f(\omega)$

If we imaging an aperiodic signal and then create its periodic extension. 
We can represent this now periodic signal with a fourier series with fourier series $c_{k}$. 

to find the coefficients
$$
c_{k}=\frac{1}{T}\int x(t)e^{ -jk\omega_{0}t } \, dt
$$
But since we are only looking at it on one period, we can use the original aperiodic signal. We can defined the aperiodic signal to be zero outside of the region we are looking at, we can go from $-\infty$ to $\infty$. 
$$
c_{k}=f(\omega)=X(jk\omega_{0})=\int x(t)e^{ -j\omega t } \, dt 
$$
We can then go ahead an substitute the function that we made as the coefficients of the fourier series. 
$$
\tilde{x}(t)=\sum_{k=-\infty}^{\infty} \frac{1}{T}X(jk\omega_{0})e^{ jk\omega_{0}k }
$$
$$
\tilde{x}(t)= \frac{1}{2\pi}\sum_{k=-\infty}^{\infty} X(jk\omega_{0})e^{ j\omega_{0}k }\omega_{0}
$$
Then we can imagine the period of our aperiodic function $T\to \infty$ and therefore $\omega_{0}\to 0$ 
$$
\tilde{x}(t)=\frac{1}{2\pi}\int X(j\omega) e^{ j\omega t }\, d\omega
$$
Where the area elements of $X\omega_{0}$ has become infinitesimally small and summed up.

## Fourier Transform
The [[Frequency Response]] is just the fourier transform of the impulse response of an LTI system.

$$
H(j\omega)=\int h(\tau)e^{ -j\omega \tau } \, d\tau
$$
>[!Example]
>![[Pasted image 20251002151447.png]]
> $$
X(j\omega) = \int \cos(\pi t)e^{ -j\omega t } \, dt 
$$

$$X(j\omega) = \frac{\sin(\omega)}{\pi-\omega}-\frac{\sin(\omega)}{\pi+\omega}$$



> In the context of signals, we need the signals to be finite in energy for the fourier transform to converge