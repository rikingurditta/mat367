# Smooth and Continuous Functions

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\angles}[1]{\left\langle #1 \right\rangle}
\newcommand{\inv}[1]{#1^{-1}}
\DeclareMathOperator{\supp}{supp}

\newcommand{\A}{\mathcal A}
\newcommand{\RP}[1]{\R P^{#1}}

\newcommand{\x}{\mathbf x}
\newcommand{\y}{\mathbf y}
$$

## Smooth functions on manifolds

Let $M$ be a set with a maximal connected atlas, and let $f: M \to \R$ be a function.

$f$ is **smooth at $p \in M$** if there exists a chart $(U, \phi)$ such that $p \in U$ and
$$
f \circ \inv\phi : \phi(U) \to \R
$$
 is smooth at $\phi(p)$ as a function from $\R^m \to \R$. We say that $f$ is **smooth** if it is smooth at every $p \in M$. The set of all smooth functions on $M$ is $C^\infty(M)$.

Note that if $f \circ \inv\phi$ is smooth at $\phi(p)$, then $f \circ \inv\psi$ is smooth at $\psi(p)$ for every chart $(V, \psi)$ that is compatble with $(U, \phi)$ with $p \in V$.

### $C^\infty(M)$ is an algebra

An **algebra** is a vector space with a vector product and an identity.

Considering $C^\infty(M)$,

- if $f, g \in C^\infty(M)$ and $a, b \in R$, then $af + bg \in C^\infty(M)$
- if $f, g \in C^\infty(M)$ then $fg \in C^\infty(M)$
- $1 \in C^\infty(M)$

### Smooth functions are continuous

Suppose $f: M \to \R$ is smooth, then for all charts $(U, \phi)$, $f \circ \inv\phi$ is smooth. Smooth functions from $\R^m$ to $\R$ are continuous, so $f \circ \inv\phi$ is continuous. This means that for all open $V \subseteq \R$, we know that $S = (f \circ \inv\phi)^{-1}(V)$ is open. Then $S = \phi(U \cap \inv f(V))$, so $U \cap \inv f(V)$ is open in $M$ for every $U$. This means that
$$
\bigcup_{\alpha} U_\alpha \cap \inv f(V) = \inv f(V)
$$
is open. Thus, $f$ is continuous.

### Support

If $f: M \to \R$ is a function, then the **support** of $f$ is
$$
\supp(f) = \text{closure of } \curlies{x \in M : f(x) \neq 0}
$$

### Extension by zero

Let $M$ be a manifold, $U \subseteq M$ be an open subset, and $g \in C^\infty(U)$ be a function so that $\supp(g) \subseteq U$ is closed in $M$. The **extension by zero** of $g$ is the function:
$$
\begin{align*}
\widetilde g: M &\to \R \\
x &\mapsto \begin{cases}
g(x) & x \in U \\
0 & x \notin U
\end{cases}
\end{align*}
$$


The extension by zero of $g$ is smooth:

### Hausdorff manifolds have separating smooth functions

Let $M$ be a set with an $m$-dimensional maximal atlas, then $M$ is Hausdorff if and only if for all distinct $p, q \in M$, there exists a smooth function $f \in C^\infty(M)$ such that $f(p) \neq f(q)$.

($\Leftarrow$) Suppose there is a smooth function $f \in C^\infty(M)$ where $f(p) \neq f(q)$. $\R$ is Hausdorff, so we can find disjoint open neighbourhoods $W_p$ and $W_q$ of $f(p)$ and $f(q)$. $f$ is continuous, so $\inv f(W_p)$ and $\inv f(W_q)$ are open and disjoint neighbourhoods of $p$ and $q$.

($\Rightarrow$) Suppose $M$ is Hausdorff, then for all $p \neq q$, there are disjoint open neighbourhoods of $p$ and $q$. Let $U, V$ be disjoint open neighbourhoods of $p, q$.

This theorem implies that $M$ is Hausdorff if there exists a smooth injective function $F: M \to \R^K$ for some $K$.

### $\RP{n}$ is Hausdorff

We will show this by defining a smooth function $F: \RP{n} \to \R^K$ for $K = (n+1)^2$.

Let $\x$ denote $(x^0, ..., x^n)$. Then we define
$$
\begin{align*}
F: \RP{n} &\to \R^{(n + 1) \times (n + 1)}\\
(x^0 : ... : x^n) &\mapsto \frac{\x \x^T}{\abs{\x}^2}
\end{align*}
$$
This is well defined on $\RP{n}$, because
$$
\frac{\lambda \x \lambda \x^T}{\abs{\lambda \x}^2} = \frac{\lambda^2 \x \x^T}{\lambda^2 \abs{\x}^2} = \frac{\x \x^T}{\abs{\x}^2}
$$
so it does not depend on the choice of $\x$ for any equivalence class $(x^0 : ... : x^n)$ in $\RP{n}$.

## Smooth functions between manifolds

Let $M, N$ be manifolds.