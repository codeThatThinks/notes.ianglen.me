---
title: Common Laplace Transforms
parent: Math
---

# Common Laplace Transforms

Definition:
$\displaystyle F(s) = \mathcal{L}\{f(t)\} = \int_0^\infty e^{-st}f(t)dt$


## Common Transforms

| f(t)               | F(s)                                                         |
|--------------------|--------------------------------------------------------------|
| $1$                | $\frac{1}{s}$                                                |
| $t^n$              | $\frac{n!}{s^{n + 1}}$ for $n = \{n \in \mathbb{Z}: n > 0\}$ |
| $e^{at}$           | $\frac{1}{s - a}$                                            |
| $sin(kt)$          | $\frac{k}{s^2 + k^2}$                                        |
| $cos(kt)$          | $\frac{s}{s^2 + k^2}$                                        |
| $\frac{d}{dt}$     | $sF(s) - f(0)$                                               |
| $\frac{d^2}{dt^2}$ | $s^2F(s) - sf(0) - f'(0)$                                    |
| $\frac{d^3}{dt^3}$ | $s^3F(s) - s^2f(0) - sf'(0) - f''(0)$                        |
| $\int_0^t f(x)dx$  | $\frac{F(s)}{s}$                                             |


## Common Operational Transforms

| f(t)               | F(s)                         |
|--------------------|------------------------------|
| $kf(t)$            | $kF(s)$                      |
| $f_1(t) + f_2(t)$  | $F_1(s) + F_2(s)$            |
| $e^{at}f(t)$       | $F(s - a)$                   |
| $f(t - a)U(t - a)$ | $e^{-as}F(s)$ for $a > 0$    |
| $t^nf(t)$          | $(-1)^n\frac{d^n}{ds^n}F(s)$ |
| $(f \ast g)(t)$    | $F(s)G(s)$                   |
