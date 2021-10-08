# The Transfer Function for The Pressure Sensors
First, lets take a look at the transfer function written previously (or used for the SSCTruStability sensor).

The general idea is to have a straight line with output voltage as the dependant variable and pressure as the independant variable. From this, whenever we get a output voltage reading we can find the assocaied pressure.

![[SSCTrustability_Transfer_Function.PNG]]

How is this implemented in code.

Class Attributes:
$$
\begin{align*}
vOut &= The\; output\; voltage.\\
pressure &= Pressure\; output.\\
vSupply &= The\; voltage\; supply\; to\; the\; pressure\; sensor.\; = 5\\
pMax &= The\; max\; pressure\; reading\; from\; the\; sensor.\; = 60\\
pMin &= The\; min\; pressure\; reading\; from\; the\; sensor.\; = 0\\
transferMax &= Proportion\; of\; the\; voltage\; supply.\; = 0.9 \\
transferMin &= Proporion\; of\; the\; voltage\; supply.\; = 0.1 \\
\end{align*}
$$


The actual transfer function:
$$vOut = \frac{(transferMax - transferMin)*vSupply}{pMax - pMin}(pressure - pMin) + transferMin*vSupply \tag{1}$$