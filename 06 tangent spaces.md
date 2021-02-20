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