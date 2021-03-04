# Tangent Spaces

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
\newcommand{\RP}[1]{\R P^{#1}}
\newcommand{\CP}[1]{\C P^{#1}}

\newcommand{\bzero}{\mathbf 0}
\newcommand{\a}{\mathbf a}
\newcommand{\p}{\mathbf p}
\newcommand{\u}{\mathbf u}
\newcommand{\x}{\mathbf x}
\newcommand{\y}{\mathbf y}
$$

## Tangent spaces

### First definition using curves

Let $M$ be an $m$-dimensional manifold. For $p \in M$, the **tangent space** $T_p M$ is the set of all linear maps $v : C^\infty(M) \to \R$ of the form
$$
v(f) = \frac{d}{dt}\bigg\vert_{t=0} f(\gamma(t))
$$
where $\gamma \in C^\infty(J, M)$ is a smooth map with $\gamma(0) = p$ and $J \subseteq \R$ is an interval containing $0$. The elements of $T_p M$ are called **tangent vectors** to $M$ at $p$.

### Charts and tangent spaces

Let $(U, \phi)$ be a coordinate chart around $p$. A linear map $v : C^\infty(M) \to \R$ belongs to $T_p M$ if and only if it has the form
$$
v(f) = \sum_{i=1}^m a^i \frac{\partial (f \circ \inv\phi)}{\partial u^i} \bigg\vert_{\u=\phi(p)} = \a \cdot \nabla (f \circ \inv \phi)\vert_{\phi(p)}
$$
for some $\a = (a^1, ..., a^m) \in \R^m$.

As a consequence, $T_p M$ is an $m$-dimensional vector space.

**Proof.**

($\Rightarrow$) Suppose $v \in T_p M$, then for any $f \in \C^\infty(M)$,

$$
v(f) = \frac{d}{dt} \bigg\vert_{t=0} f(\gamma(t))
$$

for some $\gamma \in C^\infty(J, M)$ with $\gamma(0) = p$. Inserting $\phi$, we see that

$$
v(f) = \frac{d}{dt} \bigg\vert_{t=0} f(\inv \phi \circ \phi \circ \gamma(t))
$$

so if $\widetilde \gamma = \phi \circ \gamma$

$$
v(f) = \frac{d}{dt} \bigg\vert_{t=0} (f \circ \inv \phi)(\widetilde \gamma(t))
$$

Since $\widetilde \gamma : J \to \R^m$, we have a composition of functions between Euclidean spaces, so we can use the chain rule to see

$$
\begin{align*}
v(f) &= \sum_{i=1}^m \frac{\partial (f \circ \inv \phi)}{\partial u^i} \bigg\vert_{\u=\widetilde\gamma(0)} \frac{\partial \widetilde\gamma^i}{\partial t} \bigg\vert_{t=0} \\
&= \sum_{i=1}^m \frac{\partial (f \circ \inv \phi)}{\partial u^i} \bigg\vert_{\u=\phi(p)} a^i \\
&= \nabla (f \circ \inv \phi)\vert_{\phi(p)} \cdot \a
\end{align*}
$$

where $\ds a^i = \frac{d\widetilde\gamma^i}{dt}\bigg\vert_{t=0}$, so  $\ds \a = \frac{\partial \widetilde \gamma}{\partial t} \bigg\vert_{t=0}$. So we have shown what we wanted.

($\Leftarrow$) Suppose we have a map

$$
v(f) = v(f) = \sum_{i=1}^m a^i \frac{\partial (f \circ \inv\phi)}{\partial u^i} \bigg\vert_{\u=\phi(p)}
$$

for some $\a = (a^1, ..., a^m)$. Then we want to find a curve $\gamma$ so that

$$
v(f) = \frac{d}{dt} \bigg\vert_{t=0} f(\gamma(t))
$$

To do this, let $\gamma(t) = \inv\phi(\phi(p) + t\a)$. Then,

$$
\begin{align*}
\frac{d}{dt} \bigg\vert_{t=0} f(\gamma(t)) &= \frac{d}{dt} \bigg\vert_{t=0} f(\inv\phi(\phi(p) + t\a)) \\
&= \frac{d}{dt} \bigg\vert_{t=0} (f \circ \inv\phi)(\phi(p) + t\a) \\
&= [...]
\end{align*}
$$

so we have once again shown what we wanted.

### Second definition using charts

The previous theorem proved that we can consider an alternate definition of the tangent space: $T_p M$ is the set of all linear maps $v : C^\infty(M) \to \R$ of the form

$$
v(f) = \sum_{i=1}^m a^i \frac{\partial (f \circ \inv\phi)}{\partial u^i} \bigg\vert_{\u=\phi(p)} = \a \cdot \nabla (f \circ \inv \phi)\vert_{\phi(p)}
$$

for some $\a = (a^1, ..., a^m) \in \R^m$.

Note that this implies that $T_p M$ is an $m$-dimensional vector space, as it is spanned by the elements

$$
\frac{\partial}{\partial x^1} \bigg\vert_{p}, ..., \frac{\partial}{\partial x^m} \bigg\vert_{p}
$$

### Product rule for tangent vectors

Let $v \in T_p M$ be a tangent vector to $M$ at $p$. Then

$$
v(fg) = f(p) v(g) + v(f) g(p)
$$

Suppose $\gamma \in C^\infty(J, M)$ is such that

$$
v(h) = \frac{d}{dt}\bigg\vert_{t=0} h(\gamma(t))
$$

then

$$
\begin{align*}
v(fg) &= \frac{d}{dt}\bigg\vert_{t=0} (fg) \circ \gamma(t) \\
&= \frac{d}{dt}\bigg\vert_{t=0} (f \circ \gamma(t))(g \circ \gamma(t)) \\
&= \frac{d}{dt}\bigg\vert_{t=0} (f \circ \gamma(t)) g(p) + \frac{d}{dt}\bigg\vert_{t=0} f(p)(g \circ \gamma(t)) \tag{product rule} \\
&= v(f) g(p) + f(p) v(g)
\end{align*}
$$

As a result, if $c$ is a constant function then $v(c) = 0$. This is because $v$ is linear, so

$$
\begin{align*}
cv(f) &= v(c \cdot f) \\
cv(f) &= v(c) f(p) + c(p) v(f) \\
cv(f) &= v(c) f(p) + cv(f) \\
0 &= v(c) f(p)
\end{align*}
$$

this is true for all $f$, no matter what $f(p)$ is, so $v(c)$ must be $0$.

Another result is, if $f(p) = g(p) = 0$ then $v(fg) = 0$ regardless of $v(f)$ and $v(g)$.

### Third definition using product rule

A linear map $v : C^\infty(M) \to \R$ is an element of $T_p M$ if and only if it satisfies the product rule at $p$, i.e.

$$
v(fg) = f(p) v(g) + v(f) g(p)
$$

We need a number of lemmas to prove that this is an equivalent characterization. For the following lemmas, assume that $v : C^\infty(M) \to \R$ is a linear map that satisfies the product rule at $p$ outlined above.

#### Hadamard's lemma: First order approximation on manifolds

Let $U$ be an open ball around the origin in $\R^m$ and assume that $h \in C^\infty(U)$. Then there exist functions $h_1, ..., h_m \in C^\infty(U)$ such that

$$
h(\u) = h(\bzero) + \sum_{i=1}^m u^i h_i(\u)
$$

and these functions satisfy

$$
h_i(\bzero) = \frac{\partial h}{\partial u^i}(\bzero)
$$

**Proof.**

We can parametrize the line from $\bzero$ to $\u = (u^1, ..., u^m)$ in $\R^m$ by considering $su$ for $s \in [0, 1]$. Using this, we can apply the fundamental theorem of calculus to see that

$$
\begin{align*}
h(\u) - h(\bzero) &= \int_0^1 \frac{d}{dt}h(s\u) ds \\
&= \int_0^1 \u \cdot \nabla h(s\u) ds \tag{chain rule} \\
&= \sum_{i=1}^m u^i \int_0^1 \frac{\partial h}{\partial u^i}(s\u)ds
\end{align*}
$$

If we define each of our functions as $\ds h_i(\u) = \int_0^1 \frac{\partial h}{\partial u^i}(s\u)ds$, then

$$
\begin{align*}
h(\u) - h(\bzero) &= \sum_{i=1}^m u^i h_i(\u)
\end{align*}
$$

and

$$
h_i(\bzero) = \int_0^1 \frac{\partial h}{\partial u^i}(s\bzero)ds = \int_0^1 \frac{\partial h}{\partial u^i}(\bzero) ds = \frac{\partial h}{\partial u^i}(\bzero)
$$

as required.

#### Lemma: If $f_1 = f_2$ on a neighbourhood $U$ of $p$ then $v(f_1) = v(f_2)$

Let $f_1, f_2 \in C^\infty(M)$ be functions so that $f_1(u) = f_2(u)$ for all $u \in U$, where $U$ is some neighbourhood of $p$. Let $g = f_1 - f_2$, then $g$ is 0 on $U$. Let $\chi \in C^\infty(M)$ be a smooth function so that $\chi(p) = 1$ and $\chi(u) = 0$ for all $u \in M \setminus U$, i.e. it is a bump function for $p$ in $U$. Then $g$ is 0 on $U$ and $\chi$ is 0 on $M \setminus U$, so $g\chi$ is 0 on all of $M$, so $v(g\chi) = 0$. Then, using the product rule,

$$
\begin{align*}
0 &= v(g\chi) \\
&= g(p) v(\chi) + v(g) \chi(p) \\
&= 0 \cdot v(\chi) + v(g) \cdot 1 \\
&= v(g) \\
&= v(f_1 - f_2) \\
&= v(f_1) - v(f_2) \tag{$v$ is linear}
\end{align*}
$$

so $v(f_1) = v(f_2)$.

This shows that $v$ can equivalently be defined as a function from $C^\infty(U)$ to $\R$ rather than from all of $C^\infty(M)$ to $\R$, since all that matters is how the input function behaves in a neighbourhood around $p$.

#### Lemma: We can lift $v$ to a map $\widetilde v$ that acts on Euclidean functions which satisfies the product rule

Let $(U, \phi)$ be a chart around $p$, and let $\widetilde U = \phi(U) \subseteq \R^m$ and $\widetilde p = \phi(p)$.

Suppose $\widetilde h \in C^\infty(\widetilde U)$  then we can define the function

$$
\begin{align*}
\widetilde v : C^\infty(\widetilde U) &\to \R \\
\widetilde h &\mapsto v(\widetilde h \circ \phi)
\end{align*}
$$

(Even though $\widetilde h \circ \phi$ is in $C^\infty(U)$ rather than $C^\infty(M)$, this function is still well-defined due to the previous lemma.)

Then if $\widetilde f, \widetilde g \in C^\infty(\widetilde U)$, then

$$
\begin{align*}
\widetilde v(\widetilde f \widetilde g) &= v((\widetilde f \widetilde g) \circ \phi) \\
&= v((\widetilde f \circ \phi)(\widetilde g \circ \phi)) \\
&= (\widetilde f \circ \phi(p)) v(\widetilde g \circ \phi)) + v(\widetilde f \circ \phi)) (\widetilde g \circ \phi(p)) \\
&= \widetilde f(\widetilde p) \widetilde v(\widetilde g) + \widetilde v(\widetilde f) \widetilde g(\widetilde p)
\end{align*}
$$

so $\widetilde v$ satisfies the product rule.

#### Proof of third definition

We know that tangent vectors by our previous definition satisfy the product rule, so we know one direction of the equivalence.

For the other direction, let $(U, \phi)$ be a chart around $p$ and let $\widetilde U = \phi(U)$ and $\widetilde p = \phi(p)$. Assume without loss of generality that $\widetilde p = \bzero$.

Define $\widetilde v$ using the previous lemma. Then if $f \in C^\infty(M)$, let $\widetilde f = f \circ \inv\phi$ be its lift to Euclidean space. By Hadamard's lemma, we know that there exist functions $f_1, ..., f_m \in C^\infty(\widetilde U)$ so that

$$
\widetilde f(\u) = \widetilde f(\bzero) + \sum_{i=1}^m u^i f_i(\u) \text{ and } f_i(\bzero) = \frac{\partial \widetilde f}{\partial u^i}(\bzero)
$$

Since $\widetilde v$ satisfies the product rule, we also know that $\widetilde v(c) = 0$ for any constant function $c$. Therefore,

$$
\begin{align*}
v(f) &= v(f \circ \inv \phi \circ \phi) \\
&= \widetilde v(\widetilde f) \\
&= \widetilde v\left(\widetilde f(\bzero) + \sum_{i=1}^m u^i f_i\right) \\
&= \widetilde v(\widetilde f(\bzero)) + \sum_{i=1}^m \widetilde v(u^i f_i) \tag{$\widetilde v$ is linear} \\
&= \sum_{i=1}^m \widetilde v(u^i f_i) \tag{$\widetilde v(c) = 0$ for constant $c$} \\
&= \sum_{i=1}^m (u^i(\bzero) \widetilde v(f_i) + \widetilde v(u^i) f_i(\bzero)) \tag{product rule} \\
&= \sum_{i=1}^m (0 \cdot \widetilde v(f_i) + \widetilde v(u^i) \frac{\partial \widetilde f}{\partial u^i}) \\
&= \sum_{i=1}^m \widetilde v(u^i) \frac{\partial (f \circ \inv\phi)}{\partial u^i}
\end{align*}
$$

So if $a^i = \widetilde v(u^i)$, then

$$
v(f) = \sum_{i=1}^m a^i \frac{\partial (f \circ \inv\phi)}{\partial u^i}
$$

which is exactly the form of a tangent vector, by the second definition.

## Tangent map

Let $F \in C^\infty(M, N)$. For any $p \in M$, we define the **tangent map** to be the linear map

$$
\begin{align*}
T_p F : T_p M &\to T_{F(p)} N \\
v(g) &\mapsto v(g \circ F)
\end{align*}
$$

We can verify that this definition sends tangent vectors to tangent vectors:

Let $v \in T_p M$ and let $w = T_p F(v) \in T_{F(p)} N$.

Let $g, h \in C^\infty(N)$ and $a, b \in \R$. Then,

$$
\begin{align*}
w(ag + bh) &= v(ag \circ F + bh \circ F) \\
&= v(ag \circ F) + v(bh \circ F) \\
&= aw(g) + bw(h)
\end{align*}
$$

so $w$ is linear, and

$$
\begin{align*}
w(gh) &= v((gh) \circ F) \\
&= v((g \circ F)(h \circ F)) \\
&= (g \circ F(p)) v(h \circ F) + v(g \circ F) (h \circ F(p)) \\
&= g(F(p)) w(h) + w(g) h(F(p))
\end{align*}
$$

so $w$ satisfies the product rule at $F(p)$. Thus, $w \in T_{F(p)} N$.

### Tangent map and curves

Suppose $v \in T_p M$ is represented by a curve $\gamma : J \to M$ where $J \subseteq \R$ is an open interval around $0$. Then $(T_p F) (v)$ is represented by the curve $F \circ \gamma : J \to N$

Suppose $\ds v(g) = \frac{d}{dt}\bigg\vert_{t=0} g(\gamma(t))$, then

$$
\begin{align*}
(T_p F)(v)(g) &= v(g \circ F) = \frac{d}{dt}\bigg\vert_{t=0} (g \circ F)(\gamma(t)) \\
&= \frac{d}{dt}\bigg\vert_{t=0} g(F \circ \gamma(t))
\end{align*}
$$

which is what we wanted to show.

### Push-forwards and pull-backs

Let $F \in C^\infty(M, N)$. We can use $F$ to *transport* between certain "objects defined on $M$" and "objects defined on $N$:

- if $I \subseteq \R$ is an interval and $\gamma \in C^\infty(I, M)$ is a smooth curve, then we can define the **push-forward of $\gamma$ by $F$** as $F _\ast \gamma = F \circ \gamma$
- given $f \in C^\infty(N)$, we can define the **pull-back of $f$ by $F$** as $F^\ast f = f \circ F$

Then, using this language, if $v \in T_p M$ then the push-forward of $v$ by $F$ is $F_\ast v = (T_p F)(v) \in T_{F(p)} N$.

Note that $F_\ast v(g) = v(F^\ast g)$

### Chain rule for tangent map

Let $M, N, Q$ be manifolds and assume that $F \in C^\infty(M, N)$ and $G \in C^\infty(N, Q)$. Then if $p \in M$, then

$$
T_p (G \circ F) = T_{F(p)} G \circ T_p F
$$

This is because if $v \in T_p M$ and $g \in C^\infty(Q)$, then

$$
\begin{align*}
(T_p (G \circ F))(v)(g) &= v((g \circ G) \circ F) \\
&= (T_p F)(v)(g \circ G) \\
&= (T_{F(p)} G)((T_p F)(v))(g) \\
&= (T_{F(p)} G \circ T_p F)(v)(g)
\end{align*}
$$

### Properties of the tangent map

The tangent map of the identity map $\id_M : M \to M$ is the identity map on the tangent space:

$$
T_p \id_M = \id_{T_p M}
$$

This is because

$$
(T_p \id_M)(v)(g) = v(g \circ \id_M) = v(g) = \id_{T_p M} (v)(g)
$$

If $F \in C^\infty(M, N)$ is a diffeomorphism then $T_p F$ is a linear isomorphism between the vector spaces $T_p M$ and $T_{F(p)} $, and $(T_p F)^{-1} = T_{F(p)}(\inv F)$. We use the previous fact to prove this:

$$
\begin{align*}
\id_M &= \inv F \circ F \\
T_p \id_M &= T_p (\inv F \circ F) \\
\id_{T_p M} &= T_{F(p)} \inv F \circ T_p F
\end{align*}
$$

A similar derivation holds for $F \circ \inv F$ as well, so $T_{F(p)} \inv F$ is the inverse of $T_p F$. Since $T_p F$ is invertible, it is an isomorphism.

Suppose $q \in N$ and let $F : M \to N$ be the constant map so that for all $p \in M$, $F(p) = q$. Then $T_p F$ is the zero map for all $p \in M$. To prove this, we use the fact that tangent vectors vanish for constant functions:

$$
T_p F(v)(g) = v(\underbrace{g \circ F}_{\text{constant}}) = 0
$$

### Tangent map and Jacobian matrix

Suppose $U \subseteq \R^m$ and $V \subseteq \R^n$ are open, let $F \in C^\infty(U, V)$, and let $p \in U$. Then,

$$
T_p F \left( \frac{\partial}{\partial x^i}\bigg\vert_p \right) = \sum_j \frac{\partial y^j}{\partial x^i}\bigg\vert_p \frac{\partial}{\partial y^j}\bigg\vert_{F(p)}
$$

where $y = F(x)$ and $y^j = F^j(x)$.

We proved earlier that

$$
\frac{\partial}{\partial x^1}\bigg\vert_p, ..., \frac{\partial}{\partial x^m}\bigg\vert_p
$$

form a basis for $T_p U$ Thus, this theorem shows that in this basis, the matrix for $T_p F$ is the Jacobian matrix. Therefore $T_p F = D_p F$ for functions between Euclidean spaces.

**Proof.**

Suppose $g \in C^\infty(N)$. Then,

$$
\begin{align*}
T_p F \left( \frac{\partial}{\partial x^i}\bigg\vert_p \right)(g) &= \frac{\partial}{\partial x^i}\bigg\vert_p (g \circ F) \\
&= \frac{\partial}{\partial x^i}\bigg\vert_p (g \circ y) \\
&= \sum_j \frac{\partial y^j}{\partial x^i}\bigg\vert_p \frac{\partial g}{\partial y^j}\bigg\vert_{F(p)}
\end{align*}
$$

### Redefinitions in terms of the tangent map

Now that we see the analogy between the tangent map and the Jacobian matrix, we can make many redefinitions:

Suppose $F \in C^\infty(M, N)$, then

- the *rank* of $F$ at $p \in M$ is the rank of $T_p F$
- $F$ has *maximal rank* at $p$ if $\rank_p F = \min(\dim M, \dim N)$
- $F$ is a *submersion* if $T_p F$ is surjective for all $p \in M$
- $F$ is an *immersion* if $T_p F$ is injective for all $p \in M$
- $F$ is a *local diffeomorphism* if $T_p F$ is bijective for all $p \in M$
  - note that if $T_p F$ is bijective then it is an isomorphism
- $p \in M$ is a *critical point* of $F$ if $T_p F$ does not have maximal rank at $p$
- $p \in N$ is a *regular value* of $F$ if $T_p F$ is surjective for all $p \in \inv F \curlies q$ (or if $q \notin F(M)$)
- $q \in N$ is a *singular value* if it is not a regular value

## Tangent spaces and submanifolds

Let $S \subseteq M$ be a submanifold and let $p \in S$. Let $i : S \to M$ be the inclusion map, so for $x \in S$, $i(x) = x \in M$. Then we identify the tangent space $T_p S$ of $S$ with the image $(T_p i)(T_p S) \subseteq T_p M$.

### Regular points are in the kernel of the tangent map

Suppose $F \in C^\infty(M, N)$ where $\dim M = m$ and $\dim N = n$. Let $q \in N$ be a regular value of $F$, and let $S = \inv F\curlies{q}$ (so $S$ is a submanifold).

Then for every $p \in S$,

$$
T_p S = \ker(T_p F) \subseteq T_p M
$$

**Proof.**

$q$ is a regular value, so $T_p F$ is surjective for every $p \in \inv F \curlies q$. Thus, $\rank T_p F = n$, so $\ker(T_p F)$ has dimension $m - n$ (rank-nullity). By the regular value theorem, $\dim S = \dim \ker(T_p F)$. We also know that the tangent space of a manifold has the same dimension as the manifold, so $\dim T_p S = \dim S = \dim \ker(T_p F) = m - n$. 

If we show that $T_p S \subseteq \ker(T_p F)$, then we will be done, because a vector subspace of $\ker(T_p F)$ with the same dimension must be all of $T_p F$.

Using the chain rule, we know that
$$
T_p F \vert_{T_p S} = T_p F \circ T_p i = T_{i(p)} F \circ T_p i = T_p (F \circ i)
$$
$F \circ i$ is constant on $S$ since $S = \inv F \curlies q$. The tangent map of a constant function is 0 so $T_p (F \circ i) = 0$ on all of $T_p S$. However, the inclusion map has trivial null space, so this means that $T_p F$ is zero on $T_p S$, so $T_p S \subseteq \ker(T_p F)$.

#### Corollary

Suppose $V \subseteq \R^\ell$ is open and $F \in C^\infty(V, \R^k)$. Let $q \in \R^k$ be a regular value of $F$ and let $M = \inv F \curlies q \subseteq \R^\ell$, so $M$ is a submanifold. If $p \in M$, then
$$
T_p M = \ker(D_p F) \subseteq T_p \R^\ell = \R^\ell
$$

#### Example: Tangent space to $S^n$

Let $p \in S^n \subseteq \R^{n+1}$. We know that if we consider the squared norm,

$$
N(x^1, ..., x^{n+1}) = (x^1)^2 + ... + (x^{n+1})^2
$$

then $S = \inv N \curlies 1$. Then the Jacobian of $N$ at $p$ is

$$
\begin{align*}
D_p F(x) &= \lim_{t \to 0} F(p + tx) \\
&= 2p \cdot x
\end{align*}
$$

so the tangent space to $S^n$ at $p$ is

$$
T_p S^n = \ker(D_p F) = \curlies{x \in \R^{n+1} : p \cdot x = 0}
$$

i.e. the set of all vectors orthogonal to $p$.

### Critical points of a function on a submanifold

Suppose $S$ is a submanifold of $M$ with inclusion map $i : S \to M$, and $h \in C^\infty(M)$ is a smooth function. Let $f = h \vert_S = h \circ i$.

Define the set of critical points:

$$
\Crit(f) = \curlies{p \in S : \rank_p f < 1}
$$

The rank of $f$ is less than one if and only if $T_p F$ is the zero map. Also, by the chain rule, $T_p f = T_p h \circ T_p i$. Then we see that

$$
\Crit(f) = \curlies{p \in S : \text{image}(T_p i) = T_p S \subseteq \ker(T_p h)}
$$

For example, let $S \subseteq \R^3$ be a submanifold and let $h(x, y, z) = z$. We know that $T_p h \cong D_p h = \begin{pmatrix} 0 & 0 & 1 \end{pmatrix}$, so

$$
\ker(T_p h) \cong \curlies{(v_1, v_2, v_3) : v_3 = 0} = \text{the } xy \text{-plane}
$$

So the critical points of $f$ are

$$
\Crit(f) = \curlies{p \in S : T_p S \subseteq \text{the } xy \text{-plane}}
$$

## Matrix Lie groups

A **matrix Lie group** is a submanifold $G \subseteq \Mat_\R(n)$ that is also a subgroup with respect to multiplication, i.e.

- $I \in G$
- if $A \in G$ then $\inv A \in G$ (so every matrix in a Lie group must be invertible)
- if $A, B \in G$ then $AB \in G$

Examples:

- $GL(n, \R)$, the set of all invertible $n \times n$ matrices over $\R$
  - this is the set of all matrices with nonzero determinant, so it is an open subset of $\Mat_\R(n)$, so it is a submanifold of $\Mat_\R(n)$ with the same dimension
- $GL(n, \C)$, the set of all invertible $n \times n$ matrices over $\C$
  - this is similarly a submanifold of $\Mat_\C(n)$
- $SL(n, \R) = \curlies{A \in \Mat_\R(n) : \det A = 1}$
  - we prove below that this is a submanifold
- $O(n) = \curlies{A \in \Mat_\R(n) : A^T A = I}$
  - we have proved earlier that this is a submanifold
- $U(n) = \curlies{A \in GL(n, \C) : A^\dagger A = I}$ (where $A^\dagger = \overline A\phantom{}^T$)
- $SU(n) = \curlies{A \in U(n) : \det(A) = 1}$

### Matrix Lie algebras

If $G$ is a matrix Lie group, then the Lie algebra of $G$ is $T_I G \subseteq \Mat_\R(n)$, denoted as $\mathfrak g$. (Similarly, `\mathfrak` is used for other symbols denoting Lie algebras.)

Examples:

- $\mathfrak gl(n, \R)$ is the Lie algebra of $GL(n, \R)$
  - it is a real vector space of dimension $\dim GL(n, \R) = n \times n$, so it is isomorphic to $\Mat_\R(n)$
- $\mathfrak o(n)$ is the Lie algebra of $O(n)$
  - recall that if $F(A) = A^T A$, then $D_A F(X) = X^T A + A^T X$
  - thus $D_I F(X) = X^T + X$
  - so $\mathfrak o(n) = \ker(D_I F) = \curlies{X : X^T + X = 0}$

### $SL(n, \R)$ is a matrix Lie group

To show that $SL(n, \R)$ is a submanifold, we will show that $1$ is a regular value of the determinant function.

$$
\begin{align*}
D_A \det(X) &= \frac{d}{dt}\bigg\vert_{t=0} \det(A + tX)
\end{align*}
$$

The determinant is the product of the roots of the characteristic polynomial, which we can find by solving $\det(A + tX - \lambda I) = 0$.

Let's consider $A = I$. Then we want to solve

$$
\begin{align*}
\det(I + tX - \lambda I) &= 0 \\
t^n\det\left(X - \frac{\lambda - 1}{t} I\right) &= 0
\end{align*}
$$

i.e., $\lambda$ is an eigenvalue of $I + tX$ if and only if $\ds \frac{\lambda - 1}{t}$ is an eigenvalue of $X$. So the eigenvalues of $I + tX$ are

$$
1 + t\mu_1, ..., 1 + t\mu_k
$$

where $\mu_1, ..., \mu_k$ are the eigenvalues of $X$. So considering the determinant,

$$
\begin{align*}
\det(I + tX) &= \prod_{i=1}^k (1 + t\mu_i) \\
\frac{d}{dt}\bigg\vert_{t=0} \det(I + tX) &= \sum_{i=1}^k \mu_i \\
(D_I \det)(X)&= \text{tr} X
\end{align*}
$$

Now considering the derivative at any arbitrary matrix $A \in SL(n, \R)$,

$$
\begin{align*}
(D_A \det)(X) &= \frac{d}{dt}\bigg\vert_{t=0} \det(A + tX) \\
&= \frac{d}{dt}\bigg\vert_{t=0} \det(A(I + t\inv A X)) \\
&= \det(A) \cdot \frac{d}{dt}\bigg\vert_{t=0} \det(I + t\inv A X) \\
&= \det(A) \cdot (D_I \det)(\inv A X) \\
&= \det(A) \text{tr}(\inv A X)
\end{align*}
$$

Suppose $\det(A) = 1$, then

$$
(D_A \det)(X) = \text{tr}(X)
$$

which is surjective onto $\R$, so $\det$ has maximal rank on $SL(n, \R) = \inv \det \curlies 1$. Thus, $1$ is a regular value, so $SL(n, \R)$ is a submanifold.

Calculating its Lie algebra,

$$
\begin{align*}
\mathfrak{sl}(n, \R) &= T_I SL(n, \R) \\
&= \ker(D_I \det) \\
&= \curlies{X : \text{tr}(X) = 0}
\end{align*}
$$

### Properties of matrix Lie algbras

Let $G$ be a matrix Lie group and let $\mathfrak g = T_I G$ be its Lie algebra. Then

1. if $A \in G$, $T_A G = \curlies{AX : X \in \mathfrak g} = \curlies{XA : X \in \mathfrak g}$
2. if $A \in G$ and $X \in \mathfrak g$, then $AX\inv A \in \mathfrak g$
3. if $X, Y \in \mathfrak g$ then so is their commutator, $[X, Y] = XY - YX \in \mathfrak g$

**Proof.**

*Part 1*

Let $Y \in T_A G$, then there is some path $\gamma : (-\delta, \delta) \to G$ with $\gamma(0) = A$ that represents $Y$. Then, since $G$ is a Euclidean space, we can identify $Y$ with

$$
Y \cong \frac{d}{dt}\bigg\vert_{t=0} \gamma(t)
$$

Define the path $\lambda(t) = \inv A \gamma(t)$, then $\lambda$ is also a path in $G$ and $\lambda(0) = I$. Then we can identify define the tangent vector $X \in \mathfrak g$ represented by $\lambda$, and we can identify $X$ with

$$
X
\cong \frac{d}{dt}\bigg\vert_{t=0} \lambda(t)
= \frac{d}{dt}\bigg\vert_{t=0} \inv A \gamma(t)
= \inv A \frac{d}{dt}\bigg\vert_{t=0}
\cong \inv A Y
$$

so $Y = AX$.

The other identity can be proven similarly if we instead set $\lambda(t) = \gamma(t) \inv A$.

*Part 2*

Suppose $A \in G$ and $X \in \mathfrak g$. Then $AX \in T_A G = \curlies{YA : Y \in \mathfrak g}$, so $AX = YA$ for some $Y \in \mathfrak g$. Then $AX\inv A = Y \in \mathfrak g$.

*Part 3*

Suppose $X, Y \in \mathfrak g$. Then there is some curve $\gamma : (-\delta, \delta) \to G$ with $\gamma(0) = I$ that represents $Y$, so we can identify

$$
Y \cong \frac{d}{dt}\bigg\vert_{t=0} \gamma(t)
$$

We can define a new curve

$$
\begin{align*}
\lambda : (-\delta, \delta) &\to \mathfrak g \\
t &\mapsto \gamma(t) X \inv{\gamma(t)}
\end{align*}
$$

Since $\gamma(t) \in G$, by part 2 we know that $\lambda(t) = \gamma(t) X \inv{\gamma(t)} \in \mathfrak g$.

We can find the derivative of $\inv{\gamma(t)}$:

$$
\begin{align*}
(\gamma \inv{\gamma}) &= I \\
D_t (\gamma \inv{\gamma}) &= D_t I \\
(D_t \gamma) \inv{\gamma} + \gamma (D_t \inv{\gamma}) &= 0 \\
\gamma (D_t \inv{\gamma}) &= -(D_t \gamma) \inv{\gamma} \\
D_t \inv{\gamma} &= -\inv{\gamma} (D_t \gamma) \inv{\gamma} \\
\end{align*}
$$

Using this, we can find the derivative of $\lambda$:

$$
\begin{align*}
D_t \lambda &= D_t (\gamma X \inv{\gamma}) \\
&= (D_t \gamma) \cdot X \inv{\gamma} + \gamma \cdot (D_t X) \inv{\gamma} + \gamma X \cdot (D_t \inv{\gamma}) \\
&= (D_t \gamma) \cdot X \inv{\gamma} - \gamma X \cdot -\inv{\gamma} (D_t \gamma) \inv{\gamma} \\
D_0 \lambda &= (D_t \gamma)(0) \cdot X \inv{\gamma(0)} - \gamma(0) X \cdot \inv{\gamma(0)} (D_t \gamma)(0) \inv{\gamma(0)} \\
&= Y X \inv I - I X \inv I Y \inv I \\
&= YX - XY
\end{align*}
$$

[...]