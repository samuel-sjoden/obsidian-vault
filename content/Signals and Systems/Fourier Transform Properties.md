Some of the key properties of the fourier transform that this section will cover is [[Convolution]], Duality, and Dilation.

>[!Fizz fact]
> A convolution with $\frac{1}{t}$ is a hilbert transform

## Duality of Fourier Transform
There are many symmetric relations betweem frequency and time representations of signals. This relates to that both forward and inverse transforms are nearly identical.

## Convolution Property of The Fourier Transform
Since we are particlularily interested with LTI systems, look at how complex exponentials are eigenfunctions of these systems.

That is if a complex exponential (or superpostion of) goes into a LTI system it will come out at the same frequency but scaled by a complex constant.

If an LTI system has an input function $X(j\omega)$ then the output will be:
$$
y(t) = \int_{-\infty}^{\infty} x(\tau)h(t-\tau) \, d\tau
$$
To get $X(j\omega)$ into the time domain, an inverse fourier transform is required.
$$
y(t) = \int_{-\infty}^{\infty} \left[ \frac{1}{2\pi}\int_{-\infty}^{\infty} X(j\omega)e^{ j\omega(t-\tau) } \, d\omega  \right] h(\tau) \, d\tau
$$
Asumming that the inner integral converges, we can swap the order of integration:
$$
y(t)= \frac{1}{2\pi}\int_{-\infty}^{\infty} X(j\omega)e^{ j\omega t } \int_{-\infty}^{\infty} h(\tau)e^{ -j\omega \tau } \, d\tau \, d\omega
$$
And seperating all of the elements that are independent of $\tau$.
We know that the solution to the integral in tau is actually the frequency repsonse of the LTI system, so we carn rewrite it as:
$$
y(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty} X(j\omega)H(j\omega)e^{ j\omega t } \, d\omega
$$
Which is an inverse fourier transform of $XH$ into time. So we can make the inference that convolution in the time domain is multiplication in the frequency domain.
$$
\boxed{\begin{align}
y(t)= x(t)*h(t) \\
Y(j\omega)=H(j\omega)X(j\omega)
\end{align}}
$$
This simplifies the solution becasue we dont need to do a weird sum of all component from all time of $x$ and $h$.

#### Filters
In the context of [[Filters]], if we know the frequency reponse of the filter, we can quickly determine the output of the system in $j\omega$ domain by multiplying the input signal and frequency response.

>[!Example]
> $$
 x(t) = \frac{\sin(\omega_{0}'t)}{\pi t} \leftrightarrow X(j\omega)= \begin{cases}
 1, & \left| \omega \right| < \omega_{0} \\
 0,  & \left| \omega \right| \geq \omega_{0}
\end{cases}$$
> We need to know the frequency representation of $x(t)$, which is just a rectangle. The product of two rectangles is a scaled rectangle with the width of the smaller rectangle. 
> Since $Y(j\omega)$ is  a rectangle, we know that the time evolution is another $\text{sinc}$ function
> $$
 y(t)=\text{sinc}(\omega^*t), \quad \omega^*=\text{min}\{ \omega_{0}, \omega_{0}' \}
$$

>[!Example]
> $$
x(t) =e^{ -t }u(t) \to y(t)=\frac{1}{2}e^{ -\left| t \right|  }$$
> Find the impulse response:
>  $$
H(j\omega)=\frac{Y(j\omega)}{X(j\omega)}$$

## Multiplication Property
For the other side of the dualty, multplication of signals in the time domain is a convolution of signals in the frequency domain.

##### Application - Modulation
When converting lower frequency signals into high frequency signals for transmission we need to do a conversion.

A carier signal which is a complex exponential at some carier frequency is multiplied by the data signal.
$$
e^{ j\omega_{c}t }
$$
In the frequency domain, the signal is a convolution with the carier signal, which is a delta function.
$$
Y(j\omega)=\frac{1}{2\pi}\int_{-\infty}^{\infty} X(j\theta)C(j(\omega-\theta)) \, d\theta
$$
$$
Y(j\omega)=X(j(\omega-\omega_{c}))
$$
Convolutions with deltas move it to where the delta is. So we have just shifted the signal from its an original range to a high frequency range. Then to downconvert, the signal is multiplied by the negative.

> In reality we cannot send an 'imaginary signal' so to get around this, the signal is sent in two components, the real and imaginary one.

###### Modulation For Filters
The same frequency shifting techniques can be used when things like high frequency filtering is required, but it is physically difficult to build one with a center frequency at the desired range. 