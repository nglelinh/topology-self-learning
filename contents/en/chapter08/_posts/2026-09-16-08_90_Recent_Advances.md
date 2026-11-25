---
layout: post
title: "Lecture 08.90: Recent Advances (2022–2026) — Topological Deep Learning and Computational Morse"
lang: en
lang-ref: lecture-08-90
chapter: 8
lecture: 90
order: 90
lesson_type: optional
categories: [chapter08]
tags: [optional, recent-advances, topological-deep-learning, morse, bundles]
description: "Optional notes: π_n, bundles, Morse, manifolds meet TDL and discrete Morse. Not a theory translation."
---

Graph Neural Networks (GNNs) conquered social networks and basic chemistry by passing messages along pairwise edges. Yet look closely at a benzene ring, a protein folding pocket, or three scientists co-authoring a single paper: a **three-way interaction** is fundamentally different from three separate pairwise conversations! Between 2022 and 2026, **Topological Deep Learning (TDL)** broke past the pairwise graph barrier by letting neural networks pass messages across triangles, polygons, and higher-dimensional cells—while **Discrete Morse Theory** quietly became the high-speed preprocessor powering topological computation at scale.

**Optional notes.** Higher homotopy, fiber bundles, Morse theory, manifolds, and knots stay as in Chapter 08. We watch them become *learning architectures* and *reduction algorithms*. The theory track is in Vietnamese; this English page holds recent-advance notes only.

---

## Key ideas: Higher-Order Complexes, Hodge Laplacians, and Discrete Morse Theory

Three advanced topological pillars from Chapter 08 now sit directly inside modern geometric AI and computational topology:

1. **Beyond Graphs — Simplicial & Cell Complexes:** A graph only stores 0-cells (vertices) and 1-cells (edges). A **simplicial complex** adds 2-cells (filled triangles), 3-cells (tetrahedra), and higher faces; a **cell complex** allows arbitrary rings (like 6-carbon benzene hexagons) as single 2-cells—giving molecular and relational AI native higher-order inductive bias.
2. **Hodge Laplacians & Higher-Order Message Passing (TDL):** On a graph, messages diffuse via the graph Laplacian $$L_0 = B_1 B_1^\top$$. On a simplicial complex, signals living on **edges** (such as traffic flows or chemical bond currents) diffuse via the **1-Hodge Laplacian** $$L_1 = B_1^\top B_1 + B_2 B_2^\top$$, combining lower adjacency (through shared vertices) and upper adjacency (through shared triangles)!
3. **Discrete Morse Theory (Robin Forman):** Just as smooth Morse theory reconstructs a manifold from its critical points (minima, saddles, maxima), discrete Morse theory pairs non-critical $$(k)$$-cells with $$(k+1)$$-cells to collapse away redundant simplices while preserving exact homotopy type—slashing huge complexes down to a tiny skeleton of **critical cells**.

---

## 📖 Overview

Topological deep learning (TDL) trains models on data supported by simplicial complexes, cell complexes, and hypergraphs — the domains Chapter 08 just named. Hajij et al. (2022/23) set the foundation; Papillon et al. (2023/24) classify message-passing architectures; Papamarkou et al. (ICML 2024 position) call TDL the frontier of relational learning. In parallel, discrete Morse theory became the reduction engine for persistence on huge data.

![Simplicial complex](https://upload.wikimedia.org/wikipedia/commons/5/50/Simplicial_complex_example.svg)
*TDL’s domain: not only graphs, but simplices of every dimension. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

![Klein bottle](https://upload.wikimedia.org/wikipedia/commons/4/46/KleinBottle-01.png)
*A manifold that does not embed in $\mathbb{R}^3$: Chapter 08 manifolds are larger than surfaces in Euclidean space. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:KleinBottle-01.png)*

---

## 🎯 Intuition

A GNN talks only along edges ($1$-simplices). A simplicial network talks along triangles: three nodes already “know” they span a $2$-face. That is Morse and CW from Lectures 08.02–08.03 written as a layer. Fiber bundles appear when features live on fibres that twist around the base — the gauge language of physics, now a trainable layer.

### Worked Example (Step by Step): How the Hodge Laplacian $$L_1$$ Sees a Filled Triangle and How Discrete Morse Collapses a Path

Test both pillars by hand on 3-vertex complexes:

**Part A — Why a GNN is blind to a 2-face, while the Hodge Laplacian $$L_1$$ sees it instantly.** Consider 3 vertices $$\{0,1,2\}$$ with 3 oriented edges $$e_{01}, e_{12}, e_{02}$$ and a circulating edge flow $$x = (1,\ 1,\ -1)^\top$$ (unit flow going around the cycle $$0 \to 1 \to 2 \to 0$$).
- The signed vertex-edge incidence matrix is $$B_1 = \begin{pmatrix} -1 & 0 & -1 \\ 1 & -1 & 0 \\ 0 & 1 & 1 \end{pmatrix}$$. Check $$B_1 x = (0, 0, 0)^\top$$ (zero net divergence at every vertex!), so the lower Laplacian gives $$L_1^{\text{down}} x = B_1^\top B_1 x = \mathbf{0}$$.
- **Hollow triangle (no 2-face):** $$B_2 = 0$$, so $$L_1 x = 0$$! A zero eigenvalue of $$L_1$$ (a *harmonic* flow) signals a genuine 1-dimensional hole!
- **Filled triangle (add 2-face $$t$$ with boundary $$B_2 = (1,\ 1,\ -1)^\top$$):** now the upper Laplacian acts as:

$$
L_1^{\text{up}} x = B_2 (B_2^\top x) = \begin{pmatrix} 1 \\ 1 \\ -1 \end{pmatrix} \cdot (1 + 1 + 1) = \mathbf{3\,x \neq 0}!
$$

A standard GNN sees only the vertex adjacency matrix—identical in both cases—whereas a simplicial neural network using $$L_1$$ immediately distinguishes the hollow cycle from the filled 2-face!

**Part B — Discrete Morse pairing on a 3-vertex path.** On the path $$v_0 - e_1 - v_1 - e_2 - v_2$$ (3 vertices, 2 edges), construct a discrete gradient vector field by pairing $$(v_1 \to e_1)$$ and $$(v_2 \to e_2)$$. Every cell except $$v_0$$ is paired and collapses away! Only **1 critical 0-cell** ($$v_0$$) survives—proving in two arrows that the path is contractible ($$\chi = 3 - 2 = 1$$) without solving any linear system.

### Explanation: From Higher-Order Complexes to TDL and Morse Reductions

1. **Match the domain to the physics:** when data carries genuine multi-body interactions (protein pockets, aromatic rings, co-authorship cliques), lifting a graph to a simplicial or cell complex lets a single message-passing step aggregate the entire group at once.
2. **Use Hodge decomposition to separate signal types:** $$L_1$$ splits any edge signal cleanly into gradient flows (from vertices), curl flows (around triangles), and harmonic flows (around true holes)—giving TDL layers crisp spectral structure.
3. **Collapse before you compute (Discrete Morse):** by pairing adjacent $$(k, k+1)$$-cells into acyclic arrows, Morse reductions delete millions of trivial cells from 3D grids while keeping every topological feature (critical cell) intact.
4. **Look before you lift:** as Papillon et al. (2026) caution, higher-order complexes cost more memory and compute; always diagnose whether higher-order structure actually carries signal before upgrading a GNN to a simplicial network.

**Quick check.** In Part B, if we close the path into a hollow triangle by adding edge $$e_3 = (v_0, v_2)$$ (keeping pairings $$v_1 \to e_1$$ and $$v_2 \to e_2$$), which cells remain unpaired (critical)? Exactly two: the 0-cell $$v_0$$ and the 1-cell $$e_3$$—giving $$\chi = 1 - 1 = \mathbf{0}$$, matching the circle $$S^1$$!

---

## 📐 Four concrete advances

### 1. TDL beyond graph data

Hajij, Zamzmi, Papamarkou, Miolane, Dey, Birdal, and many coauthors (2022/23) define TDL: learning on topological domains (simplicial, cell, combinatorial complexes). This is the manifesto linking Chapter 08 to geometric deep learning.

- Mustafa Hajij et al., *Topological Deep Learning: Going Beyond Graph Data*, arXiv:2206.00606 (2022).

### 2. Architecture survey and the ICML 2024 position

Papillon, Sanborn, Hajij, and Miolane (2023/24) classify topological neural networks by how messages travel on the skeleton. Papamarkou, Birdal, Bronstein, Carlsson, Curry, and 20+ coauthors (2024) argue that TDL complements — does not replace — graph representation learning, and they list gaps (representation, compute, benchmarks).

- Mathilde Papillon, Sophia Sanborn, Mustafa Hajij, Nina Miolane, *Architectures of Topological Deep Learning: A Survey of Message-Passing Topological Neural Networks*, arXiv:2304.10031 (2023).
- Theodore Papamarkou et al., *Position: Topological Deep Learning is the New Frontier for Relational Learning*, ICML 2024, arXiv:2402.08871.

### 3. Discrete Morse as the computer of Lecture 08.02

Bauer–Roll (2022) bridge persistent homology and discrete Morse via “wrapping cycles”. Guillou–Vidal–Tierny (2022) and Le Guillou–Fortin–Tierny (2025) turn Morse sandwich into a distributed pipeline. Ahuja–Iyer (2026) put simple-homotopy invariants into persistence via discrete Morse. Morse is no longer only a cell-attachment theorem: it is a preprocessor.

- Ulrich Bauer, Fabian Roll, *Wrapping Cycles in Delaunay Complexes: Bridging Persistent Homology and Discrete Morse Theory*, arXiv:2212.02345 (2022).
- Eve Le Guillou, Pierre Fortin, Julien Tierny, *Distributed Discrete Morse Sandwich*, arXiv:2505.21266 (2025).

### 4. TDL for proteins / materials, and diagnostics

Wang, Jamasb, Hajij et al. (2025) bring TDL to protein representation (Topotein). Papillon et al. (2026) build “look before you lift” diagnostics for TDL. Yadav, Er, Goto, and Xia (2026) use periodic TDL for polymers. Chapter 08 manifolds and bundles become inductive bias.

- Zhiyu Wang, Arian Jamasb, Mustafa Hajij et al., *Topotein: Topological Deep Learning for Protein Representation Learning*, arXiv:2509.03885 (2025).
- Mathilde Papillon et al., *Look Before You Lift: Visual and Quantitative Diagnostics for Topological Deep Learning*, arXiv:2608.15388 (2026).

---

## 🧠 Papers and references

- Hatcher, *Algebraic Topology*, Ch. 4.
- Milnor, *Morse Theory*.
- The arXiv/ICML items above.

## 🔗 Applications

Predicting polymer properties when the repeating unit lives on a periodic complex: TDL uses the same symmetry that bundles and group actions (Chapters 05–08) already describe.

## Video tham khảo

- **xem trước** [Introduction to Topological Deep Learning](https://www.youtube.com/watch?v=N67GABKImZA) — Mathilde Papillon, English. Topological deep learning beyond graph data, the survey direction of this note.
- [Nicholas Scoville: Discrete Morse Theory as an Introduction to Topology](https://www.youtube.com/watch?v=p7bzaDrNHrQ) — Kaleidoscope Circles, English. Nicholas Scoville on discrete Morse theory, the computable form of the Morse theory in this note.

## 🧩 Exercises

1. Name a 3-point relation a GNN cannot see but a simplicial network can.
2. Relate Morse index to the birth/death of a bar in a barcode.
3. Read the Papamarkou et al. (2024) abstract and list two TDL gaps they name.
