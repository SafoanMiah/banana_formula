<div align="center">
   <h1>Surface Area Between Two Parabolas</h1>
   
   <b>NOTE: This is a mathematical explanation for surface area calculation between two quadratic functions.</b>
   
   <img src="https://github.com/user-attachments/assets/4bc3df09-cc20-4885-87d8-4001c7190040">
</div>

<div><h2>1. Explanation:</h2></div>

Consider two quadratic functions, $f(x)$ and $g(x)$, defined as:

$$f(x) = ax^2 + bx + c$$
$$g(x) = px^2 + qx + r$$

* The functions $f(x)$ and $g(x)$ represent the upper and lower curves respectively.
* The difference $f(x) - g(x)$ gives the vertical distance between the curves.
* Integrating this difference from $u$ to $v$ gives the area between the curves.

<div><h2>2. Area Between Curves:</h2></div>

$$\text{Area} = \int_{u}^{v} \left[ f(x) - g(x) \right] dx$$

Subtracting the two functions:

$$f(x) - g(x) = (a - p)x^2 + (b - q)x + (c - r)$$

Taking the derivative:

$$\left[ f(x) - g(x) \right]' = 2(a - p)x + (b - q)$$
<div><h2>4. Surface Area Formula:</h2></div>

The surface area of revolution around the x-axis is given by:

$$\text{Surface Area} = \int_{u}^{v} 2\pi \left[ f(x) - g(x) \right] \sqrt{1 + \left( \left[ f(x) - g(x) \right]' \right)^2} dx$$

<div><h2>5. Python Script for Calculation:</h2></div>

```python
import numpy as np
from scipy.integrate import quad

# Functions
f = lambda x, a, b, c: a*x**2 + b*x + c
g = lambda x, p, q, r: p*x**2 + q*x + r

def surface_area(a, b, c, p, q, r, u, v):
    def integrand(x):
        diff = f(x, a, b, c) - g(x, p, q, r)
        derivative = 2*(a - p)*x + (b - q)
        return 2 * np.pi * diff * np.sqrt(1 + derivative**2)

    area, _ = quad(integrand, u, v)
    return area
```
