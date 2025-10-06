Homework 3                        Samuel Sjoden                      PHYS 304

>[!Question]
> Consider the 1D Potential
> $$
V(x) = \begin{cases}
 -V_{0} + \lambda \delta(x) & |x| < \frac{L}{2} \\
 0  & |x| \geq \frac{L}{2}
\end{cases}
>$$
Where $V_{0}>0,L>0,\lambda\geq0$

## A)
>[!Part a)]
>a) Write piecewise forms for all bound-state wavefunctions and state the matching conditions they must satisfy at $x=\pm L/2$ and at $x=0$. Include the derivative jump condition at the delta and reduce the problem to transcendental conditions for even and odd cases (do not solve them).

First I will be splitting the well into four regions. 
- Region A - Left Side outside of the well
- Region B - Left half inside of the well
- Region C - Right half inside the well
- Region D - Right side outside of the well
![[IMG_0081.jpg]]

Since the potential is symmetric, I will be leveraging this by solving one side of the well and imagining either an odd or even counterpart on the other side of the well reflected about $x=0$
$$
-\frac{\hbar^2}{2m}\left( \frac{\partial^2}{\partial x^2}\psi \right) + V(x)\psi = E\psi
$$
Then solving a peicewise solution to make the ODE constant coefficient.
##### Region A
$$
\begin{align}
\psi'' + \frac{2m}{\hbar^2}(E)\psi=0 & \quad \kappa^2=\frac{2m|E|}{\hbar^2}\\
\psi''-\kappa^2\psi=0 \\
r^2-\kappa^2=0 \\ \\

\boxed{\psi=Ae^{-\kappa x} + Be^{\kappa x}}
\end{align}
$$
This solution will have the following boundary conditions
$$
\begin{align}
\lim_{ x \to -\infty } \psi(x) &= 0 \\
\lim_{ \epsilon \to 0 } \psi( -{L}/{2} - \epsilon) &= \psi( -{L}/{2} + \epsilon) \\
\lim_{ \epsilon \to 0 } \psi'( -{L}/{2} - \epsilon) &= \psi'( -{L}/{2} + \epsilon)
\end{align}
$$
##### Region B
$$
\begin{align}
\psi'' -\frac{2m}{\hbar^2}(-V_{0}-E)\psi=0 &\quad k^2=\frac{2m(V_{0}+E)}{\hbar^2} \\ \\

\psi''+k^2\psi=0 \\ \\

\boxed{\psi = C\cos(kx) -D\sin(kx)}
\end{align}
$$

The boundary conditions at the delta spike in the well require some additional care. The continuity condition still applies, which will be covered by the assumption that the wavefunction is even/odd symmetric. The derivative across requires special attention.

Integrating the Schrodinger equation at $x=0$, the resulting boundary condition for the derivative of the wavefunction at $x=0$ is 
$$
\psi'(0) = \frac{m\lambda}{\hbar^2}\psi(0)
$$

Now we have enough information to build the wavefunction. The solutions can be separated into odd solutions and even solutions.
#### Odd Solutions
Odd states go to zero at the location of the delta spike, so they are not impacted by the delta in the center of the well.

Assuming then that $C=0$ so that the solutions are non-shifted sinusoids,
I reached a transcendental relation from the continuity and derivative B.C.'s at the edge of the well.
$$
\boxed{\tan(kx)=-\frac{k}{\kappa}}
$$

Solving this relationship can find the energy of each state. The odd solutions to this FSW are then: 
$$
\boxed{\psi(x) = \begin{cases}
Be^{\kappa x}  & x \leq -L/2 \\
D\sin(kx) & -\frac{L}{2} <x\leq 0 \\
D\sin(kx)  & 0 < x < \frac{L}{2} \\
-Be^{-\kappa x}  & x \geq \frac{L}{2}
\end{cases}}
$$

#### Even Solutions
Since the even solutions do not go to zero at the delta, some additional work is required. To satisfy the derivative condition at $x=0$, a sum of sine and cosine will be used as the guess. The result will then be mirrored across $x=0$ to give the even solution.

$$
\begin{align}
1.&\qquad Be^{-\kappa L/2} = C\cos\left( \frac{kL}{2} \right) + D\sin\left( \frac{kL}{2} \right) \\
2.&\qquad B\kappa e^{-\kappa L/2} = Ck\sin\left( \frac{kL}{2} \right) - Dk\cos(kx) \\
3.& \qquad -Dk=\frac{m\lambda}{k\hbar^2}
\end{align}
$$
Then rearranging and making the substitution $\alpha =\frac{m\lambda}{\hbar^2}$ I reach the transcendental relation:
$$
\boxed{\tan\left( \frac{kL}{2} \right) = \frac{k(\kappa-\alpha)}{k^2 + \kappa \alpha}}
$$

![[QMHW3lambdabig.png]]
The solutions for the even cases will then have the form:
$$
\boxed{\psi(x) = \begin{cases}
Be^{\kappa x}  & x\leq -\frac{L}{2} \\
C\cos(kx) - D\sin(kx)  & -\frac{L}{2} < x \leq 0 \\
C\cos(kx) + D\sin(kx)  & 0 < x < \frac{L}{2} \\
Be^{-\kappa x}  & x\geq \frac{L}{2}
\end{cases}}
$$
## B)
>[!Part B]
> On a single graph, hand-sketch (qualitatively) the lowest bound-state wavefunction for three cases: $\lambda \rightarrow 0$, $\lambda> 0$, $\lambda \rightarrow\infty$. Label any nodes.

##### $\lambda \rightarrow 0$
When $\lambda$ goes to zero, the transcendental relation just becomes the typical finite square well relation.
$$
\tan(kx)= \frac{\kappa}{k}
$$
So the ground state is just a cosine.

![[IMG_0084.jpg]]

##### $\lambda>0$
There is a small downwards cusp at $x=0$. With larger $\lambda$ the cusp grows as the energy of the ground state increases (higher angular frequency)

![[IMG_0083.jpg]]


##### $\lambda\rightarrow \infty$
In the limit as lambda goes to infinity, looking at the RHS of the transcendental relation.
$$
\lim_{ \alpha \to \infty } \frac{k\left( \frac{\kappa}{\alpha} - 1 \right)}{\frac{k^2}{\alpha} + \kappa} = -\frac{k}{\kappa}
$$
Which is identical to the odd solution. The energy has risen enough that it now matches the second lowest bound state. A node forms at $x=0$ and the angular frequency of this solution matches that of the first sinusoid solution.
![[IMG_0082.jpg]]


## C)
>[!Part C]
> Describe qualitatively how the second-lowest bound-state wavefunction is affected (or not) by $\lambda$

Since the second lowest state reaches $\psi(x=0) = 0$, it is unaffected by the delta spike in the middle of the well. The odd solution says that the particle will never be there, so it never interacts with that region with the delta.

## D)
>[!Part D]
> As $\lambda$ increases, does the ground-state energy move up or down? Argue your answer qualitatively based on the change in shape of the wavefunctions within the well.

As lambda increases, a higher angular frequency is required to form the cusp at $x=0$ in the limit $\lambda \rightarrow\infty$ the ground state energy is brought up high enough that a node forms forms.

## E)
>[!Part E]
> In the limit $\lambda \rightarrow \infty$ , explain why the lowest two bound-state energies become equal. Describe the physical picture that leads to this conclusion.

As a cusp in the wavefunction grows and the angular frequency increases, once lambda grows to infinity, a node has formed and now the angular frequency has grown large enough that it matches the odd energy state. The area of the delta function has grown so large that the particle can not exist there (the node) and now it can only exist in the right and left sides of the wall. This results in degenerate even and odd bound states.
