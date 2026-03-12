TASK 10 – INFINITE SERIES

Problem:
Ant starts at origin, moves:
1 m east, 1/2 m north, 1/3 m west, 1/4 m south, 1/5 m east, ...
Find final position.

Solution:

Track x and y coordinates separately.

X-coordinate (east-west):
East movements: 1, 1/3, 1/5, 1/7, ... (odd terms)
West movements: 1/2, 1/4, 1/6, 1/8, ... (even terms starting from 2)

This is the alternating harmonic series:
1 - 1/2 + 1/3 - 1/4 + 1/5 - 1/6 + ... = ln 2

Therefore, x-coordinate = ln 2

Y-coordinate (north-south):
North movements: 1/2, 1/6, 1/10, ... = (1/2)(1 + 1/3 + 1/5 + ...)
South movements: 1/4, 1/8, 1/12, ... = (1/4)(1 + 1/2 + 1/3 + ...)

This series converges to π/4.

Final answer:
The ant approaches position (ln 2, π/4) ≈ (0.693, 0.785)
