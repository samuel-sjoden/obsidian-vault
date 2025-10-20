## Building an Orthogonal Basis of A Subpace $U$
If there is a $U$ represented by a basis that is not necesarrily orthogonal to each other, we can build a basis by finding the orthogonal projections of each other
$$
\begin{align}
v_{1}=u_{1} \\
v_{2}=u_{2}-\text{proj}_{v_{1}}u_{2} \\
v_{3}=u_{3}-\text{proj}_{v_{2}}u_{3}-\text{proj}_{v_{1}}u_{3} \\
\dots \\
v_{m}=u_{m}-\text{proj}_{v_{1}}u_{m} - \dots-\text{proj}_{v_{m-1}}u_{m}
\end{align}
$$
> [!Question]
> If my spanning set is not orthogonal, are the vectors still linearly independent?

>[!Question]
> Why do we need an orthogonal basis to build a projection matrix