What does it mean for $\Phi$ to be "single valued"
In class he showed half integer values of $l$. Why is expectation value never a half integer?
More division by zero?

Differential equation with imaginary coefficents

If I apply the $\hat{L}_{\pm}$ operator to the eigenfunction $Y_{ll}(\theta,\phi)$ this means that $m$ is maximized. When I apply the sum of $\hat{L}_{x},\hat{L}_{y}$ it means that since all of my angular momentum is in the $z$ direction. No. Why do I know that their sum must be zero? $(\hat{L}_{x} + i\hat{L}_{y})Y_{lm_{max}}$. Is $\hat{L}_{+}$ a ladder operator? I thought that $\hat{L}_{z}$ was the ladder operator thing. Yeah no it is an upwards ladder operator on the $\hat{L}_{z}$ eigenstate.

$\hat{L}^{2}$ must still $>\hat{L}_{z}^{2}$ otherwise then we would know with absolute certainty that $\hat{L}_{y},\hat{L}_{x}$ are $0$. 
> Is there a way to explain this not with uncertainty principle?

> [!Question]
>  I have no clue why the states have to be integers and especially half integers

Say that $\bra{\theta \phi}\ket{l,m}=Y(\theta, \phi)$
From the discussion about [[Angular Momentum]], we previously knew that:
$$
\begin{align}
\hat{L}^{2}Y(\theta,\phi)=\hbar^{2}l(l+1)Y(\theta,\phi) \\
\frac{1}{\Theta}\left[ \frac{1}{\sin \theta}\times \frac{d}{d\theta}\left( \sin(\theta)\times \frac{d\Theta}{d\theta} \right)  \right] 
\end{align}
$$
We can write the $L$ operators in terms of function notation in position space and then we can generate a differential equation which we will again assume to be seperable $Y(\theta, \phi)= \Theta \Phi$.  The solution to the differential equation in $\phi$ makes $\Phi$ an eigenfunction of $\hat{L}_{z}$ 