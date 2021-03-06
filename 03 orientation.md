# Orientation

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

## Oriented manifolds

Two charts $(U, \phi)$ and $(V, \psi)$ on $M$ are **orientation-compatible** if they are compatible and the transition map $\psi \circ \inv \phi$ is *orientation-preserving* on $\R^m$, i.e.

$$
\det(D(\psi \circ \inv \phi)) > 0 \text{ on } \phi(U \cap V)
$$

An *oriented atlas* is an atlas where any two coordinate charts are orienation-compatible.

A manifold $M$ is **orientable** if it admits an oriented atlas.

### Maximal oriented atlases

Given an oriented atlas $\A$, we can find a **maximal oriented atlas** $\overline A$ which is the set of all coordinate charts that are orientation-compatible with $\A$.

