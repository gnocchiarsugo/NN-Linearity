[![arXiv](https://img.shields.io/badge/arXiv-2510.08570-b31b1b)](https://arxiv.org/abs/2510.08570)
[![Repo](https://img.shields.io/badge/GitHub-assafshocher%2FLinearizer-black?logo=github)](https://github.com/assafshocher/Linearizer)

## Math of Linearizer
Have $A$ depend on time as:
$$ g^{-1}(A_t g(x))$$

$$h(t) = tg(x_1) - (1-t)g(x_0) $$

Loss is:
$$\mathcal{L} = \left\|g(x_1)- A_t(h(t)) \right\|^2 $$

Then to sample using an ODE solver, the velocitiy is:
$$v(t) = \frac{g(x_1) - h(t)}{1-t} = \frac{A_t - \mathbf{1}}{1-t}h(t) $$
where $\mathbf{1}$ is the identity matrix. The result is easily obtained once one realizes that $h(t)$ is distant $1-t$ from $g(x_1)$ and $t$ from $g(x_0)$, at that point, since the latent space is hypothesised linear, velocity is space over time.

## Implementation
The target is still a simple checkerboard pattern. Together with the flow matchin loss, in line with the code given by the paper's authors, we add reconstruction losses.