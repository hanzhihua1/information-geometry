## 1. Differential geometry
A **differentiable manifold** is a set $S$ with a coordinate system. The elements of $S$ are called **points**.

$S$ must also have a **coordinate system**. A coordinate system is a one to one mapping from $S \to \mathbb{R}^n$, which allows us to specify a point by a vector of $n$ real numbers.

$n$ is called the **dimension** of $S$, and write $n = \text{dim }S$.

![](https://cdn.mathpix.com/snip/images/YkivCUuLsNhXM7qGYv0-MjBCl_11ZlagxUNZodeRuX8.original.fullsize.png)

The coordinate system may not be valid everywhere, that is, there are not global. For example, it is impossible to map the surface of the sphere into flat euclidean space. 

We can view these the following way: Consider an open subset $U$ of $S$ and suppose $U$ has a coordinate system. This is a local coordinate system for points in $U$. For points not in $U$, we consider an open subset $V$, which also has another coordinate system. Repeat this process until $S$ is covered.

Let $S$ be a manifold and $\phi : S \to \R^n$ be a coordinate system for $S$. Then, $$\varphi(p)=\left[\xi^{1}(p), \cdots, \xi^{n}(p)\right]=\left[\xi^{1}, \cdots, \xi^{n}\right] = [\xi^i]$$

Each $\xi^i : S \to \R^n$ is called the **coordinate functions**.

Note: we use $\xi^i, \rho^i$ to denote both the variable and the function, like how we write $y = y(x)$.

Now, suppose we had another coordinate system $\psi = [\rho^i]$ for $S$. Then the point $p \in S$ has both the coordinates $[\xi^i(p)] = [\xi^i] \in \R^n$, and  $\left[\rho^{i}(p)\right]=\left[\rho^{i}\right] \in \mathbb{R}^{n}$. We can obtain the coordinates $[\rho^i]$ from $[\xi^i]$ in the following way:

First apply the inverse mapping $\varphi^{-1}$ to $[\xi^i]$. This is a point $p \in S$. Then apply $\psi$. The result is $[\rho^i]$. 

![](https://cdn.mathpix.com/snip/images/w69fTMZ2qKk16_2V_IzGrf9kvutRKHjybfXP8m42fRI.original.fullsize.png)

The result is:
$$\psi \circ \varphi^{-1}:\left[\xi^{1}, \cdots, \xi^{n}\right] \mapsto\left[\rho^{1}, \cdots, \rho^{n}\right]$$

This is the coordinate transformation from $\varphi=\left[\xi^{i}\right]$ to $\psi=\left[\rho^{i}\right]$.

On manifolds, we care about properties of $S$ that are *invariant under coordinate transformations.* Differential geometry analyzes the geometry of objects using differential operators with respect to a variety of functions on $S$. 

This gives rise to the following definition:

Let $S$ be a set. If there is a coordination system $A$ for $S$ which satisfies:
1. Each element $\varphi$ of $A$ is a one to one mapping from $S$ to some open subset of $\R^n$.
2. For all $\varphi \in A$, given any one to oen mapping $\psi$ the following holds:
$$ \psi \in \mathcal{A} \Longleftrightarrow \psi \circ \varphi^{-1} \text { is a } C^{\infty} \text { diffeomorphism }$$
Then we say that $S$ is a $C^\infty$ **differentiable manifold, or a manifold.**

And of course, by **diffeomorphism** we mean that $\psi \circ \varphi^{-1}$ and the inverse $\varphi \circ \psi^{-1}$ are $C^\infty$ (infinitely many times differentiable).

The class of $C^\infty$ functions on $S$ is $\mathcal{F}$. For all $f$ and $g$ in $\mathcal{F}$,we have:
- The sum $(f+g)(p) = f(p) + g(p)$
- The scaling $(cf)(p) = cf(p)$
- The product $(fg)(p) = f(p) g(p)$
These members are also in $\mathcal{F}$.

Let $[\xi^i]$ and $[\rho^i]$ be two coordinate systems. Thus
$$\sum_{j=1}^{n} \frac{\partial \xi^{i}}{\partial \rho^{j}} \frac{\partial \rho^{j}}{\partial \xi^{k}}=\sum_{j=1}^{n} \frac{\partial \rho^{i}}{\partial \xi^{j}} \frac{\partial \xi^{j}}{\partial \rho^{k}}=\delta_{k}^{i}$$
by the chain rule.

In addition, for any $C^\infty$ function $f$, we have

$$\frac{\partial f}{\partial \rho^{j}}=\sum_{i=1}^{n} \frac{\partial \xi^{i}}{\partial \rho^{j}} \frac{\partial f}{\partial \xi^{i}} \quad \text{and} \quad \frac{\partial f}{\partial \xi^{i}}=\sum_{j=1}^{n} \frac{\partial \rho^{j}}{\partial \xi^{i}} \frac{\partial f}{\partial \rho^{j}}$$

Einstein summation says that when we sum over two indicies, it is not confusing to remove the summation. We can write them like this:

$$\begin{aligned} & \frac{\partial \xi^{i}}{\partial \rho^{j}} \frac{\partial \rho^{j}}{\partial \xi^{k}} &=\frac{\partial \rho^{i}}{\partial \xi^{j}} \frac{\partial \xi^{j}}{\partial \rho^{k}} &=\delta_{k}^{i} \\ \frac{\partial f}{\partial \rho^{j}} &=\frac{\partial \xi^{i}}{\partial \rho^{j}} \frac{\partial f}{\partial \xi^{i}}, & \frac{\partial f}{\partial \xi^{i}} &=\frac{\partial \rho^{j}}{\partial \xi^{i}} \frac{\partial f}{\partial \rho^{j}} \end{aligned}$$

## 1.2 Tangent Spaces
The tangent space $T_p$ at a point $p$ is the vector space obtained by locally linearlizing $S$ around $p$. 

## 1.6 Affine Connections
