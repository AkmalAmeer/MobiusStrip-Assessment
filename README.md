# MobiusStrip-Assessment
### 🌀 **Task**

Write a Python script that models a **Mobius strip** using parametric equations and computes key geometric properties.

---

#### **1. Requirements**

* Define a `MobiusStrip` class that:

  * Accepts:

    * Radius `R` (distance from the center to the strip)
    * Width `w` (strip width)
    * Resolution `n` (number of points in the mesh)
  * Computes:

    * A 3D mesh/grid of (x, y, z) points on the surface
    * Surface area (numerically, using integration or approximation)
    * Edge length (numerically along the boundary)

---

#### **2. Parametric Equation of Mobius Strip**

Use the parametric equations:

$$
x(u, v) = \left(R + v \cdot \cos\left(\frac{u}{2}\right)\right) \cdot \cos(u)
$$

$$
y(u, v) = \left(R + v \cdot \cos\left(\frac{u}{2}\right)\right) \cdot \sin(u)
$$

$$
z(u, v) = v \cdot \sin\left(\frac{u}{2}\right)
$$

Where:

* $u \in [0, 2\pi]$
* $v \in [-w/2, w/2]$

---

#### **3. Deliverables**

* Python script (clean, modular, commented).
* 3D plot or screenshot (if you include visualization).
* A short write-up explaining:

  * How you structured the code
  * How you approximated surface area
  * Any challenges you faced


### Answers to above questions
  *How you structured the code?
      I organized everything into a single class called MobiusStrip, which keeps the code clean and modular. The idea was to encapsulate all the properties (like radius, width, and resolution) and methods (for generating the mesh, computing area and edge length, and plotting) into one object.

      The constructor handles setting up the parameters and generating the 3D coordinates using the parametric equations. I kept mesh generation as a separate method to keep things tidy. The other methods are focused and only do one thing each—either calculate surface area, compute edge length, or plot the strip. That way, the class is easy to read, modify, and test.

  * How I Approximated the Surface Area

      To approximate the surface area of the Möbius strip, I used a numerical integration approach based on surface calculus. Specifically, I calculated the partial derivatives of the surface in both directions (u and v) using NumPy’s gradient() function. Then, I computed the cross product of those two vectors at every point on the surface to get a small patch area.

      This essentially breaks the strip into tiny parallelograms, calculates the area of each, and sums them all up.

   * Any Challenges I Faced

     One tricky part was handling the Möbius strip’s twist. Because it's a non-orientable surface, the parametric equations have to be crafted carefully so they “flip” properly as you go around the loop. Fortunately, the standard parametric form using u and v worked out nicely.

     Another challenge was getting accurate area and edge calculations. Numerical integration can get rough if the mesh resolution (n) is too low, so I had to find a good balance between performance and precision. Using higher resolution helps with accuracy but slows things down and increases memory use.

      Plotting it was also a little fiddly—the Möbius strip loops over itself, so I had to make sure the mesh didn’t self-intersect visually in a weird way.
  
