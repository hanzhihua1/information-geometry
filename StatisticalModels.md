# 2. Statistical Models

A probability distribution is a function $p: \mathcal{X} \to \R$. If $\mathcal{X}$ is discrete, we have 
$$p(x) \geq 0 \quad(\forall x \in \mathcal{X}) \quad \text{and} \quad \sum_{x \in \mathcal{X}} p(x)=1$$
if $\mathcal{X}$ is continuous, ($\mathcal{X} = \R^n$)
$$p(x) \geq 0 \quad(\forall x \in \mathcal{X}) \quad  \text{and} \quad \int_\mathcal{X} p(x) \mathrm{d} x=1$$

Consider a family $S$ of probability distributions on $\mathcal{X}$. We can parameterize each probability distribution by its parameters $[\theta^i]$. 

$$S=\left\{p_{\theta}=p(x | \theta) | \theta=\left[\theta^{1}, \cdots, \theta^{n}\right] \in \Xi\right\}$$

This is called a **statistical model.** A statistical model defines a statistical manifold, a unique set of parameters $[\theta^i]$ specifies a unique point on a statistical manifold.

### Example. The normal distribution:
$$\mathcal{X}=\mathbb{R}, \quad n=2, \quad \theta=[\mu, \sigma], \quad \Xi=\{[\mu, \sigma] |-\infty<\mu<\infty, 0<\sigma<\infty\}$$
$$
p(x | \theta)=\frac{1}{\sqrt{2 \pi} \sigma} \exp \left\{-\frac{(x-\mu)^{2}}{2 \sigma^{2}}\right\}
$$

### Example. The poisson distribution:
$$\mathcal{X}=\{0,1,2, \cdots\}, \quad n=1, \quad \Xi=\{\lambda | \theta>0\}$$
$$p(x ; \lambda)=e^{-\lambda} \frac{\lambda^{x}}{x !}$$

# The Fisher Metric

In parameter estimation problems, we obtain information about hte parameter from some sample from the underlying probability distribution. How much information can a sample of data provide about the unknown parameter? 

Intuitively, if an event has a small probability then the occurrence of this event brings a lot of information. This is consistent with how shannon's information content is defined, and the entropy is defined as the expected value of information content.

For a random variable $X ~ p(x|\theta)$, if $\theta$ were the true value of the parameter, we expect the likeihood function $\ell(x|\theta)$ to be large. This means that the derivative $\partial_\theta \ell(x|\theta)$ should be close to zero. This is the basic idea behind MLE. Define $l(x | \theta)=\log f(x | \theta)$ to be the **log likelihood function**.


$$
l^{\prime}(x | \theta)=\frac{\partial}{\partial \theta} \log f(x | \theta)=\frac{f^{\prime}(x | \theta)}{f(x | \theta)}
$$

Again, if $\partial_\theta \ell(x|\theta) \approx 0$, then it is expected and does not provide any information. But if $| \partial_\theta \ell(x|\theta)| \gg 0$, or $(\partial_\theta \ell(x|\theta))^2 \gg 0$, then the random variable provides a lot of information about $\theta$.

This might seem a little weird that shannon entropy and fisher information are defined so differently, one is defined through MLE and the other basically originates from counting bits. But the gist is that both of them measure information from a random variable specified by $\theta$. That is, both fisher information and shannon information depend only on $\theta$ and nothing else.

If we recall that a random variable is basically a probability distribution, and note that all definitions of entropy do not depend on $x$ but $\theta$, then it works out.

### The fisher information

Let $S=\left\{p_{\theta} | \theta \in \Xi\right\}$ be a statistical model. Given a point $\theta \in \Xi$, the **Fisher information matrix** of $S$ at $\theta$ is the $n \times n$ matrix $[g_{ij}(\theta)]$.

$$g_{i j}(\theta) \stackrel{\text { def }}{=} E_{\theta}\left[\partial_{i} \ell_{\theta} \partial_{j} \ell_{\theta}\right]=\int \partial_{i} \ell(x | \theta) \partial_{j} \ell(x | \theta) p(x | \theta) \mathrm{d} x$$

where $\partial_{i} \stackrel{\text { def }}{=} \frac{\partial}{\partial \theta^{\prime}}$, and $\ell_{\theta}(x)=\ell(x | \theta)=\log p(x | \theta)$. $\ell$ is the log likelihood.

$E_\theta$ denotes the expectation with respect to the distribution $p_\theta$, $E_{\theta}[f] \stackrel{\text { def }}{=} \int f(x) p(x | \theta) \mathrm{d} x$.

We can also write the fisher information as:

[https://people.missouristate.edu/songfengzheng/Teaching/MTH541/Lecture%20notes/Fisher_info.pdf](https://people.missouristate.edu/songfengzheng/Teaching/MTH541/Lecture%20notes/Fisher_info.pdf)

[https://web.stanford.edu/class/stats311/Lectures/lec-09.pdf](https://web.stanford.edu/class/stats311/Lectures/lec-09.pdf)

## Relation between fisher information and KL divergence

The fisher information metric is important because when the parameters are sufficiently close, the KL divergence is approximated by the fisher information metric. As we said before, the KL divergence is not a true metric, but the fisher information is.

Let us show the relationship between KL and fisher information. First the KL divergence is:

$$
D\left(\theta|| \theta^{\prime}\right)=\int \log \left(\frac{p(x| \theta)}{p\left(x| \theta^{\prime}\right)}\right) p(x| \theta) dx
$$

The fisher information metric is:

$$
I(\theta)=\int\left(\frac{\partial}{\partial \theta} \log p(x| \theta)\right)^{2} p(x| \theta) d x
$$
The claim is that the fisher information matrix is the Hessian of the KL divergence at a point:
$$
\left.\frac{d^{2}}{d \theta^{2}} D\left(\theta||\theta^{\prime}\right)\right|_{\theta^{\prime}=\theta}=I(\theta)
$$

$$
\begin{aligned}
\partial_{\theta^{\prime}} D\left(\theta||\theta^{\prime}\right)= &\int-\frac{1}{p\left(x, \theta^{\prime}\right)} \partial_{\theta^{\prime}} p\left(x, \theta^{\prime}\right) p(x| \theta) d x \\
\partial_{\theta^{\prime}}^{2} D\left(\theta||\theta^{\prime}\right)=&\int\left(\frac{1}{p\left(x, \theta^{\prime}\right)^{2}}\left(\partial_{\theta^{\prime}} p\left(x, \theta^{\prime}\right)\right)^{2}-\frac{1}{p\left(x, \theta^{\prime}\right)} \partial_{\theta^{\prime}}^{2} p\left(x, \theta^{\prime}\right)\right) p(x| \theta) d x  \\
\rightarrow_{\theta^{\prime} \rightarrow \theta} &\int\left(\partial_{\theta} \log (p(x| \theta))\right)^{2} p(x| \theta) d x-\partial_{\theta}^{2} \int p(x| \theta) d x \\
=&\int\left(\partial_{\theta} \log (p(x| \theta))\right)^{2} p(x| \theta) d x-0
\end{aligned}
$$

where we used normalization: $\int p(x| \theta) d x=1$.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE5NzE0MDQ1Ml19
-->