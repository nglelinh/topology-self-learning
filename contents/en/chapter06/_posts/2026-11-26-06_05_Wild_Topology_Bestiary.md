---
layout: post
title: "Lecture 06.05: Wild Topology — Spaces Beyond CW Complexes"
lang: en
lang-ref: lecture-06-05
chapter: 6
lecture: 5
order: 5
categories: [chapter06]
tags: [wild-topology, hawaiian-earring, warsaw-circle, peano-continuum, fundamental-group]
description: "Wild Topology: Hawaiian Earring, Warsaw Circle, Harmonic Archipelago, and where classical algebraic topology fails outside CW complexes"
---

**A "wild" world where standard CW-complex intuition breaks down**

---

## 📖 Overview

> **Opening Story:** In Chapters 05 and 06, we grew comfortable with "tame" spaces such as manifolds and CW complexes, where every point has a contractible neighborhood and $\pi_1$ is computed cleanly via Seifert–Van Kampen. What happens if we take infinitely many circles of radius $1/n$ tangent at a single point? The resulting space is **compact and path-connected**—yet its fundamental group suddenly becomes **uncountable**, it admits no universal cover, and standard CW induction collapses! Welcome to **Wild Topology**, cataloged in the [Wild Topology Bestiary](https://wildtopology.com/bestiary/).

![Hawaiian Earring and Warsaw Circle]({{ site.imgurl }}/chapter_img/chapter06/06_01_wild_topology.png)

## 🗺️ Knowledge Map: What Does Wild Topology Study?

1. **The Tame vs. Wild Boundary:** Even a compact, metrizable, path-connected space can exhibit **local pathologies** that disable universal covering spaces and naive Seifert–Van Kampen decompositions.
2. **Semilocal Simple Connectedness:** A space $X$ admits a universal cover only if every point $x \in X$ has a neighborhood $U$ such that $i_*: \pi_1(U, x) \to \pi_1(X, x)$ is trivial.
3. **Topological Fundamental Group:** When $\pi_1(X, x_0)$ is uncountable, endowing it with the quotient topology from the loop space $\Omega(X, x_0)$ preserves convergence data of shrinking loops.

## 🧮 Worked Example: Comparing $\bigvee_{n=1}^\infty S^1$ vs. the Hawaiian Earring $\mathbb{E}$

1. **Infinite Wedge $W = \bigvee_{n=1}^\infty S^1$ (CW weak topology):** Any continuous loop $\gamma: [0,1] \to W$ has compact image, so it meets only finitely many circles $C_1, \dots, C_N$. Thus $\pi_1(W, p) \cong \ast_{n=1}^\infty \mathbb{Z}$ (countable free group).
2. **Hawaiian Earring $\mathbb{E} = \bigcup_{n=1}^\infty C_n \subset \mathbb{R}^2$ (subspace topology):** Every ball $B(p, \varepsilon)$ contains all $C_n$ with $n > 2/\varepsilon$. A loop can traverse $C_n$ on $[1-2^{-(n-1)}, 1-2^{-n}]$ and converge continuously to $p$ at $t=1$. Mapping binary sequences $(a_n) \in \{0,1\}^{\mathbb{N}}$ to loops proves $\pi_1(\mathbb{E}, p)$ is **uncountable** (see [L. Maxim, Sec. 4.1](https://people.math.wisc.edu/~lmaxim/topbookf.pdf)).

## 🦁 Classics from the Wild Topology Bestiary

| Space | Geometric Construction | Surprising Property |
|---|---|---|
| **Hawaiian Earring** ($\mathbb{E}$) | Circles of radius $1/n$ tangent at $(0,0)$ | Compact, path-connected, uncountable $\pi_1$, no universal cover |
| **Warsaw Circle** | Closure of $\sin(1/x)$ closed by an external arc | Path-connected, $\pi_1 = 0$, yet **not contractible** |
| **Griffiths Twin Cone** | Two cones over $\mathbb{E}$ glued at their basepoint | Union of two contractible spaces with nontrivial $\pi_1$ |
| **Harmonic Archipelago** | Infinite "bumps" over each loop of $\mathbb{E}$ | Uncountable $\pi_1$ despite each individual circle being null-homotopic |

## 🧩 Exercises

1. Prove continuity at $t=1$ of the infinite-loop path $\gamma: [0,1] \to \mathbb{E}$ traversing $C_n$ on $[1-2^{-(n-1)}, 1-2^{-n}]$.
2. Show the retraction $r_k: \mathbb{E} \to C_k$ induces a surjection $\pi_1(\mathbb{E}) \to \prod_{n=1}^\infty \mathbb{Z}$.
3. Explain why the Warsaw Circle is not homotopy equivalent to a point.
4. Prove the identity map $\bigvee_{n=1}^\infty S^1 \to \mathbb{E}$ is continuous but not a homeomorphism.
