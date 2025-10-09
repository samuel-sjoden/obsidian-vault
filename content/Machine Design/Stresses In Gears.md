There are two primary forces in gears: [[Bending Stress]] from the catelevering of the teeth and contact stress from the contact between the teeth.

## Hertz Contact Stress
Whereever the two objects make contact there is a small path of material that deforms slightly. Depending on the geometry of the contact patch the stress distribution changes. The involute profile of the gears make contact in a cylindrical profile. 

We are most interested in where the stress is at a maximum. 

The perpendicular contact stresses create additional internal [[Poisson Stresses]], adding more compressive stresses inside the tooth. All of the stresses currently are stricly in perpendicular directions with no shear, and therefore are principle stresses on the material. We can then draw a [[Mohr's Circle]] and use an appropriate failure criteria. 

From the [[St. Venants Principle]], we usually look just under the surface so that the forces are more distributed. This is often evident a few microns below the surface. This is where the the maximum shear stress is typically reached and is where the gear ends up failing due to contact shear stresses.

### Contact Stress Equations
To find out the worst case senario to determine the maximum load the contact stresses are applying we use the maximum point from the hertz contact stress when the gears have one contact point. 

#### Elastic Coefficent $C_{p}$

#### Geometry Factor $I$
The geometry factor scales the $\sigma_{all}$ based on the geometry from the gear. This comes from factors like number of teeth, gear ratio and pressure angles.
$$
\sigma_{nom, contact}= C_{p}\sqrt{ \frac{W_{t}}{FDpI} }
$$
#### Contact Stress Number
To adapt the nominal allowable stress, the nominal stress is adapted to the specific system, so we add the derating and rating constants.
There is an additional constant here to derate the gears if there is a surface finish that may affect the contact stresses.
$$
\sigma_{contact, design (corrected)}=C_{p}\sqrt{ \frac{W_{t}K_{o}K_{v}K_{s}K_{m}}{} }
$$
#### Allowable Contact Strengths $S_{c}$
Found in a table and is a fuction of gear hardness. The over all contact strength will have a dependence on lifetime number of cycles and some other stuff.

$$
\sigma_{contact, allowable}=\frac{S_{c}Z_{m}C_{H}}{K_{T}K_{R}}
$$
##### Saftey Factor
$$
n_{fs}=\frac{\sigma_{contact, allowable}}{\sigma_{contact, design}}
$$
Most of the design margins are baked into the design factors, so we only require a saftey fator $[1,1.5]$.
### Rolling Friction Stress
Ontop of the static hertz contact stress, there is additional shear stresses from the rolling of the teeth. These occur entering and leaving the contact.  Entering contact as a driving tooth, it starts by getting compressed. As it leaves the contact, the pressure leaves the tooth and the surface expands again.

## Bending Stress
The teeth of the gear can be modelled as cantelevered beams. Since the geometry is often very complicated for tooth profiles, it is precalculated and stored into an empirically found variable.

##### Key Geometric Features
- The number of teeth or modulus affects the shape of the teeth
- The pressure angle of the teeth
- The load sharing ratio

Ontop of the geometric factor is an additional factor for fatigue stresses. 

> [!Example]
>  $$
\sigma_{bending, nom} = S_{b, nom} = \frac{W_{t}P}{FJ}$$
> Where $F$ is the face with $P$ is the pitch and $J$ is our mystery geometry factor. 

![[Pasted image 20251007114248.png]]
> From the graph here and the given teeth on each gear we can find $J$

The geometry factor $J$ is based on maximum possible stress with fatigue and single point contact. It is very conservative. 

### Correction Factors
To tune the result to the designed system we just add a whole lotta correction factors. This will give us a design stress that is adjusted to our specific conditions
Usually:
$$
\sigma_{nom} < \sigma_{design}
$$

##### Dynamic Factor $K_{v}$
A factor depending on the quality and speed of the gears used.

##### Size Factor $K_{s}$
Larger teeth, larger size teeth there is a larger probability that a flaw exists, so it is more likley to develop internal cracks leading to fatigue failure.
Ususally for small modulus gears where the teeth have gotten big.

##### Load Distribution $K_{m}$
In gears where alignment is critical, like in big gears, the load distribution can result in increased wear. The larger the face is, the better alignment we will need. Since its not gonna be perfect, you derrate.
$$
K_{m} = 1.0 + C_{pf} + C_{ma}
$$
The two components are scaled by the width of the face $C_{pf}$ and the mesh alignement which  is from the tolerance for the alignement of the gears $C_{ma}$.

Other factors can include the crowning of the teeth, which rounds them out to increase tolerance for misalignment, but concentrates forces more.

##### Rim Thickness $K_{B}$
Accounts for bending of the rim of the gear which basically ensures theres enough meat on the gear to support the teeth. It is usually just $1.0$ in most senarios.

### Material Properties of Gears
When making gears they can often undergo treatments that alter the material properties. This will have an affect on the allowable stress on the material.


### Stress-Cycle Factors
Often things are calculated for $10^7$ cycles, which means that looking at a single tooth, each time it is loaded, it is a cycle.  For a gear at 1750 rpm continous operation this is like two weeks.

If we want it to last longer, we want to derate the allowable stress number.

##### Temperature Factor $K_{T}$
At temperatures above a threshold, the material properties degrade rapidly, so correction factors for high temperature operation are added.





