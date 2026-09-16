---
layout: post
title: "Lecture 03.90: Recent Advances (2022–2026) — Separation, Embeddings, and Stable Shape"
lang: en
lang-ref: lecture-03-90
chapter: 3
lecture: 90
order: 90
lesson_type: optional
categories: [chapter03]
tags: [optional, recent-advances, hausdorff, embedding, stability]
description: "Optional notes: separation axioms and metrization meet TDA stability and the UMAP critique. Not a theory translation."
---

**Optional notes.** The axioms $T_0$–$T_4$, Urysohn’s lemma, and metrization stay as in Chapter 03. We only ask: in what sense do data and TDA invariants “separate points”?

The theory track is in Vietnamese. This English page holds recent-advance notes only.

---

## 📖 Overview

Hausdorff means distinct points have disjoint neighbourhoods — limits, when they exist, are unique. Machine learning often *assumes* this when it draws a UMAP: distinct points should sit in two places. Work from 2022–2026 shows the assumption is both necessary (barcode stability) and fragile (UMAP is not a topological embedding).

![Hausdorff distance](https://upload.wikimedia.org/wikipedia/commons/2/21/Hausdorff_distance_sample.svg)
*Hausdorff distance between two sets: the $T_2$ idea, metrized. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_distance_sample.svg)*

---

## 🎯 Intuition

Urysohn’s lemma says that in a sufficiently nice (normal) space, disjoint closed sets are separated by a continuous $[0,1]$-valued function. Mapper and UMAP try to *draw* that function for data. When the space is not Hausdorff — e.g. Kayacan’s finite Alexandroff spaces (Lecture 00.90) — point-separation fails and embedding algorithms start inventing distances.

---

## 📐 Four concrete advances

### 1. Diagram space is Hausdorff — that is why stability means anything

The bottleneck metric $d_B$ on persistence diagrams satisfies
$$
d_B(\mathrm{Dgm}(X),\mathrm{Dgm}(Y))\le d_{GH}(X,Y)
$$
under compact hypotheses. $(\mathrm{Dgm},d_B)$ is metric, hence $T_2$: distinct barcodes are ball-separated. Fu et al. (2025) extend Gromov–Hausdorff stability to labeled sets — an *applied* metrization theorem: we may treat barcodes as points of a Hausdorff space.

- Yaoying Fu et al., *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 2. The UMAP critique: not every “embedding” is an embedding

Yang (2026) shows that everyday UMAP is **spectral clustering on a fuzzy nearest-neighbour graph** — not a topological embedding of a hidden manifold. Li and Zhang (2026) add geometric/topological priors (JORC-UMAP) exactly where UMAP breaks local $T_2$. The Chapter 03 lesson: “drawable in $\mathbb{R}^2$” $\neq$ “an embedding exists”.

- Yang Yang, *UMAP Is Spectral Clustering on the Fuzzy Nearest-Neighbor Graph*, arXiv:2602.11662 (2026).
- Xiaobin Li, Run Zhang, *Understanding and Improving UMAP with Geometric and Topological Priors: The JORC-UMAP Algorithm*, arXiv:2601.16552 (2026).

### 3. Finite $T_0$ as a computational model

Kayacan (2025) works on finite $T_0$ non-Hausdorff spaces. This does not contradict Chapter 03: it explains why a discrete TDA pipeline *must* pass through a non-$T_2$ space before a Hausdorff barcode is emitted.

- Selçuk Kayacan, *Persistent Homology via Finite Topological Spaces*, arXiv:2512.23348 (2025).

### 4. Stable vectorization: Lipschitz instead of mere continuity

A continuous function on diagram space is not enough for learning; one wants Lipschitz so that small noise cannot explode features. Loiseaux et al. (2023) and Bravetti et al. (2024) build (including multiparameter) vectorizations with stability proofs — a quantitative cousin of Urysohn’s “continuous functions separate sets”.

- David Loiseaux et al., *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Alessandro Bravetti, Martín Mijangos, Pablo Padilla, *New divergence measures between persistence diagrams and stability of vectorizations*, arXiv:2410.03910 (2024).

---

## 🧠 Papers and references

- Munkres, *Topology*, Ch. 4–5.
- Willard, *General Topology*, Ch. 13–23.
- The arXiv items above.

## 🔗 Applications

When a UMAP dashboard “separates” two patient groups, Chapter 03 forces the question: is that genuine $T_2$ of the data, or a spectral-clustering artifact?

## 🧩 Exercises

1. Exhibit a 3-point $T_0$ space that is not $T_1$. Could it appear as an intermediate filtration stage?
2. Why does the bottleneck metric make diagram space Hausdorff, while raw union-find does not?
3. Read Yang (2026)’s abstract and write one sentence: what does UMAP preserve, and what does it not?
