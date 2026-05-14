FILE: task_01.md

```markdown
# Task 01 – Propagation of Error I

## Problem Statement

The radius of a sphere is measured as

$$
r = (6.20 \pm 0.05) \, \text{cm}
$$

Calculate the volume of the sphere and its associated uncertainty.

## Theory

The volume of a sphere is given by

$$
V = \frac{4}{3}\pi r^3
$$

For quantities involving powers, the relative uncertainty propagates according to

$$
\frac{\Delta V}{V} = 3 \frac{\Delta r}{r}
$$

where:

- $\Delta V$ is the uncertainty in volume
- $\Delta r$ is the uncertainty in radius

## Step-by-Step Solution

Given:

$$
r = 6.20 \, \text{cm}
$$

$$
\Delta r = 0.05 \, \text{cm}
$$

### Volume Calculation

$$
V = \frac{4}{3}\pi (6.20)^3
$$

$$
V = \frac{4}{3}\pi (238.328)
$$

$$
V \approx 998.3 \, \text{cm}^3
$$

### Relative Uncertainty

$$
\frac{\Delta V}{V} = 3 \times \frac{0.05}{6.20}
$$

$$
\frac{\Delta V}{V} \approx 0.0242
$$

### Absolute Uncertainty

$$
\Delta V = 0.0242 \times 998.3
$$

$$
\Delta V \approx 24.2 \, \text{cm}^3
$$

## Final Result

$$
V = (998 \pm 24) \, \text{cm}^3
$$

## Interpretation

The uncertainty in the radius is amplified because the volume depends on the cube of the radius. Even a small uncertainty in radius produces a larger uncertainty in volume.
```

---

