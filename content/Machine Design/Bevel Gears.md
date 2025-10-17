## Stresses in Bevel Gears
The process is a slightly modified version of finding [[Stresses In Gears]].

Start off with the force analysis
### Bending Stresses In Bevel Gears
First find the design bending stress number:
$$
\sigma_{\text{bending, design}}=\frac{\frac{W^{t}}{F}R_{d}K_{o}K_{s}K_{m}K_{v}}{K_{x}J}
$$
##### $K_{o}$ Overload Factor
##### $K_{v}$ Dynamic Factor
Use the pitch diameter not the average diameter
#### Size of teeth, Load, and Curvature: $K_{s},K_{m},K_{x}$

$K_{s}$ Size factor is the same deal as the spur gears

$K_{m}$ The load distribution factor depends on face width and the bearings that mount the shafts. This is a bit dissimilar to the alignment factor in spur gears.

$K_{X}$ The curvature factor only comes into play for non straight cut bevel gears like a spherical guy.

#### Strength Analysis
To get to [[Saftey Factor]], find the allowable bending stress which is mostly dependent on the material properties.$$
\sigma_{\text{Bending, Allowable}} = \frac{s_{\text{all}}K_{L}}{S_{F}K_{T}K_{R}}
$$
##### $K_{T}$ Temperature Factor
##### $K_{R}$ Reliability Factor

### Contact Stresses In Bevel Gears
First find the design stress:
$$
\sigma_{\text{design, contact}} = C_{p}\left( \frac{W_{t}}{Fd_{p}I}\times K_{o}K_{v}K_{m}C_{s}C_{xc} \right)
$$
Many of the factors are recycled from the bending stress analysis
##### Size and crowning factors $C_{s},C_{xc}$
Slightly different size factor for contact stresses

Bevel gears typically are crowned, so an additional factor is added.

#### Strength Analysis
$$
\sigma_{\text{allowable, contact}}=\frac{s_{c}C_{L}C_{H}}{S_{H}K_{T}C_{R}}
$$

#### Factor of Saftey $n_{fs}$
$$
n_{fs} = \frac{\sigma_{\text{design, contact}}}{\sigma_{\text{allowable, contact}}}
$$

