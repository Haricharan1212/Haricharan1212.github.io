---
layout: post
title: Pick's Theorem
date: 18-12-2023
description: an example of a blog post with some code
tags: math
categories: 
featured: false
toc:
  sidebar: left

---

> We will attempt to answer a very interesting problem today: Given a Simple Polygon with its points on a 2D integer lattice, find the **Number of Lattice Points** inside the Polygon.

<details markdown=1>

<summary markdown=1>#### The premise: </summary>
<!--All you need is a blank line-->
<br>

- Calculating the area of the polygon
- Finding the number of boundary points
- Using a very interesting theorem to get our answer

Good luck reading!

</details>

## Finding the Area of the Polygon:

#### Finding the area of a triangle

A triangle is a nice convex figure, which allows us to compute its area in a clean manner. The magnitude of the cross product $$\vec a \times \vec b$$ gives us the area of the parallelogram with sides along $$\vec a$$ and $$\vec b$$.

For a triangle with coordinates at $$\vec p_1 = (x_1, y_1), \vec p_1 = (x_2, y_2), \vec p_1 = (x_3, y_3)$$, the area would be half the area of the parallelogram formed by $$\vec p_1 - \vec p_2$$ and $$\vec p_1 - \vec p_3$$, which is:

$$
A_{123} = abs \frac 12 \left (  (x_2 - x_1) (y_3 - y_1) - (y_2 - y_1) (x_3 - x_1) \right )
$$

This nicely simplifies to $$abs \frac 12 \left ((-x_2 y_1 + x_3 y_1 + x_1 y_2 - x_3 y_2 - x_1 y_3 + x_2 y_3 )\right )$$, which can be written succintly as $$\boxed{ \frac 12 abs \left ( \sum_{i = 1} ^ 3 x_{i} y_{i + 1} - x_{i + 1} y_i \right )}$$, with the indices wrapping modulo $$3$$ (i.e. $$x_4 = x_1, y_4 = y_1$$).

---

A natural suggestion for the area of a $$n$$-sided polygon might be this:
1. Divide up the polygon into triangles. This division will be of the following form: We pick a "base point" with say $$\vec p_1$$, sort the points in anti-clockwise order of their angles from the fixed base point and iterate over the base line, which would be the line joining $$(\vec p_2 \text{ and } \vec p_3), (\vec p_3 \text{ and } \vec p_4) \dots (\vec p_{n - 1} \text{ and } \vec p_n)$$ respectively.
2. Sum up the areas of each of the triangles

This seems reasonable but has a slight caveat. It works only for convex polygons. In case of concave polygons, we might be overcounting the areas!

Now, let's think about the ominous $$abs$$ at the front and try to tackle it. Let's just remove the abs and see what it really means. It just means that we'd take the signed area, i.e. the order in which we take our vectors matters! This would work only if $$\vec p_1 - \vec p_2$$ and $$\vec p_1 - \vec p_3$$ are anti-clockwise in order for each of the polygons.

In the off-chance that $$\vec p_1 - \vec p_i$$ and $$\vec p_1 - \vec p_{i + 1}$$ are clock-wise, that can only indicate non-convexity. But in that case, we would want to subtract the area anyways! So our signs are accounted for, and we're golden.


Finally, our area is ($$S_{ijk}$$ indicates the signed area of the triangle formed by the points $$P_i, P_j, P_k$$):

$$
S = S_{123} + S_{134} + \dots + S_{1(n - 1)n} = \frac 12  \sum_{i = 2}^{n - 1} \left ((-x_{i} y_1 + x_{i + 1} y_1 + x_1 y_{i} - x_{i + 1} y_{i} - x_1 y_{i + 1} + x_{i} y_{i + 1} ) \right )
$$

How you spotted it yet? Most of the terms in the above expression cancel out. $$-x_{i} y_1$$ would cancel out with $$x_{i + 1} y_1$$ in most of the cases, except when $$i = 2$$ or $$i = n - 1$$. 

$$
S = \frac 12 \left (-x_2 y_1 + x_n y_1 + x_1 y_2 - x_1 y_n \sum_{i = 2}^{n - 1} (- x_{i + 1} y_{i} + x_{i} y_{i + 1})  \right )
= \boxed{\frac 12 \left ( \sum_{i = 1} ^ n x_{i} y_{i + 1} - x_{i + 1} y_i \right )}
$$

And yes, $\vec p_{n + 1} = \vec p_1$, the indices do wrap around.

We generally don't care about the order of the points (i.e. clockwise or anti-clockwise), so to avoid confusion, let's put a modulus on the above expression: $$S = \boxed{\frac 12 abs \left ( \sum_{i = 1} ^ n x_{i} y_{i + 1} - x_{i + 1} y_i \right )}$$

---

### Finding the number of boundary points

#### Finding the number of lattice points between two points

Consider a point $$\vec p_1 = (x_1, y_1)$$, we will find the number of lattice points between the origin and $$\vec p$$ (exclusive of both).

The equation of this line is $$\frac{x_1}{x} = \frac{y_1}{y}$$.

To start with, if we set the above ratio to be equal to the $$g = \gcd(x_1, y_1)$$, it certainly satisfies the equation. By definition, $$x = \frac{x_1}{g}$$ and $$y = \frac{y_1}{g}$$ are certainly integral.

On the same token, $$(k \frac{x_1}{g}, k \frac {y_1}g), 1 \le k \le g$$ are also integral points satisfying the above equation, so they also work!

We find $$g - 1$$ many such points, for each of the values of $$k$$.

*Note: We take the gcd of any two numbers (positive of negative) to be only positive. Also note that $$\gcd(0, c) = c$$*

##### Exercise: Prove that there aren't any more integral points.

We did it for a point and the origin, for two general points $$\vec p_1, \vec p_2$$, we could just do a coordinate shift and conclude that the number of lattice points is $$\gcd(x_2 - x_1, y_2 - y_1) - 1$$.

Now, let's do this for our polygon. The number of boundary points excluding the vertices would just be $$\sum_{i = 1}^n (\gcd(x_{i + 1} - x_i, y_{i + 1} - y_i) - 1)$$, and including our vertices, our final expression is simply $$\boxed{\sum_{i = 1}^n \gcd(x_{i + 1} - x_i, y_{i + 1} - y_i)}$$

### Pick's Theorem

Ok fine let's get into the theorem.



<!-- <head>
  <meta charset="UTF-8">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
  <style>body 
  {
  display: flex; 
  /* position: relative; */
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  }</style>
</head>

<body>

<script>
  let points = [];
  let numPoints = 5;
  let dragging = false;
  let draggedPoint = null;
  let gridSize = 40; // Adjust grid size as needed

  function setup() {
    createCanvas(400, 400);
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

</body>  -->