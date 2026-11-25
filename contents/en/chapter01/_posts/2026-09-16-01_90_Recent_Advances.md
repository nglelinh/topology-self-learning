---
layout: post
title: "Lecture 01.90: Recent Advances (2022–2026) — Topology of Data and Clustering"
lang: en
lang-ref: lecture-01-90
chapter: 1
lecture: 90
order: 90
lesson_type: optional
categories: [chapter01]
tags: [optional, recent-advances, clustering, topology-of-data, tda]
description: "Optional notes: point-set topology meets clustering and TDA (2022–2026). Not a theory translation."
---

Every data scientist has had the same unsettling experience: you run a clustering algorithm on a biological dataset, tweak one neighborhood parameter by 10%, and suddenly two tidy cell populations shatter into five fragments—or fuse into one blob. Beneath that practical headache hides the very first definition of general topology: **what counts as an open neighborhood, and when does a map preserve nearness without tearing space apart?**

**Optional notes.** Open sets, bases, closure, and continuity in Chapter 01 stay as they are. These notes show how they reappear when $X$ is a point cloud in 2022–2026 research. The theory track is in Vietnamese; this English page holds recent-advance notes only.

---

## Key ideas: How Open Sets, Continuity, and Superlevel Sets Power Modern Clustering

To a university graduate, the axioms of a topological space can feel oddly detached from data algorithms. In 2022–2026 machine learning, three Chapter 01 concepts sit right inside the engine:

1. **Coarser vs. Finer Topologies as Scale Knobs:** Choosing a smaller neighborhood radius $$\varepsilon$$ (or fewer $$k$$-nearest neighbors) creates a *finer* topology with many small open pieces; enlarging $$\varepsilon$$ passes to a *coarser* topology that glues pieces together. Comparing topologies across all scales at once is the core of **persistent clustering**.
2. **Density Superlevel Sets & Mode Prominence (ToMATo):** Given an estimated data density $$\rho: X \to \mathbb{R}$$, the superlevel sets $$U_\lambda = \{x : \rho(x) > \lambda\}$$ form an expanding family of open sets as threshold $$\lambda$$ drops from $$\infty$$ to $$0$$. Each density peak births a cluster, and each saddle point merges two clusters—measuring each cluster's true **prominence** rather than relying on one brittle cutoff.
3. **Continuity vs. Homeomorphism in Dimension Reduction:** A continuous map $$f: X \to Y$$ guarantees that preimages of open sets are open—meaning nearby points stay nearby, though distinct clusters can still collide. Only a **homeomorphism** preserves topology both ways. Popular projections like UMAP approximate local neighborhoods, so dropping a single bridge edge in the neighbor graph can tear one cluster into two!

---

## 📖 Overview

A topology on $X$ is a way to say which points sit next to which, without a metric. Clustering is the same question written as an algorithm: which pieces of the data are natural “open chunks”? From 2022 to 2026, topological clustering left the appendix of TDA books and became multiscale, multiparameter, and stable.

![Clustering](https://upload.wikimedia.org/wikipedia/commons/c/c8/Cluster-2.svg)
*Two planar clusters: a discrete picture of disconnectedness. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cluster-2.svg)*

---

## 🎯 Intuition

Recall an open set: if $x\in U$, a whole “region around $x$” stays in $U$. In data that region is usually $k$ neighbours or an $\varepsilon$-ball. Small $\varepsilon$ makes every point a cluster; large $\varepsilon$ glues everything. **Persistent clustering** watches clusters through $\varepsilon$ — the same spirit as comparing coarser/finer topologies in Lecture 01.01.

### Worked Example (Step by Step): Tracking Superlevel-Set Clusters and Prominence on a 5-Point Density Profile

Suppose we sample a 1D dataset along a path of 5 adjacent points $$x_1 - x_2 - x_3 - x_4 - x_5$$ whose estimated density values are:

$$
\rho(x_1) = 5,\quad \rho(x_2) = 2,\quad \rho(x_3) = 1,\quad \rho(x_4) = 4,\quad \rho(x_5) = 2.
$$

There are two clear density peaks—at $$x_1$$ (height 5) and $$x_4$$ (height 4)—separated by a valley at $$x_3$$ (height 1). Sweep the threshold $$\lambda$$ downward and record the connected components of the open superlevel set $$U_\lambda = \{x : \rho(x) > \lambda\}$$:

| Threshold $$\lambda$$ | Superlevel set $$U_\lambda = \{x : \rho(x) > \lambda\}$$ | Connected components | Topological event |
|---|---|---|---|
| $$\lambda = 4.5$$ | $$\{x_1\}$$ | 1 | Cluster A **born** at height $$5$$ |
| $$\lambda = 3.5$$ | $$\{x_1\} \sqcup \{x_4\}$$ | 2 | Cluster B **born** at height $$4$$ |
| $$\lambda = 1.5$$ | $$\{x_1, x_2\} \sqcup \{x_4, x_5\}$$ | 2 | Both clusters grow; valley $$x_3$$ still separates them |
| $$\lambda = 0.5$$ | $$\{x_1, x_2, x_3, x_4, x_5\}$$ | 1 | Valley $$x_3$$ enters → B **merges** into A at height $$1$$ |

By the **Elder Rule** (the higher peak survives, the younger peak dies at the saddle), Cluster B has persistence prominence $$4 - 1 = \mathbf{3}$$, while Cluster A persists forever ($$[5, -\infty)$$). Now imagine a noisy bump of height $$1.2$$ sitting next to the valley: its prominence is only $$1.2 - 1 = \mathbf{0.2}$$. Choosing a prominence cutoff $$\tau = 1$$ cleanly keeps the 2 real clusters and discards the noise bump—something no single fixed density threshold $$\lambda$$ could achieve if one true cluster were slightly shorter than another!

### Explanation: Why Topological Clustering Beats Single-Threshold Clustering

1. **Replace one fragile threshold with a full filtration:** single-threshold density clustering (like classic DBSCAN with one fixed density) fails when Cluster A has peak density 5 and Cluster B has peak density 2 while a valley sits at 1; sweeping $$\lambda$$ sees *every* peak at its own native scale.
2. **Measure cluster significance by lifetime (prominence):** a cluster's persistence $$\text{birth} - \text{death}$$ is literally the depth of the valley separating it from a taller neighbor—a coordinate-free topological invariant of the density function.
3. **Move to multiparameter filtrations when density and scale interact:** real datasets vary in both local density $$\rho$$ and geometric radius $$\varepsilon$$; 2025–2026 methods like ToMAToMP track components across *both* parameters simultaneously to resist outliers.
4. **Audit dimension-reduction plots with continuity:** before trusting two separated blobs on a UMAP scatter plot, remember that UMAP is not guaranteed to be a homeomorphism—check whether the separation already lives in the high-dimensional $$H_0$$ persistence diagram!

**Quick check.** In our 5-point example, what happens to the persistence prominence of Cluster B if the valley $$x_3$$ rises from $$1$$ to $$3.8$$? Its prominence shrinks from $$4 - 1 = 3$$ down to $$4 - 3.8 = \mathbf{0.2}$$, immediately signaling that the two peaks have nearly merged into a single broad cluster.

---

## 📐 Four concrete advances

### 1. Persistent multiscale density-based clustering

Bot, McInnes, and Aerts (2025) introduce *Persistent Multiscale Density-based Clustering*: instead of one density threshold they track connected components of density superlevel sets as a filtration. Chapter 01 becomes an algorithm: the open sets $\{x:\rho(x)>\lambda\}$ move with $\lambda$, and the topology changes under control.

- Daniël Bot, Leland McInnes, Jan Aerts, *Persistent Multiscale Density-based Clustering*, arXiv:2512.16558 (2025).

### 2. ToMATo again: multiparameter topological clustering

The ToMATo line (Topological Mode Analysis Tool) pairs density modes with $0$-dimensional persistence. Martineau, Pouzat, and Geffray (2025) take ToMATo to high-dimensional spike sorting. Andrianirina and Carrière (2026) extend it to ToMAToMP — stable multiparameter clustering. A “mode” is a peak of a density; a “valley” is where clusters meet — a very point-set picture of closure and boundary.

- Louise Martineau, Christophe Pouzat, Ségolen Geffray, *ToMATo: an efficient and robust clustering algorithm for high dimensional datasets*, arXiv:2509.17499 (2025).
- Ludo Andrianirina, Mathieu Carrière, *ToMAToMP: Robust and Multi-Parameter Topological Clustering*, arXiv:2605.14824 (2026).

### 3. Continuity and homeomorphism in dimension reduction

UMAP claims to preserve local topology. Dalmia and Sia (2021; still shaping 2022–2026 practice) show that **connectivity** of the neighbour graph decides cluster quality after UMAP: lose an edge and you lose a component. That is Lecture 01.03 in experimental form: a merely “almost continuous” map can break a homeomorphism type and merge or split clusters.

- Ayush Dalmia, Suzanna Sia, *Clustering with UMAP: Why and How Connectivity Matters*, arXiv:2108.05525 (2021).

### 4. Neural networks as topological spaces of data

Ballester, Casacuberta, and Escalera (2023/24) survey TDA on neural networks: weights, activations, and datasets are treated as spaces. The forward pass is a map in the sense of Chapter 01, except $X$ has millions of points.

- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *Topological Data Analysis for Neural Network Analysis: A Comprehensive Survey*, arXiv:2312.05840 (2023).

**Formal reminder:** if $f:X\to Y$ is continuous and $U\subset Y$ is open, then $f^{-1}(U)$ is open. In an encoder, “open” is usually an ambient ball in latent space. When the encoder fails this, clusters tear.

---

## 🧠 Papers and references

- Munkres, *Topology*, Ch. 2.
- Adams & Franzosa, *Introduction to Topology: Pure and Applied*, Ch. 1.
- The arXiv items above.

## 🔗 Applications

Single-cell grouping uses UMAP plus density clustering. These notes let you read the 2025–2026 papers without leaving Chapter 01.

## Video tham khảo

- **xem trước** [UMAP Dimension Reduction, Main Ideas!!!](https://www.youtube.com/watch?v=eN0wFzBA4Sc) — StatQuest with Josh Starmer, English. UMAP as a dimension reduction. This note then explains why that is not yet a homeomorphism.
- [Henry Adams (5/3/22): Topology in Machine Learning](https://www.youtube.com/watch?v=kwYiQNa_pTc) — Applied Algebraic Topology Network, English. Topology used as a feature of data and of clustering, close to the TDA items here.
- [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, English. Components and holes across scales, which is what a clustering algorithm is trying to see.

## 🧩 Exercises

1. Draw two topologies on the same 5 points: one with 2 clusters, one with 1. Which is finer?
2. Why does increasing $k$ in $k$-NN look like passing to a coarser topology?
3. Take a density on $\mathbb{R}^2$ with two peaks. Sketch the filtration $\{\rho>\lambda\}$ as $\lambda$ drops.
