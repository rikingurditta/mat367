# Differential Forms

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\angles}[1]{\left\langle #1 \right\rangle}
\newcommand{\inv}[1]{#1^{-1}}
\DeclareMathOperator{\supp}{supp}
\DeclareMathOperator{\id}{id}
\DeclareMathOperator{\rank}{rank}
\DeclareMathOperator{\Mat}{Mat}
\DeclareMathOperator{\Crit}{Crit}

\newcommand{\A}{\mathcal A}
\newcommand{\J}{\mathcal J}
\newcommand{\RP}[1]{\R P^{#1}}
\newcommand{\CP}[1]{\C P^{#1}}

\newcommand{\bzero}{\mathbf 0}
\newcommand{\a}{\mathbf a}
\newcommand{\p}{\mathbf p}
\newcommand{\u}{\mathbf u}
\newcommand{\x}{\mathbf x}
\newcommand{\y}{\mathbf y}
\newcommand{\X}{\mathfrak X}
$$

## Dual space

Let $E$ be a finite dimensional vector space.

[...]

### Cotangent space

Let $M$ be a manifold. For $p \in M$, we define the **cotangent space at $p$** to be the dual of the tangent space, i.e.
$$
T_p^* M = (T_p M)^*
$$
Elements of the cotangent space are called **cotangent vectors** or **covectors**.

For $F \in C^\infty(M, N)$, the **cotangent map** is the dual of the tangent map:
$$
\begin{align*}
T_p^* F : T_{F(p)}^* N &\to T_p^* M \\
g &\to (T_p F)^* g
\end{align*}
$$

### Differential of $f$ at $p$

For $f \in C^\infty(M)$, we define the **differential of $f$ at $p$** to be the element $(df)_p \in T_p^M$ defined by $(df)_p (v) = v(f)$ for $v \in T_p M$.

### Differential commutes with pullback (primitive)

For $F \in C^\infty(M, N)$ and $g \in C^\infty(N)$, we have
$$
d(F^* g)\big\vert_p = T^* F ((dg)_{F(p)})
$$

## 1-forms

A **1-form on $M$** is a map
$$
\begin{align*}
\alpha : \X(M) &\to C^\infty(M) \\
X &\mapsto \alpha(X) = \angles{\alpha, X}
\end{align*}
$$
This is $C^\infty(M)$-linear, i.e. if $f, g \in C^\infty(M)$ and $X, Y \in \X(M)$, then
$$
\alpha(fX + gY) = f\alpha(X) + g\alpha(Y)
$$
The vector space of 1-forms on $M$ is denoted $\Omega^1(M)$.

### 1-forms and cotangent vectors

For any $\alpha \in \Omega^1(M)$ and $p \in M$, there exists $\alpha_p \in T_p^*(M)$ so that for all $X \in \X(M)$,
$$
\alpha(X)_p = \alpha_p(X_p)
$$
**Proof**.

[...]

### Exterior derivative of a 1-form

If $f \in C^\infty(M)$, the **exterior derivative of $f$** is the 1-form $df \in \Omega^1(M)$ defined by $\angles{df, X} = X(f)$.

- if $\alpha \in \Omega^1(M)$ and $U$ is an open subset of $M$, the restriction of $\alpha$ to $U$ is a 1-form on $U$, and $\left(a \big\vert_U\right)_p = a_p$ for $p \in U$.
- if $U \subseteq \R^m$ is open and $\alpha \in \Omega^1(U)$, then $\ds \alpha = \sum_i \alpha_i dx^i$ where $\ds \alpha_i = \alpha\left(\frac{\partial}{\partial x^i}\right)$

