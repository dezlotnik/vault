---
id: Bayes Filter
aliases:
  - Bayes Filter
tags: []
---

# Bayes Filter

> [!tip] Key Idea
> From Wikipedia: "Bayes filter, is a general probabilistic approach for
> estimating an unknown probability density function (PDF) recursively over
> time using incoming measurements and a mathematical process model. 

## Definitions

The belief over a state variable $x_t$ is $\text{bel}(x_t) = p(x_t | z_{1:t}, u_{1:t})$.
That is, the belief is the probability of the state $x_t$ given all past
measurements, $z_{1:t}$, and controls, $u_{1:t}$.

The belief before incorporating the measurement $z_t$ is denoted
$\bar{\text{bel}}(x_t) = p(x_t | z_{1:t-1}, u_{1:t})$. This is sometimes called
the prediction.

## Algorithm

The Bayes Filter is comprised of two steps:
1. Prediction. Calculate the belief over the state $x_t$ given the previous belief over
$x_{t-1}$ and the control $u_t$. This is $\bar{\text{bel}}(x_t) = \int p(x_t | u_t, x_{t-1}) \text{bel}(x_{t-1}) \mathrm{d}x$.
2. Measurement Update. Calculate the current belief by incorporating the current
measurement $z_t$. This is done via, $\text{bel}(x_t) = \eta p(z_t | x_t) \bar{\text{bel}}(x_t)$, where $\eta$ is a normalization constant.

## Derivation

We are interested in finding the current belief which is $p(x_t | z_{1:t}, u_{1:t})$.
From [[Bayes Theorem]] we know that the probability of the state given the
latest measurement is equal to 

$$
\begin{aligned}
 p(x_t | z_{1:t}, u_{1:t}) & = p(x_t | z_t, z_{1:t-1}, u_{1:t}) \\
                           & = \frac{p(x_t | z_{1:t-1}, u_{1:t}) p(z_t | x_t, z_{1:t-1}, u_{1:t})}{p(z_t | z_{1:t-1}, u_{1:t})} \\
                           & = \frac{\bar{\text{bel}}(x_t) p(z_t | x_t, z_{1:t-1}, u_{1:t})}{p(z_t | z_{1:t-1}, u_{1:t})} \\
                           & = \frac{\bar{\text{bel}}(x_t) p(z_t | x_t)}{p(z_t | z_{1:t-1}, u_{1:t})}.
\end{aligned}
$$

And via the law of total probability

$$
\begin{aligned}
\bar{\text{bel}}(x_t) & = \int p(x_t | x_{t-1}, z_{1:t-1}, u_{1:t}) p(x_{t-1} | z_{1:t-1}, u_{1:t-1}) \mathrm{d} x_{t-1} \\
                      & = \int p(x_t | x_{t-1}, z_{1:t-1}, u_{1:t}) \text{bel}(x_{t-1}) \mathrm{d} x_{t-1} \\
                      & = \int p(x_t | x_{t-1}, u_t) \text{bel}(x_{t-1}) \mathrm{d} x_{t-1}
\end{aligned}
$$
