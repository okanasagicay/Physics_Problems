Task 09 – Optimization of a Rectangle Under a Curve
Problem Statement
A rectangle is inscribed under the curve

$$
y = 3 - x^2
$$

in the first quadrant. Determine the dimensions of the rectangle with maximum area.

Theory
If the upper-right corner of the rectangle lies on the curve, then its width and height can be expressed in terms of one variable. The area then becomes a function of that variable, and the maximum can be found using calculus.

Because the rectangle lies in the first quadrant with sides along the axes:

width is $x$,
height is $y = 3 - x^2$.

Thus the area is

$$
A(x) = x(3 - x^2)
$$

Step-by-Step Solution
Area function
The area is

$$
A(x) = x(3 - x^2)
$$

Expand:

$$
A(x) = 3x - x^3
$$

Differentiate the area
$$
A'(x) = 3 - 3x^2
$$

Set the derivative equal to zero:

$$
3 - 3x^2 = 0
$$

$$
1 - x^2 = 0
$$

$$
x^2 = 1
$$

Since the rectangle is in the first quadrant, $x > 0$, so

$$
x = 1
$$

Determine the corresponding height
Substitute $x = 1$ into the curve equation:

$$
y = 3 - x^2
$$

$$
y = 3 - 1^2
$$

$$
y = 2
$$

Verify that this gives a maximum
The second derivative is

$$
A''(x) = -6x
$$

At $x = 1$,

$$
A''(1) = -6 < 0
$$

so the area is maximized there.

Final Result
The rectangle of maximum area has dimensions

$$
\text{width} = 1
$$

and

$$
\text{height} = 2
$$

Its maximum area is

$$
A_{\max} = 1 \cdot 2 = 2
$$

Interpretation
As the rectangle becomes wider, its height decreases because the top-right corner must remain on the parabola. The optimal rectangle balances these two competing effects, producing the maximum area at $(x,y) = (1,2)$.

---

