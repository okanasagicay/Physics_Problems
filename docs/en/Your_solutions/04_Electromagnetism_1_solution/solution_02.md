
I’ll calculate the electric potential at the center of the square step by step.

---

## **Step 1: Understand the setup**
Square side length: \( a = 1.0 \ \text{m} \)  
Charges at corners in order:  
\( q_1 = +1 \ \text{C} \)  
\( q_2 = -2 \ \text{C} \)  
\( q_3 = +3 \ \text{C} \)  
\( q_4 = -4 \ \text{C} \)

All placed at corners of a square in cyclic order.

---

## **Step 2: Distance from center to any corner**
For a square of side \( a \), the distance from center to any corner is half the diagonal:

\[
r = \frac{\sqrt{a^2 + a^2}}{2} = \frac{a\sqrt{2}}{2} = \frac{a}{\sqrt{2}}
\]
\[
r = \frac{1.0}{\sqrt{2}} = \frac{\sqrt{2}}{2} \ \text{m} \approx 0.7071 \ \text{m}
\]

---

## **Step 3: Formula for electric potential**
Electric potential is scalar:
\[
V = \frac{1}{4\pi\epsilon_0} \sum_{i=1}^{4} \frac{q_i}{r}
\]
Since \( r \) is the same for all charges:
\[
V = \frac{1}{4\pi\epsilon_0} \cdot \frac{1}{r} \left( q_1 + q_2 + q_3 + q_4 \right)
\]

---

## **Step 4: Sum of charges**
\[
q_1 + q_2 + q_3 + q_4 = 1 - 2 + 3 - 4
\]
\[
= (1-2) + (3-4) = (-1) + (-1) = -2 \ \text{C}
\]

---

## **Step 5: Plug into formula**
\[
V = \frac{1}{4\pi\epsilon_0} \cdot \frac{1}{0.7071} \cdot (-2)
\]

We know \( \frac{1}{4\pi\epsilon_0} = 8.9875\times 10^9 \ \text{N·m}^2/\text{C}^2 \), but we can keep it symbolic for now.

\[
V = -\frac{2}{4\pi\epsilon_0 r}
\]
\[
r = \frac{1}{\sqrt{2}}
\]
\[
V = -\frac{2}{4\pi\epsilon_0 \cdot \frac{1}{\sqrt{2}}}
= -\frac{2\sqrt{2}}{4\pi\epsilon_0}
\]

---

## **Step 6: Simplify**
\[
V = -\frac{\sqrt{2}}{2\pi\epsilon_0}
\]

Numerically:
\[
\frac{1}{4\pi\epsilon_0} \approx 8.9875\times 10^9
\]
\[
\frac{1}{4\pi\epsilon_0} \cdot \frac{1}{r} = (8.9875\times 10^9) \times \sqrt{2} \approx 8.9875\times 10^9 \times 1.41421356
\]
\[
\approx 12.708 \times 10^9 \ \text{N·m/C}
\]

Multiply by \(-2\):
\[
V \approx -25.416 \times 10^9 \ \text{V}
\]
\[
V \approx -2.54 \times 10^{10} \ \text{V}
\]

---

## **Step 7: TCT file output**
```tct
Problem: Electric potential at center of square
Given: square side 1.0 m
Charges at corners in order: q1=+1C, q2=-2C, q3=+3C, q4=-4C

Distance from center to corner:
r = a/√2 = 1.0/√2 = 0.70710678 m

Sum of charges = 1 - 2 + 3 - 4 = -2 C

Electric potential V = (1/(4πε₀)) * (Σq_i)/r

V = (8.98755e9 N·m²/C²) * (-2 C) / (0.70710678 m)

V = -2.5410e10 V

Answer: -2.54 × 10¹⁰ V
```
