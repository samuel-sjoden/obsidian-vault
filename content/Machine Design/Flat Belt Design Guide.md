## Geometry
First identify the geometry of the [[Flat Belts|flat belt]]. 
Given a speed ratio or center distance the $d,D,C,L$ must be specified.
**Guidelines:**
- Keep $v_{b}<600\text{fpm}$ $\to$ higher speeds result in more frequency of bending which result in greater fatigue stress in the belt
- The same idea for minimum pulley size $\to$ for higher belt speeds, to reduce [[Bending Stress|bending stress]], the driven diameter should be larger.

Wrap angles:
$$
\begin{align} \\
\phi_{d} = 180 - 2\sin^{-1}\frac{\left( D-d \right)}{2C} \\
\phi_{D} = 180 + 2\sin^{-1} \frac{\left(  D-d\right)}{2C} 
\end{align}
$$
Belt Length:
$$
L = \sqrt{ 4C^{2}-(D-d)^{2} } + \frac{1}{2}(D\phi_{D}+d\phi_{d}) \quad \text{Angles are in degrees}
$$
Center Distance from belt length:
$$
\begin{align}
B = 4L - 6.28(D+d) \\
C = \frac{B+\sqrt{ B^{2}-32(D-d)^{2} }}{16}
\end{align}
$$
Belt Dip:
$$
\text{dip} = \frac{C^{2}w}{96F_{i}}
$$
## Forces
1. First find centifugal force in the belt $F_{c}$ from the belt material properties
	![[Pasted image 20251023144647.png]]
		$$
\begin{align}
V=\frac{\pi dn}{12}\text{ft/min} \\
w = 12\gamma bt \\
F_{c} = \frac{w}{g}\left( \frac{V}{60} \right)^{2}
\end{align}
$$
2. Find the necesarry torque to operate the belt from:
$$
H_{\text{design}} = H_{\text{nom}}K_{s}n_{d}
$$
	$H_{nom}$ is the horsepower of the driving machine
	$K_s$ is the service factor used to derate loads that may fluctuate and aren't smooth
	$n_{d}$ used to derate in abnormal conditions Ex. Dirty environment
	$$
T=\frac{63025H_{\text{nom}}K_{s}n_{d}}{n} = \frac{63025H_{\text{design}}}{n}
$$
3. Find the maximum allowable taught side tension to validate the design
$$
(F_{1})_{a} - F_{2} = \frac{2T}{d}
$$
	This difference contains the maximum for the system. Plugging in the actual maximum for the belt:
$$
(F_{1})_{a} = bF_{a}C_{p}C_{v}
$$
	Where the $F_{a}$ in the above table is adjsuted to the width of the belt, and the size of the pulley $C_{p}$ and speed of the belt $C_{v}$. The constants derate the rated force if the belt is being bent at a higher frequency (higher speed belt and smaller driven pulley).
	$C_{v}=1.0$ for polyamide belts.
	**For LEATHER BELTS ONLY!!**
	![[Pasted image 20251023145814.png]]
	![[Pasted image 20251023145836.png]]
4. Now find $F_{2}$ now that $(F_{1})_{a}$ is known
	 $$
F_{2} = (F_{1})_{a} -\left[ (F_{1})_{a}-F_{2} \right]
$$
5. Find the initial tension in the belt with:
	$$
F_{i} = \frac{\left( (F_{1})_{a}+F_{2} \right)}{2}-F_{c}
$$
6. Validate the friction required $f'<f$  found in Table 17-2 above.
	$$
f'=\frac{1}{\phi}\ln \frac{\left( (F_{1})_{a}-F_{c} \right)}{F_{2}-F_{c}} \quad \text{Angle in radians}
$$
7. Validate factor of safety. The true validation is kind of that there is a sufficent friction constant and this is kind of derived.
	$$
n_{fs} = \frac{H_{\text{design}}}{H_{\text{nom}}K_{s}}
$$
