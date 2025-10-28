Roller chains are a form of flexible drives that have the advantage of negligable amounts of creep and no slipping. They have a long life span and they are capable of driving multiple shafts from one driven sprocket.

## Geometry
| Term                    | Definition                                                                                      | Usage                                                                                                                                             |
| ----------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pitch$\left( p \right)$ | The linear distance between each link or roller.                                                | Determines the length of the link plates. Larger pitch chains are typically stronger, but not always. Corresponds to the chain number.            |
| Link Plate              | The external plates of the chain link connecting the rollers together                           |                                                                                                                                                   |
| Roller                  | Small tubes that connect the sides                                                              | Permits rolling action over the teeth                                                                                                             |
| Width                   | The spacing between the link plates (width of the rollers)                                      |                                                                                                                                                   |
This formula to find the pitch diameter of the spocket approximates the $N$ toothed sprocket as a $N$ sided polygon and makes a small angle approximation that taking $\frac{p}{2}$ and $\frac{D}{2}$ we can assume that the line between the pitches is almost tangent and forms a right angle triangle.
$$
P_{d}=\frac{p}{\sin\left( \frac{180}{N} \right)}
$$
### Speed Variation
The small difference in distance from the pitch diamter to the circle where the chain enters. This again is modelled as a polygon, so the difference is the difference between entering the gear at a midpoint and entering at a vertex. We can clearly see that this effect is smaller for polynomials with more sides. The change in distance creates a variation in chain speed called **chordal speed variation**. To minimize the additional wear and vibrations created by this make pinion sprockets with $\mathbf{N \geq 17}$. 

### Velocity Ratio
It is best to keep vecity ratios at a maximum of $6:1$. 

## Failure Modes
The two most common forms of failure in roller chains are **Link Plate** and **Roller** failure. The link plate failure mode occurs at lower speeds under high tension. This occurs in the region of **Pre-Extreme Horsepower** because this failure occurs at lower speeds before the maximum power transmision is reached. Roller plate failure happens in the **Post Extreme Horsepower** domain when fatigue failure begins governing the limits of power transmisson, and is where roller failure occurs.

### Pre-Extreme, Link Plate Failure Horsepower
$$
H_{1}=0.004N_{1}^{1.08}n_{1}^{0.9}p^{3-0.07p}
$$
### Post-Extreme, Roller Fatigue Failure Horsepower
$$
H_{2}=\frac{1000K_{r}N_{1}^{1.5}p^{0.8}}{n_{1}^{1.5}}
$$
Where $K_{r}$ is specified by chain number: 29 for chain numbers 25, 35; 3.4 for chain 41; and 17 for chains 40–240.

