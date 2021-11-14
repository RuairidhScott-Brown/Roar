# Sizing to Constraints

## Take-off Weight
$$W_0 = W_{crew} + W_{payload} + W_{fuel} + W_{empty}$$
The empty weight considers the structure, engine, landing grear, fixed equipment, avionics, etc.

We then express the fuel and empty weight as fractions of the gross take-off:

$$ W_0 = W_{crew} + W_{payload} + \left( \frac{W_f}{W_0}  \right)W_0 + \left( \frac{W_e}{W_0} \right) W_0 $$

and then we re-arrange:

$$W_0 = \frac{W_{crew} + W_{payload}}{1 - \left( \frac{W_f}{W_0} \right) - \left( \frac{W_e}{W_0}\right)} $$

We the define the ($WEF$) weight escalation factor (note: $M_f$ refers to all the mass fractions):

$$WEF = \frac{1}{1 - \sum{M_f}}$$

We should know the fixed masses form the [[target_design_specification]] so the weights that need to be calculated are the weight fractions.

### Empty Weight Estimate

$$ \frac{W_e}{W_0} $$

To do this we will use regression methods.
![[regression_method_for_empty_weight.PNG]]

The empty weight fraction historically lies between ==0.3 and 0.7==. But, a trend does arise giving:

$$ \frac{W_e}{W_0} = A W_0^c $$

Where $A$ and $B$ are constants that are dependant on the aircraft.

![[A_and_B_constants_for_empty_weight_fraction.PNG]]

```ad-note
color: 200,200,200
That variable sweep wings are heavier than fixed wings therefore you have to multiply the empty weight faction by 1.04.

For composite aircraft you can multiply the empty weight fraction by 0.95.
```


### Fuel Wright Estimate

$$ \frac{W_f}{W_0} $$

We can't use regression data because the mission that planes fly can be very varied. We need to fly the mission, [[target_design_specification]].

For initial guesses the fuel can be said to be proportional to the aircraft weight. So this means the fuel fraction is based on the mission flown.

For initial sizing we can use some basic rules of thumb. Where the mission segement is related to $\frac{W_i}{W_{i-1}}$ i.e. the weight after the mission segment compared to the weight before the mission segment.
![[fuel_usage_dependant_on_mission_segment.PNG]]

For the range and endurance we will use the [[breguet_range_and_endurance]] equations.

However, we will not know our specific fuel consumption and lift to drag ratio.

#### Specific Fule Consumption
It is the fule consumption per unit thrust. It is dependent on Mach number and the type of power plant used.
![[power_plant_specific_fuel_consumption.PNG]]

For a propeller aircraft we have to do things in terms of power:

$$ C = C_{power} \frac{V}{\eta_p} $$

Where the propeller efficiency $\eta_p$ is normally around 0.8.
![[typical_power_values_for_propeller_aircraft.PNG]]

#### Lift to Drag Ratio Estimation
*Check out Roskam for an alternative method*

The wetted aspect ratio is a good predictor of $\frac{L}{D}$, where:

$$ A_{wetted} = \frac{b^2}{S_{wetted}} = \frac{A}{\big( \frac{S_{wet}}{S_{ref}}\big)}$$

Where, $A$ is the [[aspect_ratio]], $b$ is the wing span, and the ratio $\frac{S_{wet}}{S_{ref}}$ is the ratio of the [[wetted_area]] to the [[reference_area]]. We then use this with the equation.

$$ \frac{L}{D_{max}} = K_{LD} \sqrt{\frac{A}{\big( \frac{S_{wet}}{S_{ref}} \big)}} $$

where the $K_{LD}$ term is a constant that depends on the type of aircraft.
![[L_to_D_for_airfcraft.PNG]]

But, where does $\frac{S_{wet}}{S_{ref}}$ comes from.
![[s_wet_over_s_ref.PNG]]

```ad-note
color: 200,200,200

The most efficient cruise and loiter velocities for jet and propeller aircraft occur at different conditions.

For a Jet -> Cruise: $0.866\frac{L}{D_{max}}$, Loiter: $\frac{L}{D_{max}}$
For a prop -> Cruise: $\frac{L}{D_{max}}$, Loiter $0.866\frac{L}{D_{max}}$
```

We then multiply all the flight segments together:
$$ \frac{W_2}{W_1} \frac{W_1}{W_0}  ...=  \frac{W_n}{W_0}$$

And  then apply the $\frac{W_n}{W_0}$ to the equation, where the 1.01 comes from the fuel that is trapped in the tank.

$$ \frac{W_f}{W_0} = 1.01 \big(1 - \frac{W_n}{W_0} \big) $$

### Putting It all Together
We have two equations relating empty weight to the gross take-off weight.

$$ \frac{W_e}{W_0} = A W_0^c $$


$$W_0 = \frac{W_{crew} + W_{payload}}{1 - \left( \frac{W_f}{W_0} \right) - \left( \frac{W_e}{W_0}\right)} $$

We need a solution which satisfies both equations we can do this by.

