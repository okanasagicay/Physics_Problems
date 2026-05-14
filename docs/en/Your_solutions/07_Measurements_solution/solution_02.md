# Task 02 – Propagation of Error II (Rectangle Area)

## Problem Statement

The length and width of a rectangular plate are measured as

$$
L = (15.3 \pm 0.1) \ \text{cm}
$$

$$
W = (8.4 \pm 0.1) \ \text{cm}
$$

Calculate the area of the plate and its uncertainty.

## Theory

The area of a rectangle is

$$
A = L \times W
$$

For multiplication, the relative uncertainties add in quadrature:

$$
\left( \frac{\Delta A}{A} \right)^2 = \left( \frac{\Delta L}{L} \right)^2 + \left( \frac{\Delta W}{W} \right)^2
$$

## Step-by-Step Solution

**Step 1: Calculate the nominal area**

$$
A = 15.3 \times 8.4 = 128.52 \ \text{cm}^2
$$

**Step 2: Calculate relative uncertainties**

$$
\frac{\Delta L}{L} = \frac{0.1}{15.3} = 0.0065359
$$

$$
\frac{\Delta W}{W} = \frac{0.1}{8.4} = 0.0119048
$$

**Step 3: Combine in quadrature**

$$
\left( \frac{\Delta A}{A} \right)^2 = (0.0065359)^2 + (0.0119048)^2
$$

$$
= 4.271 \times 10^{-5} + 1.417 \times 10^{-4} = 1.8441 \times 10^{-4}
$$

$$
\frac{\Delta A}{A} = \sqrt{1.8441 \times 10^{-4}} = 0.01358
$$

**Step 4: Calculate absolute uncertainty**

$$
\Delta A = A \times 0.01358 = 128.52 \times 0.01358 \approx 1.745 \ \text{cm}^2
$$

Round to one decimal place (matching input precision):

$$
\Delta A \approx 1.7 \ \text{cm}^2
$$

Round area to same decimal precision:

$$
A \approx 128.5 \ \text{cm}^2
$$

## Final Result

$$
A = (128.5 \pm 1.7) \ \text{cm}^2
$$

## Interpretation

The width measurement has a larger relative uncertainty (1.19%) than the length (0.65%) because $W$ is smaller. The quadrature combination gives a total relative uncertainty of about 1.36%. This method assumes the errors in $L$ and $W$ are independent and random.
