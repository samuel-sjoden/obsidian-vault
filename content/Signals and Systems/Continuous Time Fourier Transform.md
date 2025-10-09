### Convergence of Fourier Transforms
Just as the condition for the [[Fourier Series]] representation of periodic continous time signals, if the signal has finite energy, the fourier transform is finite. The energy of the error function will additionally be zero.
$$
\int_{-\infty}^{\infty} \left| x(t) \right| ^2 \, dt < \infty
$$
If we do not contain all high frequency components, we will see gibbs phenomenon.

**Stronger Conditions**
If the signal is 
- absolutley integrable
- has a finite number of maxima and minima on a finite interval
- has a finite number of discontinuities within a finite interval
Then the [[Fourier Transform]] will converge to $x(t)$ where it is continous and will be the average value on the discontinuity.

### Periodic Signals
An interesting example: all periodic signals are not square integrable (we cannot normalize them). Since the above conditions are only sufficent and not necesarry, we can still conjure fourier series representations by using the delta function.

> [!Example]
>  $$
 X(j\omega)= 2\pi\delta(\omega-\omega_{0})$$
  > This represents a single periodic signal with frequency $\omega_{0}$. The delta function is large enough that it provides enough energy for the signal to be seen. 
  > $$
 x(t) = \frac{1}{2\pi}\int_{-\infty}^{\infty} 2\pi\delta(\omega-\omega_{0}) e^{ j\omega t }\, d\omega $$
 > $$
 = e^{ j\omega_{0}t }$$
 > which is just a simple complex periodic signal. The fourier series representation would have coefficents
 > $$
 c_{n} = \begin{cases}
c_{1}=1 \\
c_{n\neq_{1}} = 0
\end{cases}$$

We have just seen that periodic signals are represented as delta functions in the fourier transform. A superposition of periodic signals is a sum of delta functions at various frequencies $\omega$. 

### Duality Property
There are symmetries between the time domain signals and frequency domain signals. The fourier transform of the function $$
x(t) = u(T_{1}-t) -u(t-T_{1})
$$
is a little box. The frequency domain representation of this signal is a $sinc$ function. If we work with a square wave in the frequency domain, like a the frequency response of a low pass [[Filters]], the impulse reponse is a sinc function in time.
$$
\text{sinc}(\theta \pi)=\frac{\sin(\pi \theta)}{\pi \theta}
$$

> [!Example]
>  What is the fourier transform of 
>  $$
 x(t) = e^{ -at }u(t)$$
 > Where $\mathrm{Re}(a)>0$
 > $$
X(j\omega)= \int_{-\infty}^{\infty} e^{ -at }e^{ -j\omega t } \, dt
$$

$$
 = \int_{-\infty}^{\infty} e^{ -(a+j\omega )t } \, dt=\frac{1}{a+j\omega}$$
 
$$
x(t)= e^{ -2\left| t-1 \right|  }
$$
which can be decomposed into 
$$
x(t) = e^{ -2(1-t) }u(1-t) + e^{ -2(t-1) }u(t-1)
$$
And we just found the fourier transform for an arbitrary $a$ who's real part is larger than $0$.
### Properties of Fourier Transform
A shift in time introduces a phase delay in the fourier transfrom. We have to move all of our sines and cosines forward and backward a bit
$$
x(t-t_{0}) \to e^{ j\omega_{0}t_{0} }X(j\omega)
$$
#### Time scaling
When you compress things in time, the frequency of the signals building the signal has increased. When I compress things in the time domain, I spread out in the frequency domain, since higher frequency components are now needed.
z