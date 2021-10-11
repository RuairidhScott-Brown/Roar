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
![[regression_method_for_empty_weight.PNG]

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






