# Wing Conceptual Design Notes
## Choosing the $C_L$

The optimal value for the $C_L$ should lie between (0.4 and 0.6) which comes from the drag model and is associated with maximum lift to drag.

![[lift _to_drag_different_AR.png]]

$$
C_D = C_{D,0} + \frac{C_L^2}{\pi e AR}
$$

and if we take a look at the typical value for lift to drag for a civil jet, wet get around 15 and 16 which is just outside of the optimal value for lift to drag.

![[L_to_D_for_airfcraft.png]]

The reaso why the $C_L$ is chosen to be smaller is that it should allow for less struture. But a $C_L$ should be chosen to still have a high lift to drag ratio. That is why is should probably lie inbetween **(0.2-0.4)**.

## Mach Consideration
From the brief the jet should be capable of flying at 0.78 M which means a super-crit aerofoil should be considered. It shold be designed to dely the onset of wave drag. This is super important as wave drag dramatically increases the drag acting on the aerofoil.

![[wave_drag.png]]

## Landing and Takeoff

## Sizing

Considering that the majority of any flight should be in the cruise phase. $L=W$ is considered. Whether to accout for the drop in fuel due to takeoff and half of the cruise should considered. Lets make the assumption that we are designing for mid-cruise (the fuel should be **semi-consumed**)

$$
L = W = 0.5 \rho V_{\infty}^2 C_L S
$$

aspect ratio [[aspect_ratio]] needs to be considered early on. It should be as high as possible?? as it is inversely proportional to the $L/D$. Typically it lies in the region of **(6,10)**. From initial sizing this can be obtained.

$C_L$ of the 3D wing should come from the the gross area of the wing and the  $L=W$ relation.

## Wing Geometry

### Aspect Ratio Trade Off
After selecting an aspect ratio that should be used we can then vary the value up and down by say 10% and see if that significantly effects the results.

Have to think about the aerodynamic wing loading. L/S.

The higher the aspect ratio the lower the wing loading.
Small increase in the aspect ratio does not necessarily mean an increase in wing loading. Increased aspect ratio can result in an increase in the exposed surface is the span also increases. Also the increase in the aspect ratio can imply a decrease in the lift due to the smaller surface of the wing, thus a smaller weight of the wing. Note that normally the wing weight has a negligible effect but if the trend variation is small that might have to be taken into account.

The effect of the aspect ratio of the stability of the aircraft???

### 3D Lift Coefficient
The 3D lift has an effect on the takeoff weight, aero loading of the wing, L/D, and the stability margin.

The takeoff weight decreases with respect to an increase of the CL

$$
L = 0.5 C_L \rho V^2 S
$$



### Taper Ratio
statistically it lies **(0.2 0.6)**. maybe 0.3 will be good?
- it reduces the lift at the wing tips i.e. reducing the strucutral weight and or rise the fuel capacity
- strong taper ratio increases the tip stall

## Twist/Washout
This is used so that the stall behaviour of the plane is alright sush that the aircraft doesnt stall at the tip first. This would induce a super high roll moment on the aircraft.

- it will redistribute the lift over the wing
- typically **(-5 , 0)**

## Sweep
due to the hight Mach number the wing should ideally be swet.
sweep angle at the quater chord should be follow this **(dont completely trust this yet)**.
- max sweep is around 35 degrees

$$
\Lambda = arccos \frac{0.72}{M}
$$

## Aerofoil Selection
For the supercritical application we could use the:
NACA SC(2)-0714

needs a certain degree of sweep so that the normal speed does not exceed 0.72. And this is where thee equation for sweep comes from.

## Wing Tips
Hoerner wing tip: The lower surface is "undercut" and canted approximately 30 deg to the horizontal (i.e., concave)


## Modeling

### Vortex lattice method
checkout
- vorview https://www.avidaerospace.com/avid-vorview
- TSFOIL https://github.com/swayli94/pyTSFoil
