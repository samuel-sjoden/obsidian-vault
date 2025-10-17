### Cubic Splines
If you have $N + 1$ data points $$
(t_{0}, y_{0}), (t_{1}, y_{1})\dots(t_{N
}, y_{N})
$$
You can write the data in terms of third order polynomials (cubic splines).
The polynomials will interpolate between pairs of points.
$$
P_{k}(t) = a_{k}(t - t_{k-1})^3+ b_{k}(t-t_{k-1})^2+c_{k}(t-t_{k-1}) + d_{k}
$$
This function and its derivatives are continuous.
$$
\begin{bmatrix}
a_{1} & a_{2} & \dots & a_{N} \\
b_{1}&b_{2}&\dots & b_{N}  \\
c_{1} & c_{2} & \dots  & c_{N} \\
d_{1} & d_{2} & \dots & d_{N}
\end{bmatrix}
$$
A cubic spline is defined with 4N coefficients we will need 4N equations to define a cubic spline.

**Interpolation**
We know that at each data point, the polynomial must correspond to the value at the data point.
$P(t_i) = y_i$

We can make further conditions based on the continuity between the polynomials.  The polynomials must equal their right and left endpoints.

This gives the first 2N equations.

**Continuity**
The endpoints of the cubic splines must be continuous with the next. This gives us another set of equations.
$$
P'(t_{k + 1}) = P'_{k+1}(t_{k+1})
$$
Since we only have this condition on interior points $$
k \neq 0,N + 1
$$
This gives $N - 1$ equations.

The same condition is true for the second derivative $$
P''(t_{k+1})=P''_{k+1}(t_{k+1})
$$
**We have a total of $4N - 2$ equations**
We apply an arbitrary constraint to get the last two equations.

Natural cubic spline condition:
$$
P_{1}''(t_{0}) = 0 ,\qquad P_{N}''(t_{N}) = 0
$$
#### Finalized Equations

$$
P_{1}''(t_{0}) = 6a_{1}(t_{0}-t_{0}) + 2b_{1} = 0
$$
$$
P_{N}''(t_{N}) = 6a_{N}(t_{N}-t_{N-1}) + 2b_{N} = 0
$$
**Example:**
$$
(0,1), (1, 3), (2, 8), (3, 10), (4, 5), (5, -1), (6, -17)
$$
The coefficient matrix $$
\begin{bmatrix}
1  & -2  & 1  & a_{4} & 1  & 1 \\
0  & 3 & -3 & b_{4} & -6 & -3 \\
1  & 4  & 4 & c_{4} & -5 & -14 \\
1  & 3  & 8 & 10 & 9 & -1 \\
\end{bmatrix}
$$
Most of the polynomials have already been found so we are tasked with solving for the coefficients for the $P_4$ polynomial.

$$
d_{4} = y_{4} = 10
$$
$$
P_{4}(t) = a_{4}(t - t_{4})^3 + b_{4}(t - t_{4})^2 + c_{4}(t- t_{4}) + d_{4}
$$
To find the P4 polynomial, we will need to find the P3 and P5 polynomials to solve for the coefficients.

We can now apply the continuity equations and the value equations
$$
P_{4}(t_{3}) = 8 = a_{4}(t_{3}- t_{4})^3 + b_{4}(t_{3}-t_{4})^2 + c_{4}(t_{3} - t_{4}) + d_{4}
$$
$$
P_{4}'(t_{3}) = 
$$

*Don't we have too many constraints? We have 2 continuity equations at each side, and an equivalence relation on each side as well for 3 coefficients*

