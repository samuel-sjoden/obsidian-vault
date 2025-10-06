The free particle solutions are solutions to the Schrodinger equation when the potential term is always zero. They don't have the same conditions as bound states which must go to zero as you get really far out.

$$
-\frac{\hbar^2}{2m}\left( \frac{d^2}{dx^2} \right)\psi=E\psi
$$
Say we have a measurement apparatus for a particle neat $x=0$ and we have accuracy $\sigma$. After measuring the location of the particle, we have given the particle a wavefunction of a Gaussian related to the accuracy of the measurement device. The wavefunction is a Gaussian because of the uncertainty in the measurement. 

Now we are interested in the momentum.
$$
\bra{\psi(t=0)} \hat{P}\ket{\psi(t=0)}
$$
$$
\int_{-\infty}^{\infty} \alpha e^{-(x/2\sigma)^2}\left[ -i\hbar \frac{d}{dx} \right] \alpha e^{-(x/2\sigma)^2}\, dx 
$$
Integrating two even functions times an odd function and integrated over a symmetric domain which ends up being zero.
This makes sense because we just measured the localized particle and we know that it is not moving.

What about in the momentum basis?

$$
\ket{\psi} = \int \phi (p) \ket{p}  \, dp
$$
This function describes the weighting of each possible momentum.
$$
\braket{ p | \psi } =\phi
$$
If we knew this relation
$$
\bra{\phi} \hat{P}\ket{\phi} =\int_{-\infty}^{\infty} \phi^*p\phi \, dp
$$
We know what the momentum eigenvectors look like in the x-basis.
$$
\ket{p} = \frac{1}{\sqrt{ 2\pi \hbar }}\int dxe^{ipx/\hbar}\ket{x}
$$

Then we can evaluate the integral associated with the inner product
$$
\braket{ p | \psi }
$$
This inner product moves us from the x basis into the p basis by measuring the weighting of each eigenvector of p in the x basis to give a function of weighted basis functions in the p basis.
The expectation value remains to be zero. This means that we are equally likely to find the particle with negative and positive momentum.

$$
\phi(p) = \beta e^{-(p\sigma/\hbar)^2}
$$
The resulting wavefunction in the p basis is now expanding with sigma. This is the Heisenberg uncertainty principle since the more localized our measurement is in position space, the less defined the momentum is although expectation value remains the same. (at $t=0$)

In the free particle case, where there is no potential energy, the eigenvectors of the p basis are the same eigenvectors for the energy basis. 

>[!Question]
> Is the exponential term he added a scaling factor for energy? 
> If our basis functions remain the same, we do not have to perform a transform

>[!Question]
> When we have wavefunctions in multiple bases, do we need a common basis?

This result would tell us that its time evolution would rapidly spread the Gaussian out 


A free particle cannot be represented by a single plane wave with definitive momentum and energy. If the momentum and energy are known certainly [[Heisenberg's Uncertainty Principle]] tells us that we can have absolutely no certainty about the position and time of the particle.

>[!Question]
> How do plane waves have well defined momentum and energy?

**A Plane Wave**
$$
\boxed{\Psi(x,t) = A_{-}e^{-i(kx + \omega t)} + A_{+}e^{i(kx - \omega t)}}
$$

A plane wave solution is not normalizable.
$$
\int_{-\infty}^{\infty} \Psi\Psi^* \, dx = |A_{\pm}|^2\int_{-\infty}^{\infty} 1 \, dx
$$
So our issue is that we cannot have a free particle with definitive momentum and energy. So, we represent free particles as wave packets.

>[!Question]
> Why are wave packets special?

## Wave Packets
Wave packets are a weighted sum of different energy/momentum states that sum to produce a wavefunction. This makes them normalizable and ensure that the free particle does not have deterministic momentum and energy.

It is a group of waves at slightly different wavelengths.