# BANANA Formula
**(VERY IMPORTANT NOTICE: This is as a joke, please dont take it seriously)**

### Simplifications: 
1. Expand the squares:
   
$$
\left[R_{1} + k_{1} \sin\left(\frac{\pi x}{L_{1}}\right)\right]^2 = R_{1}^2 + 2R_{1}k_{1} \sin\left(\frac{\pi x}{L_{1}}\right) + k_{1}^2 \sin^2\left(\frac{\pi x}{L_{1}}\right)
$$

$$\left[R_{2} - k_{2} \sin\left(\frac{\pi x}{L_{2}}\right)\right]^2 = R_{2}^2 - 2R_{2}k_{2} \sin\left(\frac{\pi x}{L_{2}}\right) + k_{2}^2 \sin^2\left(\frac{\pi x}{L_{2}}\right)$$

2. Subtract the expressions
   
$$
\left(R_{1}^2 - R_{2}^2\right) + 2R_{1}k_{1} \sin\left(\frac{\pi x}{L_{1}}\right) + k_{1}^2 \sin^2\left(\frac{\pi x}{L_{1}}\right) - 2R_{2}k_{2} \sin\left(\frac{\pi x}{L_{2}}\right) - k_{2}^2 \sin^2\left(\frac{\pi x}{L_{2}}\right)
$$

4. Seperating each term for integration
$$\int_{0}^{L} (R_{1}^2 - R_{2}^2) \, dx = (R_{1}^2 - R_{2}^2) L$$

$$\int_{0}^{L} 2R_{1}k_{1} \sin\left(\frac{\pi x}{L_{1}}\right) \, dx$$

$$\int_{0}^{L} k_{1}^2 \sin^2\left(\frac{\pi x}{L_{1}}\right) \, dx$$

$$\int_{0}^{L} -2R_{2}k_{2} \sin\left(\frac{\pi x}{L_{2}}\right) \, dx$$

$$\int_{0}^{L} -k_{2}^2 \sin^2\left(\frac{\pi x}{L_{2}}\right) \, dx$$


4. Evaluating the integrals involving $sin^2$ and $sin$ use the following

$$\int \sin(ax) \, dx = -\frac{1}{a} \cos(ax)$$

$$\int \sin^2(ax) \, dx = \frac{x}{2} - \frac{\sin(2ax)}{4a}$$

### Script
```py
import numpy as np
from scipy.integrate import quad


def banana_volume(R1=2.5, k1=0.5, L1=19, R2=2.6, k2=0.5, L2=20):
    def integrate(x): #integrate over range
        top_curve = R1 + k1 * np.sin(np.pi * x / L1)
        bottom_curve = R2 - k2 * np.sin(np.pi * x / L2)
        return (top_curve**2 - bottom_curve**2)
    
    # Integrate over length of banana
    volume, _ = quad(integrate, 0, L1)
    return np.pi * volume

volume = banana_volume()
print(f"Volume of your banana is aprox: {volume:.2f}^3 cm.")

R1 = float(input("Average radius of the top curve (in cm):              "))
k1 = float(input("Top curve extrusion (in cm):                          "))
L1 = float(input("Length of the banana for the top curve (in cm):       "))

R2 = float(input("Average radius of the bottom curve (in cm):           "))
k2 = float(input("Bottom curve extrusion (in cm):                       "))
L2 = float(input("Length of the banana for the bottom curve (in cm):    "))

# average values
# Length (L1, L2): 18–20 cm
# Average Radius (R1, R2): 2.5–3 cm
# Top Curve Extrusion (k1): 0.5 cm
# Bottom Curve Extrusion (k2): 0.5 cm
```
