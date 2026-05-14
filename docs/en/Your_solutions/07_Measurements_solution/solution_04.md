# Task 04 – Relative Uncertainty (Speedometer)

## Problem Statement

A car's speedometer has a 5% uncertainty. If it reads 60 km/h, what is the range of the car's actual speed?

## Theory

Percentage uncertainty is defined as:

$$
\text{Percentage uncertainty} = \frac{\Delta x}{|x|} \times 100\%
$$

Given the percentage uncertainty, the absolute uncertainty is:

$$
\Delta x = \frac{\text{Percentage uncertainty}}{100\%} \times |x|
$$

The range is:

$$
x_{\text{min}} = x - \Delta x, \quad x_{\text{max}} = x + \Delta x
$$

## Step-by-Step Solution

**Step 1: Identify given values**

Reading: $x = 60 \ \text{km/h}$

Percentage uncertainty: $5\% = 0.05$

**Step 2: Calculate absolute uncertainty**

$$
\Delta x = 0.05 \times 60 = 3 \ \text{km/h}
$$

**Step 3: Determine the range**

$$
x_{\text{min}} = 60 - 3 = 57 \ \text{km/h}
$$

$$
x_{\text{max}} = 60 + 3 = 63 \ \text{km/h}
$$

## Final Result

The actual speed lies in the range:

$$
57 \ \text{km/h} \ \text{to} \ 63 \ \text{km/h}
$$

Or written as:

$$
v = (60 \pm 3) \ \text{km/h}
$$

## Interpretation

A 5% relative uncertainty means the true value could be 5% above or below the reading. This does not mean the speedometer is "bad" — all measurements have uncertainty. The range represents a confidence interval (typically one standard deviation if the uncertainty is reported as such).
