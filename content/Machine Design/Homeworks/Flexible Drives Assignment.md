## Problem 1
>[!Question]
> A 12 inch wide Polyamide A-3 flat-belt drive is to connect a 5 inch diameter pulley to drive a larger pulley with a velocity reduction ratio of 0.5. The center line distance is 20 feet. The small pulley turns at 1750 rpm as it delivers 3hp. Use a service factor Ks = 1.25 and design factor of 1.0.

**Key Information**
$$
\begin{align}
&\text{Type}=\text{Polyamide A-3} \\
&b=12in \\
&d = 5in \\
&D= 10in  \\
&C=20ft \\
&n_{1}=1750rpm \\
&H_{nom}=3hp \\
&K_{s} = 1.25 \\
&n_{d} = 1.0
\end{align}
$$
##### a) Find $F_{c}$, $F_{i}$, $(F_{1})_{a}$ and $F_{2}$ assuming operation at maximum tension limit

Operating at the maximum tension limit means that $F_{1}= (F_{1})_{a}$

The first step is to find the centrifugal force in the belt
$$
F_{c} = \frac{w}{\frac{32.2ft}{s^2}}\left( \frac{v_{b}}{\frac{60s}{min}} \right)^2
$$
I first need to find $w$ and $v_{b}$. From a table lookup to Table 17-2
![[Pasted image 20250930184309.png]]
I find that $\gamma=\frac{0.042lb}{in^3}$ and $t=0.13in$
$$
w=\gamma bt=\frac{0.78624lb}{ft}
$$

The for the belt velocity I use this formula
$$
v = \frac{\pi dn}{12}=\frac{\pi(5)(1750)}{12}=\frac{2290.74ft}{min}
$$
plugging it into the $F_{c}$ equation I find:
$$
\boxed{F_{c} =  35.6lb}
$$
Then to find the tension in the taught side of the belt, I look to the maximum allowable force.
$$
(F_{1})_{a}=bF_{a}C_{p}C_{v}
$$
$C_{v}=1.0$ for Polyamide belts
From the table above $F_{a} = \frac{100lb}{in}$
From Table 17 - 4
![[Pasted image 20250930184911.png]]
	$C_{p}=0.7$
	$$
(F_{1})_{a}=(12)(1.0)(0.7)(100)=840lb
$$
$$
\boxed{F_{1}=840lb}
$$
Knowing the power of the drive, we can find the torque on the pulley which allows us to use the relation
$$
(F_{1})_{a} - F_{2}=\frac{2T}{d}
$$
$$
T=\frac{63025*H_{nom}K_{s}n_{d}}{n}=63025\left( \frac{(3hp)(1.25)(1.0)}{1750rpm} \right)=135.054lb-in
$$
$$
\boxed{F_{2}=840-\left( \frac{2(135.054)}{5} \right)=786lb}
$$
Then finally the initial tension can be found
$$
F_{i} = \frac{F_{1}+F_{2}}{2}-F_{c}
$$
$$
\boxed{F_{i} = 777lb}
$$
##### b) Find $H_{a}$, safety factor $n_{fs}$ and belt length

Since we are operating the belt at its maximum limit, we expect the safety factor to come out to be 1.

$$
H_{a} = H_{nom}K_{s}n_{d}=(3hp)(1.5)(1.0)
$$
$$
\boxed{H_{a} =3.75hp}
$$
$$
H_{d} = \frac{((F_{1})_{a}-F_{2})v_{b}}{33000}=3.75hp
$$
$$
\boxed{n_{fs}=\frac{H_{a}}{H_{d}}=1}
$$

For the length of the belt:

$$
L=\sqrt{ 4C^2 -(D+d)^2} +\frac{1}{2}(D\phi_{D}+\phi_{d}d)
$$
First we have to find the wrap angles
$$
\phi_{D} = \pi + 2\sin^{-1}\left( \frac{D-d}{2C} \right)=3.16\text{rad}
$$
$$
\phi_{d} = \pi - 2\sin^{-1}\left( \frac{D-d}{2C} \right)=3.12\text{rad}
$$
$$
\boxed{L=503.6in=42.0ft}
$$
##### c) Find the dip in the belt.
$$
\text{dip}= \frac{C^2w}{96F_{i}}
$$
$$
\boxed{\text{dip}=0.607in}
$$