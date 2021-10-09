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

Calculating: 

$$ \frac{W_e}{W_0} $$

To do this we will use regression methods.
![[regression_method_for_empty_weight.PNG]

The empty weight fraction histori


