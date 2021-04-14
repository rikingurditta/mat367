# Vector Fields

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

## Vector fields

A set of tangent vectors $\curlies{X_p \in T_p M : p \in M}$ (i.e. one tangent vector for every point in $M$) defines a **vector field** if and only if for every $f \in C^\infty(M)$, the function

$$
p \in M \mapsto X_p(f) \in \R
$$

is smooth.

The set of all vector fields on $M$ is denoted $\X(M)$. $\X(M)$ is a vector space.

A vector field $X$ determines a linear map $X : C^\infty(M) \to C^\infty(M)$ (we use the same letter for convenience) defined by

$$
(Xf)(p) = X_p(f)
$$

i.e., $f$ is the input of the function, and the output is the function $p \mapsto X_p(f)$.

This actually characterizes vector fields, so we can equivalently define a vector field as a map $X : C^\infty(M) \to C^\infty(M)$ satisfying
$$
X(fg) = (Xf) g + f(Xg)
$$

### Properties of vector fields

- if $X \in \X(M)$ and $h \in C^\infty(M)$, then $hX \in \X(M)$
- a derivation of an algebra $A$ is a map $D : A \to A$ so that if $a, b \in A$ then $D(ab) = D(a) b + aD(b)$ - vector fields are derivations of the algebra $C^\infty(M)$
- for every $p \in M$, $X_p$ is a tangent vector so we can express $X_p$ in terms of a coordinate chart $(U, \phi)$ around $p$ as $\ds X_p(f) = \sum_i a_i \frac{\partial}{\partial u^i} (f \circ \inv \phi)$

### Vector fields and coordinates

A collection of tangent vectors $\curlies{X_p \in T_p M : p \in M}$ defines a vector field $X$ such that $X(f)\vert_p = X_p(f)$ if and only if for all charts $(U, \phi)$, the functions $a^i : \phi(U) \to \R$ defined by

$$
X_{\inv\phi(u)} (f) = \sum_{i=1}^m a^i(u) \frac{\partial}{\partial u^i} \bigg\vert_u (f \circ \inv\phi)
$$

**Proof.**

Suppose $X$ is a vector field and $i \in \curlies{1, ..., n}$. Choose $f \in C^\infty(M)$ so that $f \circ \inv\phi$ is a projection to the $i$'th coordinate on a neighbourhood of $\phi(p)$, i.e.

$$
(f \circ \inv\phi)(u^1, ..., u^n) = u^i
$$

so $f = \pi^i \circ \phi$. Then $a^i(u) = X f \circ \inv \phi(u)$, and it is smooth since it is a composition of smoth functions.

[...]

#### Vector fields on Euclidean spaces

As a result of the theorem above, if $U \subseteq \R^m$ we know that every vector field has the form

$$
X = \sum_i a^i \frac{\partial}{\partial x^i}
$$

If $F : U \to V$ is a diffeomorphism, then

$$
(TF)\left(\sum_i a_i \frac{\partial}{\partial x^i}\right) = \sum_j \left(\sum_i a_i \frac{\partial F^j}{\partial x^i}\right) \bigg\vert_{x=\inv F(y)} \frac{\partial}{\partial y^j}
$$

Put more briefly,
$$
\frac{\partial}{\partial x^i} = \sum_j \frac{\partial y^j}{\partial x^i} \frac{\partial}{\partial y^i}
$$

### Lie bracket

In general, the composition of two vector fields $X, Y \in \X(M)$ is not a vector field. For example, let $M = \R$ and define
$$
X = Y = \frac{\partial}{\partial x} \\
\text{then } X \circ Y = \frac{\partial^2}{\partial x^2}
$$
However, the commutator $[X, Y] = X \circ Y - Y \circ X$ is always a vector field:
$$
\begin{align*}
X \circ Y (fg) &= X((Yf) \cdot g + f \cdot (Yg)) \\
&= (X \circ Y)f \cdot g + (Yf) \cdot (Xg) \\
&\quad+ (Xg) \cdot (Yf) + f \cdot (X \circ Y) g \\
Y \circ X (fg) &= (Y \circ X)f \cdot g + (Xf) \cdot (Yg) \\
&\quad+ (Yg) \cdot (Xf) + f \cdot (Y \circ X) g \\
[X, Y](fg) &= (X \circ Y - Y \circ X)(fg) \\
&= (X \circ Y)(fg) - (Y \circ X)(fg) \\
&= (X \circ Y)f \cdot g + f \cdot (X \circ Y) g \\
&\quad- (Y \circ X)f \cdot g - f \cdot (Y \circ X) g \\
&= [X, Y]f \cdot g + f \cdot [X, Y] g
\end{align*}
$$
Thus, $[X, Y]$ is a derivation, so it fits our second definition of vector fields.

$[X, Y]$ is called the **Lie bracket of $X$ and $Y$**.

### Lie bracket formula for Euclidean space

Let $U \subseteq \R^m$ and suppose $X, Y \in \X(U)$ have formulas

$$
X = \sum a^i \frac{\partial}{\partial x^i} \text{ and } Y = \sum b^i \frac{\partial}{\partial x^i}
$$

Then, computing the formula, we find that

$$
[X, Y] = \sum_i \sum_j \left(a^j \frac{\partial b^i}{\partial x^j} - b^j \frac{\partial a^i }{\partial x^j} \right) \frac{\partial}{\partial x^i}
$$

Notice that in particular,
$$
\left[\frac{\partial}{\partial x^i}, \frac{\partial}{\partial x^j} \right] = 0
$$

## $F$-related vector fields

Let $F \in C^\infty(M, N)$ be a smooth map. Vector fields $X \in \X(M)$ and $Y \in \X(N)$ are **$F$-related** if $T_p F(X_p) = Y_{F(p)}$ for all $p \in M$. If $X$ and $Y$ are $F$-related, we write $X \sim_F Y$.

### Problems with push-forwards

We define the notion of $F$-relatedness to get around the problems with trying to define push-forwards for functions $F$ which are not diffeomorphisms.

Suppose $F \in C^\infty(M, N)$ and we want to define a vector field $F_* X \in \X(N)$ as a unique push-forward of $X$.

If $F$ is not surjective, then there is some $q \in N$ so that $q \neq F(p)$, so we do not know how to define $(F_* X) \big\vert_q$.

If $F$ is not injective, then for any $q \in N$ there may be multiple points $a, b \in M$ so that $F(a) = F(b) = q$, so we do not know whether to define $F_* X\big\vert_q(g)$ to be $X(g \circ F) \big\vert_a$ or $X(g \circ F)\big\vert_b$.

If $F$ is bijective but not a diffeomorphism, then $F_* X\big\vert_q$ may not vary smoothly with $q$ across $N$.

This is why we abandon push-forwards for general smooth maps, and instead stick to $F$-relatedness.

### Properties of $F$-related vector fields

Suppose $X \sim_F Y$ and $Y \sim_G Z$. Then $X \sim_{G \circ F} Z$, since

$$
\begin{align*}
T_p (G \circ F) (X_p) &= T_{F(p)} G \circ T_{p} F(X_p) \\
&= T_{F(p)} G (Y_{F(p)}) \\
&= Z_{G \circ F(p)}
\end{align*}
$$

Note that if $X \in \X(M)$ and $F \in C^\infty(M, N)$, then there may be no $Y \in \X(N)$ so that $X \sim_F Y$. For example,

[...]

If $F : M \to N$ is a submersion, $X \in \X(M)$, and $X \sim_F 0$, then we have $T_p F (X_p) = 0$ for all $p \in M$. Then for every $p \in M$, $X_p \in \ker T_p F = T_p S$, so $X$ is tangent to the level set of $F$.

If $\pi_1 : \R^2 \to \R$ is defined by $\pi_1(x, y) = x$ and $X \sim_{\pi_1} Y$, then

[...]

Let $\pi : S^n \to \RP{n}$ denote the usual quotient map (antipodal identification), and let $F$ be the antipotdal map $F(x) = -x$. Then $X \in \X(S^n)$ and $X \sim_\pi Y$ for some $Y \in \X(\RP{n})$ if and only if $TF \circ X = X \circ F$.

### $F$-related vector fields and composition

Let $X \in \X(M)$, $Y \in \X(N)$, and $F \in C^\infty(M, N)$. Then $X \sim_F Y$ if and only if for all $g \in C^\infty(M)$, we have

$$
X(g \circ F) = Y(g) \circ F
$$

**Proof.**

$X \sim_F Y$ if and only if for all $p \in M$, $T_p F(X_p) (g) = Y_{F(p)}(g)$, so

[...]

### $F$-related vector fields and the Lie bracket

Let $F \in C^\infty(M, N)$ and assume that $X_1, X_2, Y_1, Y_2$ are vector fields so that $X_1 \sim_F Y_1$ and $X_2 \sim_F Y_2$. Then $[X_1, X_2] \sim_F [Y_1, Y_2]$.

If $g \in C^\infty(M)$, then using the lemma above,

$$
\begin{align*}
[X_1, X_2](g \circ F) &= X_1 \circ X_2(g \circ F) - X_2 \circ X_1(g \circ F) \\
&= X_1 (Y_2(g) \circ F) - X_2 (Y_1(g) \circ F) \\
&= (Y_1 \circ Y_2)(g) \circ F - (Y_2 \circ Y_1)(g) \circ F \\
\end{align*}
$$

So [...]

## Curves and flows

### Tangent to a curve

Let $J \subseteq \R$ be an open interval and $\gamma \in C^\infty(J, M)$ be a curve. Then the tangent to a curve at $p \in J$ is

$$
(\dot\gamma(p))(f) = \frac{d}{dt}\bigg\vert_p f(\gamma(p + t))
$$

### Solution curves

Let $X \in \X(M)$ be a vector field and $J \subseteq \R$ be an open interval. Then a curve $\gamma : J \to M$ is called a **solution curve** to $X$ if for all $t \in J$, $\dot\gamma(t) = X_{\gamma(t)}$.

Equivalently, $\gamma$ is a solution curve to $X$ if $\ds\frac{\partial}{\partial t} \sim_\gamma X$.

### Existence and uniqueness of solution curves

Let $U \subseteq \R^m$, and define a curve

$$
x(t) = (x^1(t), ..., x^m(t))
$$

If $X \in \X(U)$, then

$$
X = \sum_{i=1}^m a_i(x) \frac{\partial}{\partial x^i}
$$

for some $a^1, ..., a^m \in C^\infty(U)$.

Considering the tangents to the curve,

$$
\begin{align*}
\dot x(p)(f) &= \frac{d}{dt} \bigg\vert_{t=p} f(x(p + t)) \\
&= \sum_{i=1}^m \frac{\partial f}{\partial x^i} (x(p)) \cdot \frac{dx^i}{dt}(p) \\
&= [...]
\end{align*}
$$

### Existence and uniqueness of systems of ODEs in Euclidean space

Let $U \subseteq \R^m$ be open, and $a = (a^1, ..., a^m) \in C^\infty(U, \R^m)$. Then we can consider the system of ODEs:

$$
\frac{dx^i}{dt} = a^i(x(t)) \text{ for } i = 1, ..., m \\
x(0) = x_0
$$

For any $x_0 \in U$, there is an open interval $J_{x_0}$ around $0$ and a solution curve $x : J_{x_0} \to U$ of the system above. This solution is unique in that if we have any other solution $x' : J' \to U$, then $x'$ restricted to $J_{x_0}$ is equal to $x$.

We use the notation $\Phi(t, x)$ to denote the solution to the system at time $t$ so that $\Phi(0, x) = x$. Then $\gamma_x(t) = \Phi(t, x)$ is a solution curve with initial condition $\gamma_x(0) = x$.

#### Solution space and solution map

If $a \in C^\infty(U, \R^m)$, then the set

$$
\J = \curlies{(t, x) \in \R \times U : t \in J_x}
$$

is an open neighbourhood of $\curlies 0 \times U$, and the map

$$
(t, x) \in \J \mapsto \Phi(t, x) \in U
$$

is smooth.

### Existence and uniqueness of systems of ODEs on manifolds

Let $X \in \X(M)$ be a vector field. For any $p \in M$, there is an open interval $J_p \subseteq R$ and a unique solution $\gamma : J_p \to M$ of the initial value problem

$$
\dot\gamma = X_\gamma \\
\gamma(0) = p
$$

Just like in the Euclidean case, this solution is maximal in the sense that any other solution restricts to this one.

The set

$$
\J = \curlies{(t, p) \in \R \times M : t \in J_p}
$$

is an open neighbourhood of $\curlies 0 \times M$, and the map

$$
\begin{align*}
\Phi : \J &\to M \\
(t, p) &\mapsto \gamma_p(t)
\end{align*}
$$

where $\gamma_p(t) = \Phi(t, p)$ is a solution curve so that $\gamma(0) = p$.

We will see later that if $M$ is compact, then $\J = \R \times M$.

### $F$-related vector fields and solution curves

Let $F \in C^\infty(M, N)$ and assume $X \in \X(M)$ and $Y \in \X(N)$ satisfy $X \sim_F Y$. Then if $\gamma : J \to M$ is a solution curve for $X$, then $F \circ \gamma : J \to M$ is a solution curve for $Y$.

**Proof.**

Since $\gamma$ is a solution curve for $X$, we know $\ds \frac{\partial}{\partial t} \sim_\gamma X$, so $\ds (T_t \gamma) \frac{\partial}{\partial t} \bigg\vert_t = X_{\gamma(t)}$. Then,

$$
\begin{align*}
(T_t (F \circ \gamma)) \frac{\partial}{\partial t} \bigg\vert_t &= (T_{\gamma(t)} F) \circ (T_t \gamma) \frac{\partial}{\partial t} \bigg\vert_t \tag{chain rule} \\
&= (T_{\gamma(t)} F) (X_{\gamma(t)}) \tag{$\ds \frac{\partial}{\partial t} \sim_\gamma X$} \\
&= Y_{F \circ \gamma(t)} \tag{$X \sim_F Y$} \\
\end{align*}
$$

### Flows

The map $\Phi : \J \to M$ defined above is called the **flow** of $X$.

For $t \in \R$, we write $\Phi_t(p)$ as shorthand for $\Phi(t, p)$ (for suitable pairs of $t, p$).

### Composing flows

Let $X \in \X(M)$ with flow $\Phi : \J \to M$. If $(s, p) \in \J$ and $t \in \R$, then

$$
(t, \Phi_s(p)) \in \J \text{ if and only if } (t + s, p) \in \J
$$

When this is true, then we have

$$
\Phi_t \circ \Phi_s  = \Phi_{t + s}
$$

**Proof.**

[...]

### Corollary: $\Phi_t$ is a diffeomorphism

Suppose $t \in \R$. Then by the previous theorem,

$$
(\Phi_{-t} \circ \Phi_t)(p) = \Phi_0(p) = p
$$

so $\Phi_{-t} = \inv\Phi_t$. Thus $\Phi_t$ is invertible, so it is a diffeomorphism from $U$ to its image.

## Complete vector fields

We write $\J^X$ and $\Phi^X$ to indicate that these sets are for the vector field $X$.

A vector field $X \in \X(M)$ is **complete** if $\J^X = \R \times M$, i.e. the solution curves are defined on all of $\R$.

For example, the vector field
$$
X_1 = x \frac{\partial}{\partial x}
$$
on $\R$ is complete, but the vector field
$$
X_2 = x^2 \frac{\partial}{\partial x}
$$
on $\R$ is not complete.

### Vector fields with compact support are complete

Suppose $X$ has compact support. Then if $p \notin \supp X$, then 

[...]

Note that as a result, every vector field on a compact manifold is complete.

### Group of diffeomorphisms of a complete vector field

If $X \in \X(M)$ is a complete vector field, then the functions $\Phi_t$ form a one-parameter group of diffeomorphisms.

### $F$-related complete vector fields

Let $F \in C^\infty(M, N)$, and $X \in \X(M)$, $Y \in \X(N)$ are complete vetor fields with flows denoted $\Phi_t^X$ and $\Phi_t^Y$. Then $X \sim_F Y$ if and only if $F \circ \Phi_t^X = \Phi_t^Y \circ Y$.

**Proof.**

($\Rightarrow$) Suppose $X \sim_F Y$. Let $p \in M$, then the curve $\gamma(t) = \Phi_t^X(p)$ is a solution curve for $X$ starting at $p$. Then, since $X$ and $Y$ are related by $F$, $F \circ \gamma$ is a solution curve for $Y$ starting at $F(p)$.

[...]

($\Leftarrow$) Suppose $F \circ \Phi_t^X = \Phi_t^Y \circ Y$, i.e. $F(\Phi_t^X(p)) = \Phi_t^Y(Y)

## Flows and the Lie bracket

### Pushforwards and pullbacks of vector fields

If $F \in C^\infty(M, N)$ is a diffeomorphism, we can define pushforwards and pullbacs by $F$ of vector fields.

If $Y \in \X(N)$, we define the [pullback? pushforward?] $F^* : \X(N) \to \X(M)$ as the unique function so that $(F^* Y)(F^*g) = F^*(Y(g))$ for all $g \in C^\infty(N)$.

Equivalently, we choose $F^*$ so that the following diagram commutes:

[...]

## Frobenius' Theorem

### Integral submanifolds

Suppose $X_1, ..., X_r \in \X(M)$ are vector fields that are linearly independent at every point, i.e. for each $p \in M$, the tangent vectors $X_1 \big\vert_p, ..., X_r \big\vert_p$ are all linearly independent.

An $r$-dimensional submanifold $S \subseteq M$ is an **integral submanifold** if $X_1, ..., X_r$ are all tangent to $S$.

### Existence of integral submanifolds

Suppose $p \in M$ and $X_1, ..., X_r$ are linearly independent vector fields. Does an integral submanifold through $p$ exist?

If $r = 1$, then we know from our investigation of ODEs that the answer is yes.

If $r > 1$, then integral submanifolds might not exist. However, if $X_1, X_2$ are tangent to a submanifold $S$, then $[X_1, X_2]$ must also be tangent to $S$. Thus, we hypothesize that an integral submanifold exists if $[X_i, X_j] \in \text{span}\{X_1, ..., X_r\}$ for every $i, j$. **[???]**

### Lemma: Flow straightening

Let $X \in \X(M)$ and let $p \in M$ be a point where $X_p \neq 0$. Then there exists a coordinate chart $(U, \phi)$ around $p$ so that
$$
X \sim_\phi \frac{\partial}{\partial x^1}
$$
Suppose $X$ is complete. Let $N \subseteq M$ be an $m-1$-dimensional submanifold containing $p$ such that $X_p \notin T_p N$.