Flat belts are useful for transmitting power over long distances and having flexibility to change axis of motion unlike [[V-Belts]].  A disadvantage they may have is belt slip, caused by a lack of friction betweent the belt and pulley and elastic creep when the belt elogates under tension.
### Geometric Parameters

| Term                                          | Definition                                                                                      | Usage                                                                                                                                             |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wrap Angle $\left( \phi_{d},\phi_{D} \right)$ | The angle that the belt is making contact with the pulley                                       | Used to determine how much contact and therefore friction the belt has with the pulley                                                            |
| Diameter $\left( D,d \right)$                 | Size of the driving $d$ and driven $D$ pulley                                                   | Affects center distance, wrap angle, and speed ratio                                                                                              |
| Center Distance $C$                           | Distance between the centers of the two pulleys                                                 | Determines how much space the sytem occupies                                                                                                      |
| Belt Length $\left( L \right)$                | The overall length of the belt                                                                  | Sizing the length of the belt                                                                                                                     |
| Dip $(\text{dip})$                            | The perpendicular distance from the line tangent to both pulleys and the slack side of the belt | For space considerations. Longer belts and lower initial tension results in greater dip                                                           |
| Crowning                                      | A slight elevation in the center of the driven pulley with a trapezoid shape                    | Keeps the belt aligned. The larger of the pulleys is the one that should be crowned. Both pulleys should be crowned if there is a change is axis. |

## Forces On Flat Belts
A key element in [[Flat Belt Design Guide |flat belt design]] is analysis of the tension inside of the belt. To solve for the forces the [[Capstan Equation]] is used to relate the force in the taught and slack side.
$$
F_{1} - F_{2} = \frac{(F_{1}-F_{c})\left(  \text{exp}(f\phi) - 1\right)}{\text{exp}(f\phi)}
$$
The centrifugal force $F_{c}$ describes the force on the belt pulling it outwards from the pulley as it rotates around.
$$
\begin{align}
V=\frac{\pi dn}{12}\text{ft/min} \\
F_{c} = \frac{w}{g}\left( \frac{V}{60} \right)^{2}
\end{align}
$$
We can also infer that the difference in force between the taught side force and the slack side tension is the torque applied to the belt
$$
F_{1}-F_{2}=\frac{2T}{d}
$$
A key idea in flat belts too is that there is some initial tension required to transmit any torque to the belt. This is a force that is shared by the taught and slack side of the belt.