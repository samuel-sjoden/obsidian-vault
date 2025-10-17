The condition number of a nonsignular square matrix $A$ is:
$$
\text{cond}(A)= \left| \left| A \right|  \right| \left| \left| A^{-1} \right|  \right|
$$
Which is defined with the [[Operator Norm]]
If $\text{det}(A)=0 \implies \text{cond}(A)=\infty$
The condition number describes how large the fluctuations in the output can be.
It can be visualized by inputing a unit vector in all directions, (the unit hypersphere) and comparing the largest stretch of the unit vector, and the largest squish.

$$
\text{cond}(A)=\frac{\text{maximum stretch}}{\text{minimum stretch}}
$$
It follows intuitivley that $$
\frac{\left| \left| \Delta x \right|  \right| }{\left| \left| x \right|  \right| }\leq \text{cond}(A)\frac{\left| \left| \Delta b \right|  \right| }{\left| \left| b \right|  \right| }
$$
the relative change in $x$ , the output, will at most be the relative change in the input scaled by the condition number.