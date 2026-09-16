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

**Optional notes.** Higher homotopy, fiber bundles, Morse theory, manifolds, and knots stay as in Chapter 08. We watch them become *learning architectures* and *reduction algorithms*.

The theory track is in Vietnamese. This English page holds recent-advance notes only.

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

## 🧩 Exercises

1. Name a 3-point relation a GNN cannot see but a simplicial network can.
2. Relate Morse index to the birth/death of a bar in a barcode.
3. Read the Papamarkou et al. (2024) abstract and list two TDL gaps they name.
