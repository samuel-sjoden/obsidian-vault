Used for [[Neural Nets]] that make class based classifiers.
One hot encoding creates a state vector of orthogonal eigenstates of the output space. When the neural network takes a measurement it produces a probability of the state vector being in some state.
Example:
$$
\begin{align}
\text{Classes}\{a,b,c\dots,z \} \\
\text{Hot vector for: a}=\begin{bmatrix}
1 & 0 & 0 & \dots & 0 
\end{bmatrix}
\end{align}
$$

This allows us to have a measure of distance between state vectors, which helps us build a loss function when [[Training Neural Nets]].



