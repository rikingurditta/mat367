# Submanifolds

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\angles}[1]{\left\langle #1 \right\rangle}
\newcommand{\inv}[1]{#1^{-1}}
\DeclareMathOperator{\supp}{supp}
\DeclareMathOperator{\id}{id}
\DeclareMathOperator{\rank}{rank}

\newcommand{\A}{\mathcal A}
\newcommand{\RP}[1]{\R P^{#1}}
\newcommand{\CP}[1]{\C P^{#1}}

\newcommand{\x}{\mathbf x}
\newcommand{\y}{\mathbf y}
$$

## Submanifolds

Let $M$ be an $m$-dimensional manifold with Atlas $\A = \curlies{(U_\alpha, \phi_\alpha)}$.

A set $S \subseteq M$ is a **submanifold** of dimension $k \leq m$ if for every $p \in S$, there is a coordinate chart $(U, \phi)$ around $p$ so that

$$
\phi(U \cap S) = \phi(U) \cap \R^k
$$

(identifying $\R^k$ with $\R^k \times \curlies{0, ..., 0} = \R^k \times \curlies{0^{m-k}} \subseteq \R^m$

Note that a chart $(U, \phi)$ is trivially a submanifold chart if both sides of the equation above are empty.

### Submanifold charts

Let $S$ be a submanifold of $M$, and define the projection

$$
\pi: \R^m \to \R^k
$$

which projects points into the first $k$ coordinates.

Let

$$
\A' = \curlies{(U \cap S, \phi')}
$$

where $(U, \phi)$ is a submanifold chart and $\phi' = \pi \circ \phi$.

Then $\A'$ is an atlas for $S$ to make it a $k$-dimensional manifold, and the inclusion map $i: S \to M$ is smooth.

**Proof.**

First, we check that $S$ is a manifold with the given atlas. For any $(U \cap S, \phi')$, we know

$$
\begin{align*}
\phi'(U \cap S) &= \pi(\phi(U \cap S)) \\
&= \pi(\phi(U) \cap \R^k) \tag{which is open}
\end{align*}
$$

so $(U \cap S, \phi')$ is a chart.

Suppose $(U, \phi)$ and $(V, \psi)$ are submanifold charts for $S$, then we want to show that $(U \cap S, \phi')$ and $(V \cap S, \psi')$ are compatible. The transition map

$$
\psi' \circ \inv{(\phi')} : \phi'(U \cap V \cap S) \to \psi'(U \cap V \cap S)
$$

is smooth, as it is equal to the restriction of $\psi \circ \inv\phi$ to $\R^k$, which we know is smooth (and same with its inverse).

To check that $S$ is Hausdorff, we can simply use the fact that $M$ is Hausdorff to produce disjoint submanifold charts around any points $p, q \in S$.

Lastly we check that $S$ can be covered by a countable number of charts. Consider a countable atlas $\curlies{(U_\alpha, \phi_\alpha)}$ for $M$, and suppose $(U, \phi)$ is in this atlas. If we can show that $U \cap S$ is covered by a countable number of submanifold charts, then we know that $S$ can be covered by countably many.

[...]

Now to prove that the inclusion map is smooth, suppose $(U, \phi)$ is a submanifold chart for $S$ on $M$, and $(U \cap S, \phi')$ is the corresponding chart on $S$. Then $\phi \circ i \circ (\phi')^{-1}(x) = (x) \times \curlies{0^{m-k}}$, which is the inclusion map from $\R^k$ to $\R^m$, which is smooth. Thus, $i$ is smooth.

![05 inclusion map is smooth.png](05 inclusion map is smooth.png)

### Examples of submanifolds

- any open subset of an $m$-dimensional manifold $M$ is an $m$-dimensional submanifold
- $\R^k \subset \R^m$
- $S^k \subset S^m$
- $\RP{k} \subset \RP{n}$
- $\CP{k} \subset \CP{n}$

### Graphs

Suppose $M$ and $N$ are $m$ and $n$-dimensional manifolds with atlases $\curlies{(U_\alpha, \phi_\alpha)}$ and $\curlies{(V_\beta, \psi_\beta)}$, then $N \times M$ is the **product manifold** with atlas $\curlies{(V_\beta \times U_\alpha, \psi_\beta \times \phi_\alpha)}$.

If $F: M \to N$ is a smooth function, then

$$
\text{graph}(F) = \curlies{(F(p), p) : p \in M} \subseteq N \times M
$$

is an $m$-dimensional submanifold of $N \times M$.

**Proof.**

Suppose $(F(x), x) \in \text{graph}(F)$. Then let $(U, \phi)$ be a chart for $M$ around $x$ and $(V, \psi)$ be a chart for $N$ around $F(x)$. Let $W = V \times U$ and $\Phi : W \to \R^{m + n}$, where 

$$
\Phi(y, x) = (\phi(x), \psi(y) - \psi(F(x)))
$$

This is a chart for $N \times M$: if we define

$$
\begin{align*}
f(y, x) &= (\phi(x), \psi(y)) \\
g(x, y) &= (x, y - (\psi \circ F \circ \inv\phi)(x))
\end{align*}
$$

then $f$ is a chart and $g$ is a diffeomorphism, so $\Phi = g \circ f$ is a chart as well.

Furthermore, since $\psi$ is injective, we know that $\Phi(y, x) \in \R^{m} \times \curlies{0^n}$ if and only if $y = F(x)$, i.e. if and only if $(x, y) \in \text{graph}(F)$. Thus, it is a submanifold chart for $\text{graph}(F)$.

#### Implicit submanifolds

Let $f : \R^n \to \R$ be a map such that $\nabla f(\x) \neq 0$ for any $\x$. Then $\inv f\curlies{0}$ is a submanifold of $\R^n$.

This is because by the implicit function theorem, for every $\x$ so that $f(\x) = 0$, we can find a function $F: \R^{n-1} \to \R$ so that $\inv f\curlies{0}$ is locally the graph of $F$ around $\x$. Therefore, $\inv f \curlies 0$ is a union of graphs, so it is submanifold.

### Restrictions to submanifolds

If $F: M \to N$ is smooth and $S \subseteq M$ is a submanifold, then $F\vert_S: S \to N$ is smooth, since $F\vert_S = F \circ i$.

[...]

## Submanifold topology

Let $S$ be a submanifold of $M$, then $U' \subseteq S$ is open if and only if $U' = U \cap S$ for some open set $U \subseteq M$. This means that submanifolds inherit the subspace topology.

($\Leftarrow$) Let $U$ be an open subset of $M$, and let $U' = U \cap S$. Let $(V, \psi)$ be a submanifold chart for $S$, and consider the associated chart $(V \cap S, \psi')$ in the atlas for $S$. Then we want to show that $\psi'(U' \cap (V' \cap S'))$ is open. But we know

$$
\begin{align*}
\psi'(U' \cap (V \cap S) &= \psi'(U \cap V \cap S) \\
&= \pi(\psi(U \cap V \cap S)) \\
&= \pi(\psi(U \cap V) \cap (\R^k \times \curlies{0^{m-k}})) \\
&= \psi(U \cap V) \cap (\R^k \times \curlies{0^{m-k}}) \\
&= [...]
\end{align*}
$$

($\Rightarrow$) Let $U'$ be an open subset of $S$, then we want to find an open subset $U$ of $M$ so that $U' = U \cap S$. To do this, suppose the charts $\curlies{(V_\alpha, \psi_\alpha)}$ cover $S$, then let

$$
U = \bigcup_\alpha \inv\psi_\alpha(\psi'_\alpha(U' \cap V_\alpha) \times \R^{m-k})
$$

For any $\alpha$, $V_\alpha$ is open, so $U' \cap V_\alpha$ is open in $S$, so $\phi'(U' \cap V_\alpha)$ is open in $\R^k$. This means that $\phi'(U' \cap V_\alpha) \times \R^{m-k}$ is open in $\R^m$, so $\inv\phi_{\alpha}(\phi'(U' \cap V_\alpha) \times \R^{m-k})$ is open in $M$. This is true for every $\alpha$, and a union of open sets is open, so $U$ is open.

Furthermore, note that for any $\alpha$,

$$
\phi(S \cap V_\alpha) = \phi'(S \cap V_\alpha) \times \curlies{0^{m-k}}
$$

This helps us see that

$$
\begin{align*}
U \cap S &= ... \\
&= ... \\
&= U'
\end{align*}
$$


### Compact submanifolds

As a corollary of $S$ inheriting the subspace topology, $S$ is a compact manifold if and only if it is compact as a subset of $M$.

## Checking submanifolds

### The derivative

Let $U \subseteq \R^m$ and $V \subseteq \R^n$ be open subsets. For $F \in C^\infty(U, V)$, the **derivative** of $F$ at $p \in U$ is the linear map

$$
\begin{align*}
D_p F: \R^m &\to \R^n \\
v &\mapsto \frac{d}{dt}\Big\vert_{t=0} F(p + tv)
\end{align*}
$$

so $D_p F$ is the linear map corresponding to the Jacobian matrix of $F$ at $p$.

### Rank for functions between Euclidean spaces

The **rank** of $F$ at $p$, $\rank_p F$, is the rank of $D_p F$.

Let $F \in C^\infty(V, W)$ and $G \in C^\infty(U, V)$ for open sets $U \subseteq \R^\ell$, $V \subseteq \R^m$, $W \subseteq \R^n$. Then we have

- for all $p \in U$, $\rank_p F \leq \min(\ell, m)$
- by the chain rule, $D_p(F \circ G) = D_{G(p)} F \circ D_p G$
- if $G$ is a diffeomorphism, then $\rank_p(F \circ G) = \rank_{G(p)} F$
- if $F$ is a diffeomorphism, then $\rank_p(F \circ G) = \rank_p G$

### Rank for $C^\infty(M, N)$

If $F \in C^\infty(M, N)$ and $(U, \phi)$, $(V, \psi)$ are charts for $M$ and $N$, then the rank of $F$ at $p \in M$ is

$$
\rank_p F = \rank_{\phi(p)} \psi \circ F \circ \inv\phi
$$

$F$ has **maximal rank** at $p \in M$ if $\rank_p F = \min(\dim M, \dim N)$.

## Smooth maps of maximal rank

### Inverse function theorem on $\R^m$

Let $U, V$ are open subsets of $\R^m$ and $F \in C^\infty(U, V)$. Let $p \in U$ be a point where $D_p F$ is invertible. Then there exists an open neighbourhood $U_1 \subseteq U$ of $p$ such that $F\vert_{U_1}: U_1 \to F(U_1)$ is a diffeomorphism.

### Inverse function theorem on manifolds

Let $M, N$ be $m$-dimensional manifolds, and $F \in C^\infty(M, N)$. Let $p \in M$ be a point at which $\rank_p F = m$. Then there exists an open enighbourhood $U \subseteq M$ of $p$ such that $F\vert_U: U \to F(U)$ is a diffeomorphism.

### Local diffeomorphisms

A function $F: M \to N$ is a local diffeomorphism if $\rank_p F = m$ for every $p \in M$, or equivalently, every $p \in M$ has an open neighbourhood $U_p$ so that $F \vert_{U_p}$ is a diffeomorphism onto its image.