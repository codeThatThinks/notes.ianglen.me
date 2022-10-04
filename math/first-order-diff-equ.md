---
title: First Order Differential Equations
parent: Math
---

# First Order Differential Equations

## Separable Equations

$\frac{dy}{dx} = g(x)h(y)$

To solve:

1. Rearrange: $$\frac{1}{h(y)}dy = g(x)dx$$

2. Integrate both sides: $$\int \frac{1}{h(y)}dy = \int g(x)dx$$

3. Solve for $y$

4. Lump all constants together into $c_1$


## Linear Equations

$a_1(x)\frac{dy}{dx} + a_0(x)y = g(x)$

If $g(x) = 0$, then the equation is said to be _homogeneous_, otherwise its _non-homogeneous_.

To solve:

1. Put into standard form: $$\frac{dy}{dx} + \frac{a_0(x)}{a_1(x)}y = \frac{g(x)}{a_1(x)}$$

2. $P(x) = \frac{a_0(x)}{a_1(x)}$ and $f(x) = \frac{g(x)}{a_1(x)}$

3. Determine the integrating factor: $\mu(x) = e^{\int P(x)dx}$\
__Note__: Ignore the constant when integrating $P(x)$.

4. Multiply both sides of the equation by the integrating factor: $$\mu(x)[\frac{dy}{dx} + P(x)y] = \mu(x)f(x)$$

5. Notice that the left side of the equation will always become $(\mu(x)y)'$: $$(\mu(x)y)' = \mu(x)f(x)$$

6. Integrate both sides: $$\mu(x)y = \int \mu(x)f(x)dx$$

7. Solve for $y$

8. Lump all constants together into $c_1$


## Exact Equations

$M(x, y)dx + N(x, y)dy = 0$

If $f(x, y)$ exists such that $df = \frac{\partial f}{\partial x}dx + \frac{\partial f}{\partial y}dy = M(x, y)dx + N(x, y)dy$, then $df = 0$ and $f(x, y) = c$

To solve:

1. Verify that $M_y = N_x$ or $M_x = N_y$ (whichever is easier): $$\frac{\partial}{\partial y}M(x, y) = \frac{\partial}{\partial x}N(x, y)$$

2. Integrate $M(x, y)$. The constant of integration will be replaced by a function that only depends on $y$: $$\int M(x, y)dx = \mathbf{M}(x, y) + h(y)$$

3. Integrate $N(x, y)$. The constant of integration will be replaced by a function that only depends on $x$: $$\int N(x, y)dy = \mathbf{N}(x, y) + g(x)$$

5. $h(y)$ is equal to the terms in $\mathbf{N}(x, y)$ that aren't also in $\mathbf{M}(x, y)$.

6. $g(y)$ is equal to the terms in $\mathbf{M}(x, y)$ that aren't also in $\mathbf{N}(x, y)$.

7. Determine $f(x, y)$. Terms that exist in both $\mathbf{M}(x, y)$ and $\mathbf{N}(x, y)$ exist only once in $f(x, y)$. Also include $h(y)$ and $g(y)$ in $f(x, y)$.

8. Rewrite as $f(x, y) = c$ to get an implicit solution.


## Bernoulli's Equation

$a_1(x)\frac{dy}{dx} + a_0(x)y = g(x)y^n$

If $n = 0$ or $1$, then the equation becomes linear and can be solved using the method above.

To solve:

1. Rewrite in standard form: $$\frac{dy}{dx} + \frac{a_0(x)}{a_1(x)}y = \frac{g(x)}{a_1(x)}y^n$$

2. $P(x) = \frac{a_0(x)}{a_1(x)}$ and $f(x) = \frac{g(x)}{a_1(x)}$

3. Compute $u = y^{n - 1}$. Solve in terms of $y$, then take the derivative to get $\frac{dy}{dx}$: $$u = y^{n - 1} \Rightarrow y = u^{(1 - n)}$$ $$\frac{dy}{dx} = (1 - n)u^{-n}$$

4. Substitute in $y$ and $y'$: $$(1 - n)u^{-n} + P(x)u^{(1 - n)} = f(x)(u^{(1 - n)})^n$$

5. Solve as a linear equation.

6. Substitute back in for $u$ and $u'$.


## Reduction to Separable

$y' = f(Ax + By + C)$


To solve:

1. Find a substitution of the form $u = Ax + By + C$

2. Solve $u$ in terms of $y$ and $y'$:
$$ u = Ax + By + C \Rightarrow By = u - Ax - C$$
$$y = \frac{1}{B}u - \frac{A}{B}x - \frac{C}{B}$$
$$ y' = \frac{1}{B}u' - \frac{A}{B}$$

3. Substitute in $y$ and $y'$

4. Solve as a separable equation.

5. Substitute back in for $u$


## Homogeneous Equations

_Not to be confused with homogeneous linear equations when $f(x) = 0$._

Any equation (not just a DE) is homogeneous to the degree $\alpha$ if: $f(tx, ty) = t^{\alpha}f(x, y)$

$M(x, y)dx + N(x, y)dy = 0$

If the equation has the form of an exact equation, but $M_y = N_x$, this method can be used if $M(x, y)$ and $N(x, y)$ are homogeneous to the same degree.

To solve:

1. Substitute $y = ux$ and $y' = udx + xdu$ or $x = vy$ and $x' = vdy + ydv$, whichever is easier.

2. Solve as a separable equation.

3. Substitute back in for $u$ or $v$.
