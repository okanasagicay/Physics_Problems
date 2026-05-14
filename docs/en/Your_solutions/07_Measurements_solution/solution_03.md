# Task 03 – Propagation of Error III (Ohm's Law)

## Problem Statement

Resistance is calculated using Ohm's Law:

$$
R = \frac{V}{I}
$$

Voltage and current measurements:

$$
V = (10.0 \pm 0.2) \ \text{V}
$$

$$
I = (2.00 \pm 0.05) \ \text{A}
$$

Calculate the resistance and its uncertainty.

## Theory

For division $R = V/I$, the relative uncertainty propagates as:

$$
\left( \frac{\Delta R}{R} \right)^2 = \left( \frac{\Delta V}{V} \right)^2 + \left( \frac{\Delta I}{I} \right)^2
$$

## Step-by-Step Solution

**Step 1: Calculate nominal resistance**

$$
R = \frac{10.0}{2.00} = 5.00 \ \Omega
$$

**Step 2: Calculate relative uncertainties**

$$
\frac{\Delta V}{V} = \frac{0.2}{10.0} = 0.02
$$

$$
\frac{\Delta I}{I} = \frac{0.05}{2.00} = 0.025
$$

**Step 3: Combine in quadrature**

$$
\left( \frac{\Delta R}{R} \right)^2 = (0.02)^2 + (0.025)^2
$$

$$
= 0.0004 + 0.000625 = 0.001025
$$

$$
\frac{\Delta R}{R} = \sqrt{0.001025} = 0.0320156
$$

**Step 4: Calculate absolute uncertainty**

$$
\Delta R = R \times 0.0320156 = 5.00 \times 0.0320156 \approx 0.160 \ \Omega
$$

Round to two decimal places:

$$
\Delta R \approx 0.16 \ \Omega
$$

## Final Result

$$
R = (5.00 \pm 0.16) \ \Omega
$$

## Interpretation

The current measurement contributes more to the uncertainty (2.5%) than the voltage (2.0%). The combined relative uncertainty is about 3.2%. This example shows how division propagates errors similarly to multiplication — relative uncertainties add in quadrature.
