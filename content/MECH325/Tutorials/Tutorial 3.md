
>[!problem]
>A mine hoist uses a 2-inch 6x19 monitor -steel wire rope. The rope is used to haul maximmum loadsof 4 tons from a 490 ft shaft. The drum has a diamter of 6 feet and the sheaves are good quality cast steel and the smallest is 3 feet in diameter

#### Key values
- Monitor steel
-  2'' 6 x 19 rope
- $D_{1} = 6$
- $d_{2} = 3'$ 
- Max load - 4 tons $\approx$ $8000$lbf
-  $a=2$ft/s^2
- $v = \frac{1200ft}{min}$

## Problem 1.

#### A)
**We want the stress in the wire**

We need the tension limit, bending force and the fatigue force.

Equation 17-47
$$
F_{t} = \left( \frac{W}{m}+wl \right)\left( 1+\frac{a}{g} \right)
$$
$g = \frac{32.2ft}{s^2}$
$W = 8000lb$ (weight supported)
w is the weight of the rope per length, we are going to find this value in a table. 
$w=1.60d^2$  where d is the diameter of the wire as given in the problem.
>[!question]
>Why are we using the weight of the rope without the core and not with the core

m is the number of ropes in the wire, here there is one rope. The 6 X 19 gives information on the number of strands in the wire.

We are given the shaft length which we will approximate as the length of wire rope.

$$
F_{t} = \left( \frac{8000lb}{1} + 1.6(2.0in)^2\left[ \frac{lb}{ft} \right](480ft)\right)\left( 1 + \frac{2}{32.2} \right)
$$

We may be using monitor steel, but the wire is not strictly steel (there's a core) so we use the strength value provided in the table.
$$
(S_{u})_{nom} < S_{u}
$$
$$
(S_{u})_{nom} = 106ksi
$$
The nominal stress is over the entire area of the wire and not just the steel.

Area of the metal is specified in the table as $$
A_{m} = 0.40d^2
$$$$
A_{m} = 1.60[in^2]
$$
**Ultimate Load**
$$
F_{u} = (S_{u})_{nom} A_{nom}
$$
$$
F_{u} = \frac{106[ksi]\pi}{4}2^2[in^2]
$$
$A_{nom}$ is the area of the rope if you approximate the cross section as a circle.

**Equivalent Bending Load**
$$
F_{b} = \frac{E_{r}d_{w}A_{m}}{D}
$$
**Better Sheave Diameter**
From the table we use:
$$
D = 45d
$$
$$
F_{b} = \frac{12\text{x10}^6\text{psi}(0.067d)[in](1.60)[in^2]}{90[in]}
$$
##### Fatigue Stress

$$
F_{f} = \frac{\frac{p}{S_{u}}(S_{u})(d)(D)}{2}
$$


To get the funky ratio $\frac{p}{S_{u}}$ we have to look at a graph with bends till failure on the x-axis. Since we don't know the number we will make an assumption, then check its validity later.

**Assuming 1 million bends till failure** $\implies \frac{p}{S_{u}} = 1.4 /1000$ 
$$
240 < S_{u} < 280[ksi]
$$
In mechanical engineering fashion we will overspec this by using the lower value of ultimate strength.
$$
F_{f} = \frac{0.0014(240(10^3))(2)(90)}{2}
$$

### B)
$$
\text{factor of safety} = \frac{\text{allowable}}{actual}
$$
For wire ropes, the allowable load is the ultimate force less the bending forces present in the system over the actual load.
$$
n_{fs} = \frac{F_{u} - F_{b}}{F_{t}}
$$
For a static situation without any bending stresses. Looking at it in a static instance (so the inertial load is present, we are just looking at a static snapshot)
$$
n_{fs \text{ no bending}} = \frac{F_{u}}{F_{t}}
$$
Fatigue safety factor with bending $$
n_{fs \text{ fatigue}} = \frac{F_{f} - F_{b}}{F_{t}}
$$
The result of the above comes out less than 1, which indicates that the wire will fatigue sooner than our assumed endurance limit. We will have to redo the calculation  of $F_{f}$ with a lower assumption to achieve a greater safety factor.

## Problem 2.
**Effective Friction**
You are usually given a friction coefficient in the table, but we want to compare to see if the belt slips or not. If the system needs a friction coefficient greater than the one in the table, your system is slipping.
$$
f' = \frac{1}{\phi}\ln\left( \frac{(F_{1})_{a} - F_{2}}{F_{2} - F_{c}} \right)
$$
if $f' < f$ you are chilling

To optimize the belt life by minimizing pretension, you can operate at the rated frictional coefficient 