Instead of a singular position coordinate we now have a vector representing a point in space. Some important [[Commutators]] relationships between elements are:
$$
 \begin{align} \\
\left[ r_{i},r_{k} \right] =0
\end{align}
$$
The schrodinger equation will now have an additional components. The actual vector usually does not matter but instead the norm of the vector. 

The wavefunction and energy are now functions of three coordinates. To seperate the equation into something more easy to analyze we perform [[Seperation of Variables]] to see if we can seperate the equations.

### Seperating the Spacial Dimensions
We require that:
$$
V(x,y,z) = V_{x}(x)+V_{y}(y)+V_{z}(z)
$$
The potential needs to be able to be represented as a sum of functions depending only on one spacial variable. This limits the potentials in 3D that we can solve with the seperated equations.

>[!Remember]
> To use the seperated equations, the potential must be seperable a sum of functions dependent only on one spacial variable

Try a solution:
$$
\psi(x,y,z) =\psi_{x}(x)\psi_{y}(y)\psi_{z}(z)
$$
When you perform this seperation with three variables, you get to a point where:
$$
f(x) = \text{constant} + (f(y,z))
$$
This shows that we cannot have dependence on any of the variables. This result then tells us that this is equal to its own constant. The new thing here is that the constant. Since the setup looks different in $x,y,z$ the constant is unique for each equation.


> is there an upper limit for energy?


> how to write multivariable function with multiple kets?

> if you have a degenerate eigenvalue, how does the particle determine what state its in? 

> is non-normalizable a sufficent condition to rule out solutions?

### Degeneracy
Eigenstates that have the same energy. Arise from symmetries in the potential. If the box had with a height b and length c, we would not have degenerate eigenstates.

