# Task 01 – Propagation of Error I (Sphere Volume)

## Problem Statement

The radius of a sphere is measured as

$$
r = (6.20 \pm 0.05) \text{ cm}
$$

Calculate the volume of the sphere and its associated uncertainty.

## Theory

The volume of a sphere is given by

$$
V = \frac{4}{3} \pi r^3
$$

For a quantity $V = k r^n$, the relative uncertainty propagates as

$$
\frac{\Delta V}{|V|} = |n| \frac{\Delta r}{|r|}
$$

where $\Delta r$ is the absolute uncertainty in $r$.

## Step-by-Step Solution

**Step 1: Calculate the nominal volume**

Substitute $r = 6.20 \text{ cm}$ into the volume formula:

$$
V = \frac{4}{3} \pi (6.20)^3
$$

First compute $r^3$:

$$
(6.20)^3 = 6.20 \times 6.20 \times 6.20 = 238.328 \ \text{cm}^3
$$

Then multiply by $\frac{4}{3} \pi \approx 4.18879$:

$$
V = 4.18879 \times 238.328 \approx 998.3 \ \text{cm}^3
$$

More precisely:

$$
V = \frac{4}{3} \pi (238.328) = \frac{4}{3} \times 3.1415926 \times 238.328
$$

$$
V = 998.3 \ \text{cm}^3
$$

**Step 2: Relative uncertainty in radius**

$$
\frac{\Delta r}{r} = \frac{0.05}{6.20} = 0.0080645
$$

**Step 3: Relative uncertainty in volume**

Since $V \propto r^3$, $n = 3$:

$$
\frac{\Delta V}{V} = 3 \times \frac{\Delta r}{r} = 3 \times 0.0080645 = 0.0241935
$$

**Step 4: Absolute uncertainty in volume**

$$
\Delta V = V \times \frac{\Delta V}{V} = 998.3 \times 0.0241935 \approx 24.15 \ \text{cm}^3
$$

Round to two significant figures (matching $\Delta r$ precision):

$$
\Delta V \approx 24 \ \text{cm}^3
$$

## Final Result

$$
V = (998 \pm 24) \ \text{cm}^3
$$

## Interpretation

The volume uncertainty is dominated by the cube power in the radius formula. A 0.8% relative uncertainty in radius leads to approximately 2.4% relative uncertainty in volume. The result shows that even small measurement errors in length amplify when calculating derived quantities with exponents greater than 1.
