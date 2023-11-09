
## Continuous State & Control
The HJB equation is given by

$$
\begin{aligned}
	\frac{\partial J^*}{\partial t}(x, t) = - \text{min}_u \ \left ( \ell(x, u, t) + \frac{\partial J^*}{\partial x} f(x, u, t) \right )
\end{aligned}
$$

^222b91

## Discrete State & Actions

Bellman Equation
$$
	J^*(s_i) = \text{min}_a \left [ \ell(s_i,a) + J^*(f(s_i, a)) \right ]
$$

Optimal policy

$$
\begin{aligned}
	a = \pi^*(s_i) = \text{argmin}_a \left [  \ell (s_i,a) + J^*(f(s_i,a)) \right ]
\end{aligned}
$$

The optimal policy satisfies $J^*(s_{i+1}) - J^*(s_i) =  - \ell(s_i,a)$.

### Value Iteration
How to find the optimal cost-to-go?

Idea: start with estimate of the value function, $\hat{J}^*(s_i) = 0$ for all $s_i \in S$. Then iterate over

$$
	\hat{J}^*(s_i) = \text{min}_{a \in A} [ \ell(s_i, a) + \hat{J}^*(f(s_i, a))].
$$
