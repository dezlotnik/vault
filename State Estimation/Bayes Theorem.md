
> [!tip] Key Idea
> Bayes theorem provides a way to update a current belief given new information.


Bayes theorem is given by,
$$
\begin{aligned}
	p(h|e) = \frac{p(h,e)}{p(e)} = \frac{p(h) p(e|h)}{p(e)} = \frac{p(h) p(e|h)}{p(h)p(e|h) + p(\neg h)p(e|\neg h)}
\end{aligned}
$$

In plain English:
> The probability of the *hypothesis*, h, given the *evidence*, e, is equal to the probability of both the *hypothesis* and the *evidence* divided by the probability of the evidence.

Or, 
$$
\begin{aligned}
	p(x|y) = \frac{p(x,y)}{p(y)} = \frac{p(x) p(y|x)}{p(y)}
\end{aligned}
$$

> The robot has observed data y. What is the probability that the robot is at state x? This probability is equal to the likelihood of both being at state x and observing data y, divided by the total likelihood of observing y at any state.

- $p(x)$ is the prior, probability of being at state $x$ before incorporating the data $y$.
- $p(y | x)$ is the posterior probability distribution. This is the probability of observing data $y$, assuming we are at state $x$. This is also called the generative model, as it describes how the evolution of the state can cause sensor measurements.


Nice video explaining Bayes Theorem:

<iframe width="560" height="315" src="https://www.youtube.com/embed/HZGCoVF3YvM?si=OlIgkgIct4ekPbZj" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

