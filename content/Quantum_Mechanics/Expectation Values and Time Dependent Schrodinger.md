## Expressing State Vectors in Discrete and Continuous Bases

**Discrete Basis**
Like a Cartesian vector. There are basis vectors each with weights

**Continuous Basis**
Just like discrete, but now an integral because each $\psi(x)$ represents a weighting for $(x, x +dx)$


If the vectors are in the same basis, basic vector operations like addition still apply

$$\braket{ \phi | \psi }$$$$
\bra{\phi} = \int dx \phi^*(x)\bra{x}  \qquad \ket{\psi} \int dx \psi \ket{x}
$$ The product of two integrals is the double integral of the product.
$$\iint dx'dx\phi^*(x')\psi(x)\braket{ x' | x }$$$$
\braket{ x' | x } = \delta(x - x')
$$
$$\int dx \phi(x)^*\psi(x)$$
## Expectation value

$$\bra{\psi} \hat{X}\ket{\psi} $$
$$\hat{X}\ket{ \psi}  = \int dx \psi \hat{X}\ket{x} $$
The operator can move through the integral until it reaches the ket. Since psi is in the x basis the result of the operator is trivial.

$$\int dx \psi x|x>$$
The operator took a ket and spat out a new ket. We can then take an inner product with our new ket and the original ket.

$$\iint dxdx' \psi(x)^*\psi(x)x<x'|x>$$
The result of an inner product is a scalar value.

### Summary

If we want to write a ket in an x-basis we can write it in terms of its functions of position
$$|\psi> = \int dx \psi(x) |x>$$
If we were trying to find the expectation value of momentum in the x-basis, we have to convert the $\hat{P}$ operator to the x basis

$$<\psi|\hat{P}| \psi> = [\int dx \psi^*d/dx \psi](-i)\hbar$$
Now we can easily change between writing things as vectors and as functions. When working with functions we have to make sure we are staying in the basis of the functions.

#### Example
Infinite Square well $0 < x < 1$ with an initial state $|\psi(t=0)> = \frac{1}{\sqrt{2}}(|\phi_1> + |\phi_2>)$

Expectation value -> if I repeat an experiment with the same initial state what is the average value I would find.

Or

$$<\hat{P}(t)$$
What would the average value of momentum be at different times.
The momentum oscillates as it evolves in time.

**Step 1.** Write the state of the particle at a later time

Easy since the state is written in the eigenvectors of the Hamiltonian.

$$\psi(x,t) = (e^{-iE_1t/\hbar}/\sqrt{2}(\psi_1 + e^{-i\delta E t/\hbar}\psi_2)$$
Writing it in function notation.

To get to function notation we took an inner product with the x basis vector which collapsed the integrals into a sum of delta functions simply giving the function.

$$<\hat{P}(t)> = \int dx \psi^*\psi_x * (-i\hbar)$$
The global phase cancels with the conjugate leaving only the relative phase.
The remaining difficulty is in evaluating this integral.

Only the cross terms will result in time dependence.

#### Aside: Computing the integrals

**Using integration by parts**
$$\int dx d/dx (f g) = \int dx f d/dx g + \int dx g d/dxf$$
We can leverage that the wavefunctions must be zero at the boundaries (for infinite square well and most other wavefunctions) 

We can use this to immediately cancel the non-cross terms if they are both real valued.

if $f = g = \phi_1$
left side is zero because of boundary, making the right side equal to each  other

$$
  
$$