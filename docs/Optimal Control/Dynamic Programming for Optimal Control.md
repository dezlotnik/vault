---
id: Dynamic Programming for Optimal Control
aliases: []
tags: []
---

The goal is to solve the following optimization problem,

![[Optimal Control Problem Statement#^9df567]]

The value function, or cost-to-go, is

$$
\begin{aligned}
	J^*(x(t_1),t_1) = \phi(x^*(t_f),t_f) + \int_{t_1}^{t_f} \ell(x^*,u^*, t) \mathrm{d}t.
\end{aligned}
$$

The optimal cost-to-go is the cost incurred from time $t_1$ to $t_f$ assuming optimal controls along that trajectory.  The cost-to-go obeys the Hamilton Jacobi Bellman Equation,

![[Hamilton Jacobi Bellman Equation#^222b91]]

or alternatively,

$$
\begin{aligned}
	0 = \text{min}_u \ \left ( \ell(x, u, t) + \frac{\partial J^*}{\partial x} f(x, u, t) + \frac{\partial J^*}{\partial t}(x, t) \right ).
\end{aligned}
$$

The corresponding optimal policy is

$$
\begin{aligned}
	u = \pi^*(x, t) = \text{argmin}_u \left ( \ell(x, u, t) + \frac{\partial J^*}{\partial x} f(x, u, t) \right )
\end{aligned}
$$

The optimal control satisfies

$$
\begin{aligned}
	\frac{\mathrm{d}J^*}{\mathrm{d}t}(x,t) = - \ell(x, u, t)
\end{aligned}
$$

> [!tip] Optimal Rate of Change of Cost-to-Go
> Under the optimal policy, the value function, or cost-to-go, decreases at a rate equal to the cost incurred at the current state. If the current cost is high the value function will decrease rapidly.

This is a stricter condition than [[Lyapunov Stability]], where the Lyapunov
function only needs to be strictly less than zero to guarantee asymptotic
stability.
