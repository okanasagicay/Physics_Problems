Task 10 – Infinite Series and Final Position of an Ant
Problem Statement
An ant starts at the origin and moves according to the pattern:

$1$ m east,
$\frac{1}{2}$ m north,
$\frac{1}{3}$ m west,
$\frac{1}{4}$ m south,
$\frac{1}{5}$ m east,

and continues in this way indefinitely.

Determine the final position of the ant.

Theory
The motion separates naturally into horizontal and vertical components.

Horizontal displacements occur on odd-numbered steps:$1, \frac{1}{3}, \frac{1}{5}, \frac{1}{7}, \dots$
Vertical displacements occur on even-numbered steps:$\frac{1}{2}, \frac{1}{4}, \frac{1}{6}, \frac{1}{8}, \dots$

The directions alternate:

horizontally: east, west, east, west, $\dots$
vertically: north, south, north, south, $\dots$

Therefore, the final coordinates are determined by two alternating series.

A standard result is

$$
1 - \frac{1}{3} + \frac{1}{5} - \frac{1}{7} + \cdots = \frac{\pi}{4}
$$

and

$$
\frac{1}{2} - \frac{1}{4} + \frac{1}{6} - \frac{1}{8} + \cdots = \frac{1}{2}\ln 2
$$

Step-by-Step Solution
Horizontal displacement
The horizontal motion is

$$
x = 1 - \frac{1}{3} + \frac{1}{5} - \frac{1}{7} + \cdots
$$

This is the Leibniz series for $\frac{\pi}{4}$, so

$$
x = \frac{\pi}{4}
$$

Vertical displacement
The vertical motion is

$$
y = \frac{1}{2} - \frac{1}{4} + \frac{1}{6} - \frac{1}{8} + \cdots
$$

Factor out $\frac{1}{2}$:

$$
y = \frac{1}{2}\left(1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \cdots \right)
$$

The alternating harmonic series satisfies

$$
1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \cdots = \ln 2
$$

Therefore,

$$
y = \frac{1}{2}\ln 2
$$
Final Result
The final position of the ant is

$$
\left(\frac{\pi}{4}, \frac{1}{2}\ln 2\right)
$$

Numerically,

$$
\left(\frac{\pi}{4}, \frac{1}{2}\ln 2\right) \approx (0.785,\ 0.347)
$$

Interpretation
The infinite motion converges to a finite point because both coordinate sums are convergent alternating series. Even though the ant keeps moving forever, the cumulative displacement approaches a fixed limit in the plane.

