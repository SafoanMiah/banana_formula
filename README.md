<div align="center">
   <h1>BANANA Formula</h1>
   
   <b> VERY IMPORTANT NOTICE: This is as a joke, please dont take it seriously)** </b>
   <img src="https://github.com/user-attachments/assets/4bc3df09-cc20-4885-87d8-4001c7190040">
</div>

<div><h2>1. Explanation:</h2></div>

Take the banana to be laying across a horizontal axis over its physical center (back of the banana).  
* We can model the inner (top) concave curvature as the outer part, while the inner is the bottom.  
* The difference in $\left([f_{\text{top}}(x)]^2 - [f_{\text{bottom}}(x)]^2\right)$ gives the area of each cross-section.  
* Integrating the difference along the length of the banana gives the total volume.

<div><h2>2. Banana Volume Formula:</h2></div>

$$
BV = \pi \int_{a}^{b} \left( [f_{\text{top}}(x)]^2 - [f_{\text{bottom}}(x)]^2 \right) dx
$$

* $f_{top}(x)$ : function describing the inner top curve of the banana
* $f_{bottom}(x)$: function of outer bottom curve
* $[a, b]$: limits along x-axis from one end of the banana to another

<div><h2>3. Curves Model</h2></div>
Lets assume the bananas top and bottom curves can be aproximated by parabolas:

$$
f_{\text{top}}(x) = R + k \sin\left(\frac{\pi x}{L}\right)
$$

$$
f_{\text{bottom}}(x) = R - k \sin\left(\frac{\pi x}{L}\right)
$$


<div><h2>4. Final Volume</h2></div>
1: top | 2: bottom

$$
BV = \pi \int_{0}^{L} \left( \left[R_{1} + k_{1} \sin\left(\frac{\pi x}{L_{1}}\right)\right]^2 - \left[R_{2} - k_{2} \sin\left(\frac{\pi x}{L_{2}}\right)\right]^2 \right) dx
$$


$$R: \text{is the average radius.}$$
$$k: \text{is how much the banana extrudes outwards.}$$
$$L: \text{is the length of the banana.}$$


<div><h2>5. Simplifications:</h2></div>
1. Expand the squares:
   
$$
\left[R_{1} + k_{1} \sin\left(\frac{\pi x}{L_{1}}\right)\right]^2 = R_{1}^2 + 2R_{1}k_{1} \sin\left(\frac{\pi x}{L_{1}}\right) + k_{1}^2 \sin^2\left(\frac{\pi x}{L_{1}}\right)
$$

$$\left[R_{2} - k_{2} \sin\left(\frac{\pi x}{L_{2}}\right)\right]^2 = R_{2}^2 - 2R_{2}k_{2} \sin\left(\frac{\pi x}{L_{2}}\right) + k_{2}^2 \sin^2\left(\frac{\pi x}{L_{2}}\right)$$

<div><h2>6. Subtract the expressions</h2></div>

$$
\left(R_{1}^2 - R_{2}^2\right) + 2R_{1}k_{1} \sin\left(\frac{\pi x}{L_{1}}\right) + k_{1}^2 \sin^2\left(\frac{\pi x}{L_{1}}\right) - 2R_{2}k_{2} \sin\left(\frac{\pi x}{L_{2}}\right) - k_{2}^2 \sin^2\left(\frac{\pi x}{L_{2}}\right)
$$

<div><h2>5. Seperating each term for integration</h2></div>

$$\int_{0}^{L} (R_{1}^2 - R_{2}^2) \, dx = (R_{1}^2 - R_{2}^2) L$$

$$\int_{0}^{L} 2R_{1}k_{1} \sin\left(\frac{\pi x}{L_{1}}\right) \, dx$$

$$\int_{0}^{L} k_{1}^2 \sin^2\left(\frac{\pi x}{L_{1}}\right) \, dx$$

$$\int_{0}^{L} -2R_{2}k_{2} \sin\left(\frac{\pi x}{L_{2}}\right) \, dx$$

$$\int_{0}^{L} -k_{2}^2 \sin^2\left(\frac{\pi x}{L_{2}}\right) \, dx$$


<div><h2>7. Evaluating the integrals involving $sin^2$ and $sin$ use the following</h2></div>

$$\int \sin(ax) \, dx = -\frac{1}{a} \cos(ax)$$

$$\int \sin^2(ax) \, dx = \frac{x}{2} - \frac{\sin(2ax)}{4a}$$


<div><h2>8. Python Script</h2></div>

```py
import numpy as np
from scipy.integrate import quad

# with average values
def banana_volume(R1=2.5, k1=0.5, L1=19, R2=2.6, k2=0.5, L2=20):
    def integrate(x): #integrate over range
        top_curve = R1 + k1 * np.sin(np.pi * x / L1)
        bottom_curve = R2 - k2 * np.sin(np.pi * x / L2)
        return (top_curve**2 - bottom_curve**2)

    volume, x = quad(integrate, 0, L1)
    return np.pi * volume

volume = banana_volume()
print(f"Volume of your banana is aprox: {volume:.2f}^3 cm.")

R1 = float(input("Average radius of the top curve (in cm):              "))
k1 = float(input("Top curve extrusion (in cm):                          "))
L1 = float(input("Length of the banana for the top curve (in cm):       "))

R2 = float(input("Average radius of the bottom curve (in cm):           "))
k2 = float(input("Bottom curve extrusion (in cm):                       "))
L2 = float(input("Length of the banana for the bottom curve (in cm):    "))
```

---
*This is all Jack's fault dc: `charlatansfolly`*
