# Topology

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\angles}[1]{\left\langle #1 \right\rangle}
\newcommand{\inv}[1]{#1^{-1}}

\newcommand{\A}{\mathcal A}
\newcommand{\RP}[1]{\R P^{#1}}

\newcommand{\x}{\mathbf x}
\newcommand{\y}{\mathbf y}
$$

## Open sets

Let $M$ be an $m$-dimensional manifold (with maximal atlas $\A$). Then a subset $U \subseteq M$ is **open** if and only if $\phi_\alpha(U \cap U_\alpha)$ is open for every $(U_\alpha, \phi_\alpha) \in \A$.

### Open sets and sub-atlases

Let $\mathcal B \subseteq \A$ be a sub-atlas whose chart domains cover $M$. Then $U \subseteq M$ is open if and only if $\phi_\beta(U \cap U_\beta)$ is open for every $(U_\beta, \phi_\beta) \in \mathcal B$.

($\Rightarrow$) Suppose $\phi_\beta(U \cap U_\beta)$ is open for every $(U_\beta, \phi_\beta) \in \mathcal B$. Let $U \subseteq M$, and suppose $(U_\alpha, \phi_\alpha) \in \A$, and $(U_\beta, \phi_\beta) \in \mathcal B$. Then since the chart domains of $\mathcal B$ cover $M$,
$$
\begin{align*}
\phi_\alpha(U \cap U_\alpha) &= \phi_\alpha \left( \bigcup_{\beta} U \cap U_\alpha \cap U_\beta \right) \\
&= \bigcup_{\beta} \phi_\alpha(U \cap U_\alpha \cap U_\beta) \\
&= \bigcup_{\beta} \phi_\alpha((U \cap U_\beta) \cap (U_\alpha \cap U_\beta)) \\
&= \bigcup_{\beta} \underbrace{\phi_\alpha \circ \inv \phi_\beta}_{\text{diffeomorphism}}(\underbrace{\phi_\beta(U \cap U_\beta)}_{\text{assumed open}} \cap \underbrace{\phi_\beta(U_\alpha \cap U_\beta)}_{\text{compatible charts}}) \\
\end{align*}
$$
By assumption, $\phi_\beta(U \cap U_\beta)$ is open. Since $\mathcal B$ is a sub-atlas of $\mathcal A$, $(U_\beta, \phi_\beta)$ is compatible with $(U_\alpha, \phi_\alpha)$, so $\phi_\beta(U_\alpha \cap U_\beta)$ is open. Thus $\phi_\beta(U \cap U_\beta) \cap \phi_\beta(U_\alpha \cap U_\beta)$ is open. Also since the two coordinate charts are compatible, we know that $\phi_\alpha \circ \inv\phi_\beta$ is a diffeomorphism, which means that it maps open sets to open sets. As a result, the entire set $\phi_\alpha \circ \inv\phi_\beta(...)$ is open, so the union is open. This holds for all coordinate charts in $\A$, so $U$ must be open.

($\Leftarrow$) Suppose $U \subseteq M$ is open. Since $\mathcal B \subseteq \A$, the image of any coordinate chart of $\mathcal B$ is open.

### Open subsets of manifolds are manifolds

This follows from the previous theorem. If $U \subseteq M$ is a manifold, then we can define the atlas
$$
\A_U = \curlies{(V_\alpha, \psi_\alpha) : V_\alpha = U_\alpha \cap U, \psi_\alpha = \phi_\alpha \large\vert_{U \cap U_\alpha}}
$$
This is an atlas since by the previous theorem, $\psi_\alpha(V_\alpha)$ is always open, and furthermore every $\psi_\alpha$ is still compatible.

## Topology

Let $M$ be a manifold, then our definition of open sets is a topology, i.e.

- $\emptyset$ and $M$ are open
- a finite intersection of open sets is open
- an arbitrary union of open sets is open

$M$ is also a Hausdorff space, so for any two distinct points in $M$ have disjoint open neighbourhoods.

### More topological notions

- an **open neighbourhood** of a point is an open set containing the point
- a set $A \subseteq M$ is **closed** if and only if $M \setminus A$ is open
- a set $A \subseteq M$ is **disconnected** if there exist disjoint nonempty open sets $U, V$ so that $A = U \sqcup V$, and $A$ is **connected** if it is not disconnected

### Compactness

A set $A \subseteq M$ is **compact** if for every collection of open sets $\curlies{U_\alpha}$ that covers $A$, i.e. $\ds A \subseteq \bigcup_{\alpha} U_\alpha$, there is a finite subcollection $\curlies{U_{\alpha_1}, U_{\alpha_2}, ... U_{\alpha_n}}$ that also covers $A$.

The Heine-Borel theorem says that a set $B \subseteq \R^n$ is compact if and only if it is closed and bounded.

#### Subsets of coordinate charts are compact if their images are compact

Suppose $A \subseteq M$ is contained within a single coordinate chart $(U, \phi)$. Then $A$ is compact if and only if $\phi(A)$ is compact in $\R^n$.

($\Leftarrow$) Suppose $\phi(A)$ is compact, and let $\curlies{U_\alpha}$ be an open cover of $A$. Then by definition, $\phi(U_\alpha \cap U)$ is open in $\R^n$. Thus, $\curlies{\phi(U_\alpha \cap U)}$ is an open cover of $\phi(A)$, so there is a finite subcover $\curlies{\phi(U_{\alpha_1} \cap U), ..., \phi(U_{\alpha_n} \cap U)}$. Thus, $A$ is covered by $\curlies{U_{\alpha_1} \cap U, ..., U_{\alpha_n} \cap U}$, so $A$ is covered by $\curlies{U_{\alpha_1}, ..., U_{\alpha_n}}$. Thus, we have found a finite subcover, so $A$ is compact.

($\Rightarrow$) We can make a similar argument for the other direction.

#### A finite union of compact sets is compact

Suppose $A_1, ..., A_n$ are compact, and let $\curlies{U_\alpha}$ be an open cover of $A_1 \cup ... \cup A_n$. Then for each $A_i$, $\curlies{U_\alpha}$ is an open cover of $A_i$, so we can find a finite subcover. Then we can take the union of these finite subcovers to obtain a finite subcollection that covers each of $A_1, ..., A_n$, so it covers $A_1 \cup ... \cup A_n$.

#### Example: The unit sphere is compact

Consider the unit sphere $S^n \subseteq \R^{n+1}$

#### Example: The projective plane is compact

Consider $\RP 2 = \curlies{(x^0 : x^1 : x^2) : (x^0, x^1, x^2) \neq (0, 0, 0)}$.

Recall that the standard atlas is $U_i = \curlies{(x^0 : x^1 : x^2) : x^i \neq 0}$ for $i = 0, 1, 2$ along with the functions
$$
\begin{align*}
\phi_0(x^0 : x^1 : x^2) &= \left(\frac{x^1}{x^0}, \frac{x^2}{x^0}\right) \\
\phi_1(x^0 : x^1 : x^2) &= \left(\frac{x^0}{x^1}, \frac{x^2}{x^1}\right) \\
\phi_2(x^0 : x^1 : x^2) &= \left(\frac{x^0}{x^2}, \frac{x^1}{x^2}\right) \\
\end{align*}
$$