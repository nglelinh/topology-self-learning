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

Open almost any genomics or AI paper today and you will see a colorful 2D scatter plot produced by UMAP, accompanied by the triumphant caption *"the embedding cleanly separates the two patient groups."* Yet a point-set topologist pauses immediately: **can you actually embed that high-dimensional structure into $$\mathbb{R}^2$$ without tearing or gluing points together, or is the plot merely a spectral-clustering illusion?** Answering that question brings Chapter 03's classic separation axioms ($$T_0, T_2, T_4$$) and metrization theorems straight into the heart of 2022–2026 machine learning.

**Optional notes.** The axioms $T_0$–$T_4$, Urysohn’s lemma, and metrization stay as in Chapter 03. We ask in what sense data and TDA invariants truly “separate points.” The theory track is in Vietnamese; this English page holds recent-advance notes only.

---

## Key ideas: Separation Axioms, Topological Embeddings, and Stable Barcodes

Why do mathematicians bother distinguishing $$T_0$$, $$T_1$$, $$T_2$$ (Hausdorff), and $$T_4$$ (normal) spaces? Three pillars show how this hierarchy bites in modern TDA and representation learning:

1. **The Separation Hierarchy ($$T_0 \subset T_1 \subset T_2 \subset T_4$$):** In a **$$T_0$$** space, distinct points merely have *some* open set containing one without the other (true of finite Alexandroff spaces used inside TDA pipelines). In a **Hausdorff ($$T_2$$)** space, distinct points enjoy *disjoint* open neighborhoods—guaranteeing unique limits and making distance-based reasoning coherent. Every metric space is automatically $$T_2$$ (even $$T_4$$).
2. **Topological Embeddings vs. Visual Projections:** A map $$f: X \to \mathbb{R}^2$$ is a true **topological embedding** only if it is a homeomorphism onto its image $$f(X)$$. Projecting a 2-sphere $$S^2$$ or a high-dimensional manifold into $$\mathbb{R}^2$$ *cannot* be an embedding without cutting or collapsing points—so 2D UMAP plots routinely distort global distances and invent false separations.
3. **Metrization & Lipschitz Stability:** Equipping persistence diagrams with the **bottleneck metric** $$d_B$$ turns diagram space into a Hausdorff metric space. Modern vectorization theory goes one step beyond Urysohn's continuous separating functions by demanding **Lipschitz** maps so tiny data noise cannot explode downstream ML features.

---

## 📖 Overview

Hausdorff means distinct points have disjoint neighbourhoods — limits, when they exist, are unique. Machine learning often *assumes* this when it draws a UMAP: distinct points should sit in two places. Work from 2022–2026 shows the assumption is both necessary (barcode stability) and fragile (UMAP is not a topological embedding).

![Hausdorff distance](https://upload.wikimedia.org/wikipedia/commons/2/21/Hausdorff_distance_sample.svg)
*Hausdorff distance between two sets: the $T_2$ idea, metrized. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_distance_sample.svg)*

---

## 🎯 Intuition

Urysohn’s lemma says that in a sufficiently nice (normal) space, disjoint closed sets are separated by a continuous $[0,1]$-valued function. Mapper and UMAP try to *draw* that function for data. When the space is not Hausdorff — e.g. Kayacan’s finite Alexandroff spaces (Lecture 00.90) — point-separation fails and embedding algorithms start inventing distances.

### Worked Example (Step by Step): A Non-Hausdorff $$T_0$$ Space and an Exact Bottleneck Distance $$d_B$$

Verify both sides of Chapter 03—failure of $$T_2$$ on finite spaces, and success of $$T_2$$ on persistence diagrams—by hand:

**Part A — Sierpiński space ($$T_0$$, yet fails $$T_1$$ and $$T_2$$).** Let $$X = \{0, 1\}$$ with open sets $$\mathcal{T} = \{\emptyset,\ \{1\},\ \{0, 1\}\}$$.
- **Check $$T_0$$:** for $$0 \neq 1$$, the open set $$\{1\}$$ contains $$1$$ and excludes $$0$$ → **$$T_0$$ holds!**
- **Check Hausdorff ($$T_2$$):** the *only* open set containing $$0$$ is $$\{0, 1\}$$, which necessarily overlaps $$\{1\}$$. No disjoint open neighborhoods exist → **not $$T_2$$!**
- **Consequence for limits:** the constant sequence $$1, 1, 1, \dots$$ eventually lies inside every open set containing $$0$$ (namely $$\{0, 1\}$$), so it converges to **both** $$1$$ and $$0$$ simultaneously!

**Part B — Exact bottleneck distance $$d_B$$ between two persistence diagrams.** Suppose Diagram $$D_1$$ has one real loop $$p = (1.0, 5.0)$$ (lifetime $$4.0$$), while noisy Diagram $$D_2$$ has a slightly perturbed loop $$q = (1.2, 4.7)$$ plus a small spurious noise loop $$r = (2.0, 2.4)$$. In the bottleneck metric, points are matched bijectively (allowing unmatched points to pair with the diagonal $$\Delta = \{(x, x)\}$$) to minimize the largest $$L_\infty$$ shift:
- Pair $$p = (1.0, 5.0)$$ with $$q = (1.2, 4.7)$$: cost $$= \max(\vert 1.0 - 1.2\vert,\ \vert 5.0 - 4.7\vert) = \max(0.2,\ 0.3) = \mathbf{0.3}$$.
- Pair the noise point $$r = (2.0, 2.4)$$ with its closest diagonal point $$(2.2, 2.2)$$: cost $$= \tfrac{1}{2}(2.4 - 2.0) = \mathbf{0.2}$$.
- Therefore:

$$
d_B(D_1, D_2) = \max(0.3,\ 0.2) = \mathbf{0.3}.
$$

Because $$d_B$$ is a metric, distinct diagrams sit inside disjoint open $$d_B$$-balls ($$T_2$$!), and tiny noise loops near the diagonal only nudge $$d_B$$ by half their lifetime.

### Explanation: Why Separation Axioms Decide When Embeddings and Barcodes Are Trustworthy

1. **Finite TDA pipelines naturally live in non-Hausdorff $$T_0$$ spaces:** every finite simplicial complex's face poset is a $$T_0$$ Alexandroff space (like a larger Sierpiński space); non-Hausdorff topology is not a pathology—it is the native combinatorial engine!
2. **Passing to homology lands in a Hausdorff metric space:** once persistent homology extracts a diagram and equips it with $$d_B$$, distinct shapes become cleanly separated by disjoint open balls, making limits and stability theorems well-defined.
3. **Never equate "drawn in $$\mathbb{R}^2$$" with "topological embedding":** as Yang (2026) proves, UMAP behaves like spectral clustering on a fuzzy neighbor graph—visually splitting or merging regions that were not separated in the original space.
4. **Upgrade continuity to Lipschitz stability for ML:** Urysohn's lemma promises *continuous* separating functions, yet machine learning requires *Lipschitz* vectorizations so small noise $$\delta$$ in data produces at most $$C\delta$$ change in features.

**Quick check.** In Part B, if a second noise point $$s = (3.0, 3.8)$$ appeared in $$D_2$$, what would $$d_B(D_1, D_2)$$ become? Its distance to the diagonal is $$\tfrac{1}{2}(3.8 - 3.0) = 0.4$$, so $$d_B$$ rises to $$\max(0.3, 0.2, 0.4) = \mathbf{0.4}$$—strictly controlled by the single worst perturbation.

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

## Video tham khảo

- **xem trước** [UMAP Dimension Reduction, Main Ideas!!!](https://www.youtube.com/watch?v=eN0wFzBA4Sc) — StatQuest with Josh Starmer, English. UMAP is sold as an embedding. This note separates that word from a topological embedding.
- [Henry Adams (5/3/22): Topology in Machine Learning](https://www.youtube.com/watch?v=kwYiQNa_pTc) — Applied Algebraic Topology Network, English. Topology in machine learning, where the stability and Lipschitz conditions of this note are used.

## 🧩 Exercises

1. Exhibit a 3-point $T_0$ space that is not $T_1$. Could it appear as an intermediate filtration stage?
2. Why does the bottleneck metric make diagram space Hausdorff, while raw union-find does not?
3. Read Yang (2026)’s abstract and write one sentence: what does UMAP preserve, and what does it not?
