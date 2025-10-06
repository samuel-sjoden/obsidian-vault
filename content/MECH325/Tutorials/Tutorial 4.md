## Question 1
>[!question]
>The double-reduction gearset shown in the figure is driven through shaft a at a speed of 900 rev/min. Gears 2 and 3 are spur gears and have a diametral pitch of 10 teeth/in and a pressure angle of 20°. The second pair of gears in the train, gears 4 and 5, are helical gears with a normal diametral pitch of 6 teeth/in, a 25° helix angle, and a normal pressure angle of 20° (see Figure 13-22). The tooth numbers for the four gears are: N 2  
= 14, N3 = 54, N 4 = 16, and N5 = 36.

![[Pasted image 20250925154145.png]]
#### c) The speed and direction of shaft c
To find the speed and direction of c, I found the direction of b which was CW on the x-axis. Therefore, direction of c is CCW on the x axis.
To find the pitch diameters 

$$
n_{b} = 233\text{rpm}
$$
$$
d_{4} = \frac{N_{4}}{P} = \frac{16}{6} \qquad d_{5}=\frac{N_{5}}{P}= \frac{36}{6}
$$
Then to get the speed 
>[!equation]
> Speed relation
> $$
n_{2} = n_{1} \left( \frac{N_{2}}{N_{1}} \right)
$$

$$
n_{c} = n_{b}\left( \frac{d_{4}}{d_{5}} \right) = 233\left( \frac{16}{36} \right)= 104 \text{rpm}
$$
I could've just used $N_{4},N_{5}$ but we will need the pitch diameter for the next part of the problem
#### d) The center distance between shafts b and c

Center distance is the distance between the center of the gears.
Since the pitch circles are tangent it is the sum of their halves.
$$
d = \frac{d_{4}+d_{5}}{2}
$$
#### e) The directions of the thrust forces exerted by gears 4 and 5 on shafts b and c, respectively

~~The thrust force is the force along the axis of the shaft due to the angled teeth of the gear. The typical normal force seen by a spur gear here is split into thrust component and a normal component.

~~The component in the thrust direction remains the same independent of the direction of the gear.

$\psi$ is the helix angle of helical gears.
$P_{n}$ is the spacing between teeth if it was a spur gear
Since we want the regular pitch between the teeth, we can't use this to get pitch diameter. Instead we want the transverse pitch $P_{t}$ 
>[!Equation]
>Transverse pitch from normal diameteral pitch
>$$
P_{n} = \frac{P_{t}}{\cos(\psi)}
$$

$$
P_{t} = P_{n}\cos(\psi)
$$
Then we can find the pitch diameters of the gears
$$
d_{4}= \frac{N_{4}}{P_{t}} \qquad d_{5}=\frac{N_{5}}{P_{t}}
$$
## Question 2
>[!question]
>The mechanism train shown consists of an assortment of gears and pulleys to drive gear 9. Pulley 2 rotates at 1200 rev/min in the direction shown. Determine the speed and direction of rotation of gear 9.

![[Pasted image 20250925162626.png]]
To get from the driven pulley 2 to the speed of the 9th gear we can chain the speeds of each shaft.
**Pulley**
$$
n_{3-4}= n_{2}\left( \frac{N_{3}}{N_{2}} \right)
$$
**Bevel** 
$$
n_{5-6} = n_{3-4}\left( \frac{N_{5}}{N_{4}} \right)
$$
**Spur**
$$
n_{7-8} = n_{5-6}\left( \frac{N_{7}}{N_{6}} \right)
$$
**Worm**
$$
n_{8-9}=n_{7-8}\left( \frac{N_{9}}{N_{8}} \right)
$$

			Here the worm gear somehow has multiple teeth. 