The magnitude and phase response of the [[Frequency Response]] of a system are often helpful metrics.

The magnitude of the frequency repose can give insight into how the system responds to different frequencies. For [[Filters]], it can determine which signals are passed by the filter and which ones are destroyed.

All im getting out of this is that phase information is important. Removing the amplitude information, the phase encodes the consrtuctive and destructive interference of the signals.

$$
\left| Y(j\omega) \right| =\left| H(j\omega) \right|\left| X(j\omega) \right|
$$$$
\text{phase }Y(j\omega)= \text{phase } H+ \text{phase }X
$$
These are the **Gain** and **Phase Shift** of the frequency response. These can be helpful when filter or using a system, or they can introduce distortion.

### Linear Phase Response
The nicest type of phase response where the phase shift of the signal is directly proportional to the frequency of the signal.

**Example**
$$
\begin{align}
H(j\omega)=e^{ -j\omega t_{0} } \\
\text{phase shift } Y(j\omega)= -\omega t_{0} + \text{phase } X(j\omega)
\end{align}
$$
This produces a shift in the time domain:
$$
y(t) = x(t-t_{0})
$$
### Non Linear Phase Response
If the phase response is non-linear, the signal gets distorted as different frequencies are shifted different amounts.

This is present in things like an RC low pass filter which has a non-linear phase response.$$
H(j\omega) = \frac{1}{1+j\omega RC}
$$
Which has a phase shift that is non-linear with phase.

#### Low Pass Filter
The ideal low pass filter has an impulse response that is acausal:$$
h(t)=\frac{\sin(\omega_{c}t)}{\pi t}
$$
This leads to the notion of buffering an input untill I haved reached the future data. We can only not build a real time system that is acausal. 
$$
H(j\omega)=\frac{1}{1+j\omega RC}

$$
$$
h(t) = \frac{1}{RC}e^{ -t/RC }u(t)
$$
### Step Response
The step response of a filter describes a systems response to a unit step function.
$$
\begin{align}
s(t)=h(t)*u(t) \\
=\int_{-\infty}^{\infty} h(\tau)u(t-\tau) \, d\tau \\
= \int_{-\infty}^{t}h(\tau)   \, d\tau 
\end{align}
$$
The step response of an ideal filter has a ringing behavior as it reaches steady state response because of the high frequency turn on and they slowly settles to a total pass.

> Is there a way to clamp the size of the ripples?
