When an insulator ([[Dielectric]]) is placed in an $\mathbf{E}$ feild, microscopic [[Dipole Moments]] are induced by the force applied on the charged elements of the atoms and a torque is applied to them to align themselves with the feild. Like in [[Conductors]], this process happens nearly instantaneously, and we can look at it from a static context. 

## Polarization Feild
The polarization feild describes the density of dipole moments in a material
$$
\mathbf{P}\equiv N\mathbf{p}
$$
where $N$ is the number of dipoles per unit volume. 

### Induced / Bound Charges
As the electric feild seperates the individual charges in the material, regions of more positive and more negative charges form. Of course, if no charges are added or removed from the material:
$$
Q_{\text{total, bound}} = 0
$$
A bound surface charge $\sigma_{b}$ can form at the surface of the dielectric, specifically surfaces that are perpendicular to $\mathbf{E_{\text{external}}}$. Unlike conductors though, the positive and negative charges are not freely moving, so the $\sigma_{b}$ developed will not necesarrily cancel out the feild internally.
$$
\mathbf{E_{\text{internal}}} \neq \mathbf{0} \quad \text{For most cases}
$$
To find the bound charge, find the component of the $\mathbf{P}$ that is aligned with the $\mathbf{\hat{n}}$.
$$
\sigma_{b}=\mathbf{P \cdot \hat{n}}
$$
>[!Intuition]
> It is helpful to picture a uniformly polarized slab of dielectric in an electric field. On the inside, since the polarization is uniform the little positves are cancelled by the little negatives right above it. When we reach the surface, there is no little negative above the positive charge to cancel it out. So the surface of the slab develop a bound charge at its surface. 
>
> Now if we wanted to figure out how much is at the surface. We expect the more $\mathbf{P}$ is aligned with the surface, the more bound charges will be there because there is less little negatives to cancel out the charge. 
>
> Now think of $\mathbf{p}$ as a *weighted seperation of charge*. Dipole moment is a moment. It is measuring how imbalanced the charge distribution is.  So $\mathbf{P}$ is kind of measuring how far these charge guys have been seperated. 
>
> Now it acts kind of weird near this surface because there is no longer a layer above the surface. So imagine it as a limit where $\mathbf{P_{\perp}}=\rho \Delta z$ where we take $\Delta z\to 0$ but $\mathbf{P_{\perp}}$ remains finite. Now we can say at this surface, the component acting perpendicular to the surface is the surface charge density
> 
