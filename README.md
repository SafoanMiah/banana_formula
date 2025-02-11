<div align="center">
   <h1>Banana Equasion</h1>
   
   <b>NOTE: This is a mathematical explanation for surface area calculation between two quadratic functions.</b>
   
   <img src="https://github.com/user-attachments/assets/4bc3df09-cc20-4885-87d8-4001c7190040">
</div>

<div><h2>1. Explanation:</h2></div>

Consider the following **quartic** equasion to model a banana
![image](https://github.com/user-attachments/assets/0a5faa2a-8341-406c-b0b9-ce589886ba39)

$$y = -A^2y^4 - B^2x^4 - C^2 - 2AB(y^2)(x^2) + 2AC(y^2) + 2BC(x^2)$$
$$\text{Factorised : }y=-\left(A\left(y\right)^{2}+B\left(x\right)^{2}-C\right)^{2\ }$$

* Increasing ( A ) would lead to a steeper curve in the ( y )-direction, affecting how the banana's shape bulges outwards.
* Increasing ( B ) would result in a broader shape, affecting how the banana's ends taper off and how wide the banana appears from the front view.
* A larger value of ( C ) would raise the entire curve, making the banana appear longer or taller, while a smaller value would lower it, potentially making it look shorter.

<div><h2>2. Area Within The Lines:</h2></div>

$$f(x,y) = (A(y)^2 + B(x)^2 - C)^2 + y$$
$$f(x,y) <0$$
<div align="center">
<img src="https://github.com/user-attachments/assets/8fd4ee2c-cb40-4054-a812-659c72417e5f">
</div>

<div><h2>3. Solving For Area</h2></div>

1. Setting  up the inequality
   * Begining with the inequality written as : $(A(y)^2 + B(x)^2 - C)^2$
   * Let $k = A(y)^2 + B(x)^2 - C$ we keed to find the region where its $<-y$
   * Since $y<0$ we can rewrite it as $-\sqrt{-y} < k < \sqrt{-y}$
   * Substituting back for $k : -\sqrt{-y} < A(y)^2 + B(x)^2 - C < \sqrt{-y}$
   * From this we can also form the following inequalities $B(x) > \sqrt{C-\sqrt{-y}-A(y)^2}$ and $B(x) < \sqrt{C+\sqrt{-y}-A(y)^2}$
2. Integration
   * We'll need a double integral with bouds being dependant on values of ( A, B, C )
   * $\text{Area} = \iint_{R} dx \, dy$
   * Where $R$ is the region defined by: $-\sqrt{-y} < A(y)^2 + B(x)^2 - C < \sqrt{-y}$ and $y < 0$
   * The exact evaluation of the integral will depend on the specific form of $A$ and $B$. However, the general approach is to integrate over the $x$-bounds for each $y$-slice, where $x_1(y)$ and $x_2(y)$ are the bounds on $x$ for each $y$.
3. Final equasion

$$\text{Solve for : } x_1(y) = B^{-1}(\sqrt{C+\sqrt{-y}-A(y)^2})$$
$$\text{Solve for : } x_2(y) = B^{-1}(\sqrt{C-\sqrt{-y}-A(y)^2})$$
$$\text{Setup and Evaluate : } \int_{-\infty}^{0} \int_{x_1(y)}^{x_2(y)} dx \, dy$$
     
<div><h2>4. Python Script for Calculation:</h2></div>

```python
import numpy as np
import scipy.integrate as integrate

# Define parameters
A = float(input('A: '))
B = float(input('B: '))
C = float(input('C: '))

# Define the bounds for x as functions of y
def x1(y):
    return (np.sqrt(C + np.sqrt(-y) - A * y**2)) / B

def x2(y):
    return (np.sqrt(C - np.sqrt(-y) - A * y**2)) / B

# Define the region of integration
def integrand(x, y):
    return 1

# Limits for y (since y < 0)
y_min = -10
y_max = 0

# Perform the double integration
sa, error = integrate.dblquad(
    integrand, 
    y_min, y_max, 
    lambda y: x1(y), 
    lambda y: x2(y)
)

print(f"Calculated Surface Area: {sa}")
```
