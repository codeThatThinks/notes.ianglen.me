---
title: Differential Equation Modeling
parent: Math
---

# Differential Equation Modeling

## Proportional Growth and Decay

$\frac{dx}{dt} = kx(t)$

Growth if $k > 0$, decay if $k < 0$.


### Example

A population grows proportionally. At $t = 3$ hours, the population size is 400. At $t = 10$ hours, the population size is 2000. What was the initial population size at $t = 0$?

$\frac{dP}{dt} = kP(t) \qquad P(3) = 400 \qquad P(10) = 2000 \qquad k > 0$

1. Solve the differential equation to get $P(t)$:

$$\frac{1}{P(t)}dP = kdt$$
$$\int \frac{1}{P(t)}dP = \int kdt$$
$$ln|P(t)| = kt + c$$
$$P(t) = \pm e^{kt + c}$$
$$P(t) = c_1e^{kt} \qquad c_1 = \pm e^{c}$$

2. Determine $k$ using the values given:

$$P(3) = c_1 e^{k(3)} = 400 \qquad P(10) = c_1 e^{k(10)} = 2000$$
$$c_1 = \frac{400}{e^{k(3)}} \qquad c_1 = \frac{2000}{e^{k(10)}}$$
$$\frac{400}{e^{k(3)}} = \frac{2000}{e^{k(10)}}$$
$$400e^{10k} = 2000e^{3k}$$
$$\frac{e^{10k}}{e^{3k}} = \frac{2000}{400}$$
$$e^{7k} = 10$$
$$7k = ln(10)$$
$$k = \frac{1}{7}ln(10)$$

3. And then determine $c_1$:

$$c_1 = \frac{400}{e^{(\frac{1}{7}ln(10))(3)}}$$

4. Finally, determine $P(0)$:

$$P(0) = \frac{400}{e^{(\frac{1}{7}ln(10))(3)}}e^{\frac{1}{7}ln(10)(0)}$$
$$P(0) = \frac{400}{e^{(\frac{1}{7}ln(10))(3)}}$$
$$P(0) \approx 149$$


## Newton's Law of Cooling and Warming

$$\frac{dT(t)}{dt} = k(T(t) - T_a)$$

Where $T(t)$ is the temperature of the object at time $t$ and $T_a$ is the ambient temperature.


### Example

A thermometer is taken outside where it is 5 degrees. After 1 minute, it reads 55 degrees. After 5 minutes, it reads 30 degrees. What was the initial temperature of the thermometer?

$$\frac{dT(t)}{dt} = k(T(t) - 5) \qquad T(1) = 55 \qquad T(5) = 300$$


## Logistic Growth

$$\frac{dP}{dt} = P(a - bP) \qquad a > 0 \qquad b > 0$$


### Example

A population of 1000 students is exposed to a virus. The rate of spread is proportional to the number of infected and non-infected students. Determine the number of infected students after 6 days if after 4 days, 50 students were infected.

$$\frac{dP}{dt} = P(a - bP) \qquad P(0) = 1 \qquad P(4) = 50$$
