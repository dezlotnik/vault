---
id: Dynamic Programming
aliases:
  - Dynamic Programming
tags: []
---


# Dynamic Programming

## Examples

### Minimize Steps from N to 1

Given an integer `n`, find the smallest number of steps we can take to reach
a value of 1. At each step we can do the following:
1. Subtract 1.
2. Divide by 2, if the number is divisible by 2.
3. Divide by 3, if the number is divisible by 3.

Let $N$ be the total number of steps taken to get from integer $n$ to $1$. Also,
let $s(k)$ be the value of the integer after taking $k$ steps, and let $a(k)$
be an action chosen at step $k$. Then, the problem can be formulated as

$$
\begin{aligned}
    & \text{min}_N \ \ J = \sum_{i = 0}^{N} 1 \\
    & \text{such that} \\
    & s(N) = 1, \\
    & s(0) = n, \\
    & s(k+1) = f(s(k), a(k))
\end{aligned}
$$

This is equivalent to a minimum time [[Optimal Control]] problem. We can solve
this using [[Dynamic Programming for Optimal Control]]. 

The [[Hamilton Jacobi Bellman Equation]] for discrete state and actions is

$$
	J^*(s) = \text{min}_{a} \left [ \ell(s,a) + J^*(f(s, a)) \right ],
$$

where $\ell(s,a) = 1$ is the running cost, and $J^*(s)$ is the value function
representing the cost-to-go at state $s$, or the minimum number of steps to
reach 1 at integer $s$. We also have the boundary condition $J^*(1) = 0$, since
the number of steps to reach 1 from 1 is zero.

To solve for the value function at integer $s = n$, we solve the HJB equations
backwards from $s = 1$. 

```python
def possible_next_states(s):
    states = [s - 1]
    if s % 2 == 0:
        states.append(s // 2)
    if s % 3 == 0:
        states.append(s // 3)
    return states

def find_min_steps(n):
    min_steps = [0] * n
    for s in range(1, n + 1):
        if s == 1:
            min_steps[s - 1] = 0
        else:
            states = possible_next_states(s)
            min_cost = float("inf")
            for state in states:
                min_cost = min(min_cost, 1 + min_steps[state - 1])
            min_steps[s - 1] = min_cost
    return min_steps[-1]
```

### Knapsack problem
http://www.iam.fmph.uniba.sk/institute/halicka/teach/english_or.pdf

http://www.cs.umsl.edu/~sanjiv/classes/cs5130/lectures/dp.pdf

https://ecal.berkeley.edu/files/ce191/CH05-DynamicProgramming.pdf

https://medium.com/@logicdevildotcom/knapsack-problems-18b2714e0737

https://medium.com/@logicdevildotcom/dynamic-programming-applied-to-graphs-f33b6b8a8247

https://apps.dtic.mil/sti/tr/pdf/ADA445180.pdf

https://bayen.berkeley.edu/sites/default/files/lecture81.pdf

In the knapsack problem, you need to pack a set of `n` items, with given weights
and values into a container with a maximum capacity with the goal of maximizing
the total value of the container.

Stated formally we want to maximize an objective function

$$
\begin{aligned}
    & \text{max value} = \sum_{i = 0}^{n-1} v_i u_i \\
    & \text{s.t.} \sum_{i=0}^{n-1} w_i u_i \le W,
\end{aligned}
$$

where $v_i$ is the item value, $w_i$ is the item weight, $W$ is the total
capacity, and $u_i \in \{0, 1, 2, ...\}$ is the number of each item type.

To help formulate the problem, consider the definition of a new state $x(k)$,
which is the remaining capacity of the container after packing $k$ item types.
The state evolves according to the equation

$$
    x(k+1) = x(k) - w(k) u(k).
$$

For example, at $k=0$ we have packed 0 item types in the container. The remaing
capacity is $x(0) = W$. Suppose we decide to pack five items from the first item
type, which has a weight of 1. Then, $x(1) = x(0) - w(0)u(0) = W - 5$. So, after
packing the first (actually zeroth) item type the remaining capacity is
$x(1) = W - 5$.

We can now restate the problem as an optimal control problem

$$
\begin{aligned}
    & \text{max} \ \ J = \sum_{k = 0}^{n-1} v(k) u(k) \\
    & \text{such that} \\
    & x(k+1) = x(k) - w(k) u(k), \\
    & x(0) = W, \\
    & x(k) \ge 0, \\
    & u(k) \in \{0, 1, 2, \ldots \},
\end{aligned}
$$

The value function is $J^*(x(k))$ is the maximum value that can be achieved for
the remaining space in the container, $x(k)$. The HJB equation is

$$
J^*(x(k)) = \max_{u(k), \ w(k) u(k) \le x(k)}  \left ( v(k) u(k) + J^*(x(k)
    - w(k) u(k)) \right ).
$$

So, how to solve the HJB equation. For a single item we can solve the HJB
equation to get the optimal value function for that item at every possible
capacity.
We then repeat this procedure for every item.
If we find a maximum value at a particular capacity that is greater
than what we had before, then we update the optimal value function at that
capacity.

> [!question] I think this is probably closely related to Dynammic Programming for [[Graph Search]].

Here's a python implementation for the 0-1 knapsack problem. In this version
$u(k)$ can only take on values of 0 or 1.
```python
def knapsack_max_value(knapsack_max_weight, items):
    """
    Get the maximum value of the knapsack.
    """
    max_value = [0]*(knapsack_max_weight + 1)
    for item in items:
        for capacity in reversed(range(knapsack_max_weight + 1)):
            if item.weight <= capacity:
                max_value[capacity] = max(max_value[capacity],
                                          item.value + max_value[capacity - item.weight])
    return max_value[-1]
```



> [!question]
> Why do we need to iteratively update the optimal value function for this
> problem? For the "Get to 1" problem above we only needed to update the value
> function for a given state a single time. What was the fundamental difference?
