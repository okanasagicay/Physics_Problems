# Task 06 – Instrument Precision

## Problem Statement

A digital thermometer reads $25.4^\circ \text{C}$. Assuming the uncertainty is half the value of the last digit, what is the absolute uncertainty of this measurement?

## Theory

For a digital instrument, the last digit represents the resolution. A common convention is:

$$
\Delta x = \frac{1}{2} \times (\text{last digit value})
$$

The last digit value is the place value of the least significant digit.

## Step-by-Step Solution

**Step 1: Identify the last digit and its place value**

Reading: $25.4^\circ \text{C}$

Digits: 2, 5, 4

The last digit is **4** in the tenths place.

Place value of the last digit = $0.1^\circ \text{C}$

**Step 2: Apply the half-digit rule**

$$
\Delta T = \frac{1}{2} \times 0.1 = 0.05^\circ \text{C}
$$

## Final Result

$$
\Delta T = 0.05^\circ \text{C}
$$

The measurement can be written as:

$$
T = (25.40 \pm 0.05)^\circ \text{C}
$$

## Interpretation

The half-digit rule is a conservative estimate of instrument uncertainty. It assumes the true value could be anywhere within $\pm 0.5$ of the last digit's resolution. For a thermometer reading to one decimal place, the uncertainty is $\pm 0.05^\circ \text{C}$.
