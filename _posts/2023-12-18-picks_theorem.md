---
layout: post
title: Pick's Theorem
date: 18-12-2023
description: An elegant theorem on 2-D integer lattices
tags: Math
featured: false
toc:
  sidebar: left
---

> Given a Simple polygon with its points on a 2D integer lattice, find the **Number of Lattice Points** interior to the polygon.

*Note:* A lattice is just a set $$\{(x, y): x, y\text{ are both integers} \}$$

The Premise:

- Calculating the area of the polygon
- Finding the number of boundary points
- Using a very interesting theorem to get our answer

Good luck reading!

---

## Area of a general polygon

#### Area of a triangle

A triangle is a nice convex figure, which allows us to compute its area in a clean manner. The magnitude of the cross product $$\vec a \times \vec b$$ gives us the area of the parallelogram with sides along $$\vec a$$ and $$\vec b$$.

For a triangle with coordinates at $$\vec p_1 = (x_1, y_1), \vec p_1 = (x_2, y_2), \vec p_1 = (x_3, y_3)$$, the area would be half the area of the parallelogram formed by $$\vec p_1 - \vec p_2$$ and $$\vec p_1 - \vec p_3$$, which is:

$$
A_{123} = \frac 12 mag((\vec p_1 - \vec p_2) \times (\vec p_1 - \vec p_3)) = abs \frac 12 \left (  (x_2 - x_1) (y_3 - y_1) - (y_2 - y_1) (x_3 - x_1) \right )
$$

This can be written succintly as $$\boxed{ \frac 12 abs \left ( \sum_{i = 1} ^ 3 x_{i} y_{i + 1} - x_{i + 1} y_i \right )}$$, with the indices wrapping modulo $$3$$ (i.e. $$x_4 = x_1, y_4 = y_1$$).

*Note:* we will assume throughout that $$x_{n + 1} = x_1$$, i.e. indices wrap modulo $$n$$.

---

#### Area of a polygon

A natural suggestion for the area of a $$n$$-sided polygon might be this:
1. Divide up the polygon into triangles. This division will be of the following form: We pick a "base point" say $$\vec p_1$$, sort the points in anti-clockwise order of their angles from the fixed base point and iterate over the base line, which would be the line joining $$(\vec p_2 \text{ and } \vec p_3), (\vec p_3 \text{ and } \vec p_4) \dots (\vec p_{n - 1} \text{ and } \vec p_n)$$ respectively.
2. Sum up the areas of each of the triangles

This seems reasonable but has a slight caveat. It works only for convex polygons. In case of concave polygons, we might be overcounting the areas!

Now, let's think about the ominous $$abs$$ at the front and try to tackle it. Let's just remove the $$abs$$ and see what it really means. It just means that we'd take the signed area, i.e. the order in which we take our vectors matters! This would work only if $$\vec p_1 - \vec p_2$$ and $$\vec p_1 - \vec p_3$$ are anti-clockwise in order for each of the polygons.

In the off-chance that $$\vec p_1 - \vec p_i$$ and $$\vec p_1 - \vec p_{i + 1}$$ are clock-wise, that can only indicate non-convexity. But in that case, we would want to subtract the area anyways! So our signs are accounted for, and we're golden.


Finally, our area is ($$S_{ijk}$$ indicates the signed area of the triangle formed by the points $$P_i, P_j, P_k$$):

$$
S = S_{123} + S_{134} + \dots + S_{1(n - 1)n} =

\frac 12  \sum_{i = 2}^{n - 1} \left ((-x_{i} y_1 + x_{i + 1} y_1 + x_1 y_{i} - x_{i + 1} y_{i} - x_1 y_{i + 1} + x_{i} y_{i + 1} ) \right )
$$

Have you spotted it yet? Most of the terms in the above expression cancel out. $$-x_{i} y_1$$ would cancel out with $$x_{i + 1} y_1$$ in most of the cases, except when $$i = 2$$ or $$i = n - 1$$. 

Using this:

$$
S = \frac 12 \left (-x_2 y_1 + x_n y_1 + x_1 y_2 - x_1 y_n \sum_{i = 2}^{n - 1} (- x_{i + 1} y_{i} + x_{i} y_{i + 1})  \right )
= \boxed{\frac 12 \left ( \sum_{i = 1} ^ n x_{i} y_{i + 1} - x_{i + 1} y_i \right )}
$$

And yes, $\vec p_{n + 1} = \vec p_1$, the indices do wrap around.

We generally don't care about the order of the points (i.e. clockwise or anti-clockwise), so to avoid confusion, let's put a modulus on the above expression: $$S = \boxed{\frac 12 abs \left ( \sum_{i = 1} ^ n x_{i} y_{i + 1} - x_{i + 1} y_i \right )}$$

---

## Number of boundary points

#### Number of lattice points between a point and the origin

Consider a point $$\vec p_1 = (x_1, y_1)$$, we will find the number of lattice points between the origin and $$\vec p$$ (exclusive of both).

The equation of this line is $$\frac{x_1}{x} = \frac{y_1}{y}$$.

To start with, if we set the above ratio to be equal to the $$g = \gcd(x_1, y_1)$$, it certainly satisfies the equation. By definition, $$x = \frac{x_1}{g}$$ and $$y = \frac{y_1}{g}$$ are certainly integral.

On the same token, $$(k \frac{x_1}{g}, k \frac {y_1}g), 1 \le k \le g$$ are also integral points satisfying the above equation, so they also work!

We find $$g - 1$$ many such points, for each of the values of $$k$$.

*Note: We take the gcd of any two numbers (positive of negative) to be only positive. Also note that $$\gcd(0, c) = c$$*

###### Exercise: Prove that there aren't any more integral points.

---

#### Number of lattice points between two points

We did it for a point and the origin, for two general points $$\vec p_1, \vec p_2$$, we could just do a coordinate shift and conclude that the number of lattice points is $$\gcd(x_2 - x_1, y_2 - y_1) - 1$$.

---

#### Number of boundary points in a Polygon

Now, let's do this for our polygon. The number of boundary points excluding the vertices would just be $$\sum_{i = 1}^n (\gcd(x_{i + 1} - x_i, y_{i + 1} - y_i) - 1)$$, and including our vertices, our final expression is simply $$\boxed{\sum_{i = 1}^n \gcd(x_{i + 1} - x_i, y_{i + 1} - y_i)}$$

---

## Pick's Theorem

For a simple polygon with Area $$A$$, number of boundary points $$b$$ and number of interior points $$i$$,

$$
\boxed{A = i + \frac b2 - 1}
$$

This theorem is not very intuitive but is vaguely reminiscent of Euler's characteristic for plane graphs.

Let's get into the proof. Consider Pick's function $$f$$ for a polygon $$P$$
$$
f(P) = A - (i + \frac b2 - 1)
$$

We will prove that this function is identically $$0$$.

*Note:* This function is coordinate-transformation invariant (as long as the shift is by an integer amount, of course).

---

#### Rectangle with edges along the axes

Consider a rectangle with $$R$$ vertices $$(0, 0), (0, x), (x, y), (0, y)$$.

Let's calculate various quantities:
$$
b = 2 (x + y)
A = xy
i = (x - 1) (y - 1)
$$

$$f(R) = xy - ((xy - x - y + 1) + \frac{2(x + y)}2 - 1) = 0$$

---

#### Additivity of Pick's Function

Consider two polygons $$P_1, P_2$$ which share atleast one edge.

Let $$f(P_1) = A_1 - (i_1 + \frac {b_1}2 - 1), f(P_2) = A_2 - (i_2 + \frac {b_2}2 - 1)$$
Now, for the combined polygon $$P$$, we observe that it has the combined area of the two initial polygons. All the boundary points in common between the two polygons become interior points of the new polygon.

From this, we observe that the sum of number of boundary points and the number of interior points remain the same (since there is a $$\frac 12$$ which multiplies number of boundary points)

This lets us conclude that $$f(P) = f(P_1) + f(P_2)$$.

###### General triangle

###### Triangle with two sides along axes

Consider a rectangle $$R$$ with edges along axes. By utilizing the diagonal, let's split it up into two triangles ($$T_1, T_2$$). Note that by symmetry, the area, number of boundary points, the number of interior points, and hence the Pick's function for the two triangles are the same.

$$
0 = f(R) = f(T_1) + f(T_2) \implies f(T_1) = 0
$$

For a general triangle with vertices along lattice points, look at the below construction and conclude that the Picks' function is zero.

#### Putting it all together

For a general polygon, we can divide it up into smaller triangles, each of which has Pick's function zero. Now, by additivity of Pick's function, Pick's function of the general polygon is $$0$$.

We're done!

> The above theorem enables us to find the number of interior points, if we know the area and the number of boundary points. We're done!

## Addenda

<!-- A general polygon $$P$$ with $$h$$ holes bounded by simple integer polygons, disjoint from each other and from the boundary, has area
$$A = i + \frac b2 + h − 1$$ -->

Why is all this useful?

It it very useful, but doesn't need to be. I won't go into the applications here. Math can be studied just for the sake of it!

<!-- 
<html lang="en">
<head>
  <meta charset="UTF-8">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
  <style>
    body {
      margin: 10;
      padding: 0;
    }
    canvas {
      display: block;
      padding: 0;
      margin: 0;
    }
  </style>
</head>

<body>
  <script>
    let points = [];
    let numPoints = 5;
    let dragging = false;
    let draggedPoint = null;
    let gridSize = 40; // Adjust grid size as needed

    function setup() {
      let canvas = createCanvas(windowWidth, windowHeight);
      background(0); // Set background to black
      for (let i = 0; i < numPoints; i++) {
        points.push(createVector(random(width), random(height)));
      }
    }

    function draw() {
      background(0); // Set background to black
      drawGrid();
      drawLines();
      drawPoints();
    }

    function drawGrid() {
      stroke(50); // Dark gray grid lines
      for (let x = 0; x < width; x += gridSize) {
        line(x, 0, x, height);
      }
      for (let y = 0; y < height; y += gridSize) {
        line(0, y, width, y);
      }
    }

    function drawLines() {
      stroke(255); // White lines
      for (let i = 0; i < points.length - 1; i++) {
        for (let j = i + 1; j < points.length; j++) {
          line(points[i].x, points[i].y, points[j].x, points[j].y);
        }
      }
    }

    function drawPoints() {
      fill(255, 255, 0); // Yellow points
      noStroke(); // No outline for points
      for (let i = 0; i < points.length; i++) {
        ellipse(points[i].x, points[i].y, 20, 20);
      }
    }

    function mousePressed() {
      for (let i = 0; i < points.length; i++) {
        let d = dist(mouseX, mouseY, points[i].x, points[i].y);
        if (d < 10) {
          dragging = true;
          draggedPoint = i;
        }
      }
    }

    function mouseReleased() {
      dragging = false;
      draggedPoint = null;
    }

    function mouseDragged() {
      if (dragging && draggedPoint !== null) {
        // Restrict the point to move only along the grid
        let x = round(mouseX / gridSize) * gridSize;
        let y = round(mouseY / gridSize) * gridSize;
        points[draggedPoint].set(x, y);
      }
    }
  </script>
</body>
</html> -->