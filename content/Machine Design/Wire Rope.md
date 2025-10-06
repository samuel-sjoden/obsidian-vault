Not a power delivery method, instead used to actually carry the load.

The spirals of the wires and strands are denoted the lay of the rope.
The grade of the wire used impacts the ultimate strength of the wire. 

### Use cases

When using a wire rope you have to consider the lay  of the rope. If you have a "free end" one end doing the load, you need swivel rope which won't unwind. Otherwise two stands are needed to carry the load.

## Design Considerations

#### Stress
When using a wire over a pulley there will be bending stress, so the amount of stress will depend on the sheave diameter and the number of passes.

Larger diameter sheaves and smaller diameter wires result in less stress in the wire. $$
\sigma = \frac{E_{r}d_{w}}{D}
$$
Where $E_{r}$ describes rope stiffness (not the young's modulus though)

The wire rope will experience "full bending" if the angle of departure is > 12 degrees. If the angle is less, the rope will not fully bend.

This comes from the width of the lay. If each lay is not being bent, the wire is not experiencing full bending. 
>[!question]
>I don't understand why the knuckles are in place? are they small ridges on the sheave? Won't that make the drive more jerky?



The equivalent bending load $F_{b}$ is the tension experienced by the wire as it is bent over the sheave. The force is used to "de-rate " the wire since it is contributing to the overall stress on the wire pushing it closer to the actual ultimate strength of the wire
$$
F_{b} = \sigma A 
$$

The wire does not have a perfectly circular cross section, so the data sheet will provide the associated area.

We only are concerned on the ultimate strength not the yield strength. To get the nominal breaking strength $F_{b}$ ,we use the ultimate strength.
$$
F_{b} = \sigma_{UT}\pi r^2
$$
Here we just approximate the area for some reason. It adds error to our calculation since the wire is not just a cylinder of steel.

With $F_{b}$ we know the ultimate strength that the wire can withstand.

##### Pressure Loads
Since the wire goes over sheaves, they apply stress on each other. Since the wire is not perfectly uniform, the contact patch will reflect the stress distribution. 

There's a table out there that tells you the maximum bearing pressure stress for the wire. The contact patch is the bottom semi-circular. The lay of the rope will have additional implications on the contact path. The regular lay results in a better contact patch.


>[!question]
>Why do we care about the contact patch? Are the stress concentrations more important than the actual load?


### Factor of Safety
$$
n = \frac{F_{u}}{F_{L(MAX)}}
$$
Where $F_{L(MAX)}$ is the maximum working load based on **static, shock, inertial, and sheave bending loads.**

$$
n_{s} = \frac{F_{u} - F_{b}}{F_{L(MAX)}}
$$
To find the maximum load that the wire rope sees:
$$
F_{L(MAX)} = \left( \frac{W}{m} + wl \right)\left( 1 + \frac{a}{g} \right)
$$
This is the  of the weight of the load per strand and the weight of the rope and under a static and inertial load.

### Fatigue Failure
Through experimentation, someone found out how many times a wire will bend before it fails via fatigue.
$$
F_{f} = \frac{\left( \frac{p}{\sigma_{UT}} \right)\sigma_{UT}Dd}{2}
$$
that's the $\frac{p}{\sigma_{UT}}$ factor. go find it in a graph

#### End Fittings
You can splice the wire or just use a metal sleeve to bend the wire back into itself to create an eye and a findle which protects the wire from wear. Findle's additionally keep the bend radius constant to prevent increased bending stress.

Then hook that thing on a shackle. It will be rated at a specific region of the shackle.

**Key Parameters**
- Minimum Sheave Diameter
- Wire Rope Stiffness
- Maximum Bearing Stress
- Breaking Force

