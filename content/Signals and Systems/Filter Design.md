> [!Naive causal lowpass filter:]
$$
h_{trunc}(t) = h(t)u(t)=\begin{cases}
\frac{\sin(\omega_{c}(t-\alpha))}{\pi(t-\alpha)} &  t >0\\
0 & t<0
\end{cases}
$$
To find the frequency response of this system we would have to do perform convolution of the two frequency domain signals $H(j\omega)$ and $U(j\omega)$

This filter does not perfectly attenuate the signals it is filtered out. Often to meaure how well a filter attenuates a signal a log scale is used to show the magnitude of the signal. This is done in the magnitude part of a [[Bode Plots| Bode Plot]]. 