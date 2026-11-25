---
layout: post
title: "Lecture 02.90: Recent Advances (2022–2026) — Connectedness, Compactness, and Components of Data"
lang: en
lang-ref: lecture-02-90
chapter: 2
lecture: 90
order: 90
lesson_type: optional
categories: [chapter02]
tags: [optional, recent-advances, connectedness, compactness, mode-connectivity]
description: "Optional notes: connectedness/compactness meet clustering, 0-dimensional persistence, and mode connectivity. Not a theory translation."
---

Train the exact same neural network twice from two different random seeds, and you land at two completely different weight vectors $$w_0$$ and $$w_1$$ in billion-dimensional space—yet both achieve 95% accuracy. For years, researchers pictured those minima as isolated mountain valleys separated by steep walls of high loss. Then came a topological surprise: in many deep networks, you can walk along a continuous, low-loss valley all the way from $$w_0$$ to $$w_1$$ without ever climbing a hill—and sometimes even along a straight line segment! That phenomenon, **mode connectivity**, is nothing other than **path-connectedness** of sublevel sets in action.

**Optional notes.** Connectedness, path-connectedness, and compactness stay as in Chapter 02. We follow them into data and neural parameter space across 2022–2026 research. The theory track is in Vietnamese; this English page holds recent-advance notes only.

---

## Key ideas: Connectedness, Compactness, and Modern Loss Landscapes

Two cornerstone properties from Chapter 02—**connectedness** and **compactness**—govern how modern AI practitioners cluster data, merge models, and stabilize topological features:

1. **Connectedness & Path-Connectedness:** A space is *connected* if it cannot be split into two disjoint nonempty open sets, and *path-connected* if any two points can be joined by a continuous curve $$\gamma: [0,1] \to X$$. In TDA, $$H_0$$ persistence tracks path-components of data across scales; in deep learning, **mode connectivity** asks whether the low-loss sublevel set $$S_c = \{w \in \mathbb{R}^N : L(w) \le c\}$$ is path-connected.
2. **Linear Mode Connectivity & Model Merging:** Stronger than arbitrary path-connectedness is *convexity along the chord*: does the straight segment $$\gamma(t) = (1-t)w_0 + tw_1$$ stay inside $$S_c$$? When it does, averaging the weights of two separately fine-tuned LLMs (model merging) preserves accuracy without paying for an ensemble!
3. **Compactness as Stability Control:** In $$\mathbb{R}^d$$, Heine–Borel characterizes compactness as closed and bounded—forcing every continuous function to attain its bounds and every open cover to reduce to a finite subcover. In TDA, compactness guarantees finite-like control over persistence diagrams so that stable vectorizations (Lipschitz maps into Banach/Euclidean spaces) never blow up under tiny perturbations.

---

## 📖 Overview

The two “most important” point-set properties — **cannot be split** and **every open cover has a finite subcover** — are the language of two modern questions: (1) how many pieces does the data have? (2) can a family of models walk from one minimum to another without climbing a loss wall?

![Mug and torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)
*Path-connectedness in shape space: a continuous path of homeomorphisms. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif)*

---

## 🎯 Intuition

A connected space cannot be written $X=U\cup V$ with $U,V$ open, nonempty, and disjoint. In clustering that is the definition of “one cluster” at a fixed scale. $H_0$ persistence refines it: two points lie in the same component at radius $\varepsilon$ when a chain of intermediate points has steps of length $\le\varepsilon$. Compactness appears when we ask whether barcodes are stable: the space of persistence diagrams (bottleneck metric) is complete, and finite diagrams behave in a Heine–Borel “finite-like” way.

### Worked Example (Step by Step): Testing Linear vs. Curved Mode Connectivity on Two Explicit Loss Surfaces

Let's test path-connectedness by hand on two concrete loss landscapes with minima at $$w^{(0)} = (-1, 0)$$ and $$w^{(1)} = (1, 0)$$:

**Landscape 1 (2D double-well):** $$L(w_1, w_2) = (w_1^2 - 1)^2 + w_2^2$$.
- At both minima $$w^{(0)} = (-1, 0)$$ and $$w^{(1)} = (1, 0)$$, the loss is $$L = 0$$.
- Check the straight-line chord $$\gamma_{\text{lin}}(t) = (-1 + 2t,\ 0)$$ for $$t \in [0, 1]$$: at the midpoint $$t = \tfrac{1}{2}$$, $$\gamma_{\text{lin}}(\tfrac{1}{2}) = (0, 0)$$ hits a loss barrier of $$L(0, 0) = (0 - 1)^2 + 0 = \mathbf{1}$$.
- What about *any* continuous curve joining $$w^{(0)}$$ to $$w^{(1)}$$? By the Intermediate Value Theorem, any path must cross the vertical line $$w_1 = 0$$, where $$L(0, w_2) = 1 + w_2^2 \ge \mathbf{1}$$! Therefore, the sublevel set $$S_c = \{w : L(w) \le c\}$$ is **disconnected** for every $$c < 1$$ (two disjoint ovals) and becomes **path-connected** at the exact critical threshold $$c = 1$$.

**Landscape 2 (3D circular valley — curved connectivity without linear connectivity):** lift into $$\mathbb{R}^3$$ with $$L_3(w_1, w_2, w_3) = (w_1^2 + w_2^2 - 1)^2 + w_3^2$$.
- Both $$w^{(0)} = (-1, 0, 0)$$ and $$w^{(1)} = (1, 0, 0)$$ still have loss $$0$$, and the **straight line** between them still hits a wall $$L_3(0, 0, 0) = \mathbf{1}$$ — so **linear mode connectivity fails** at $$c = 0.1$$!
- Yet along the semicircular arc $$\gamma_{\text{arc}}(t) = (\cos(\pi t),\ \sin(\pi t),\ 0)$$, we have $$\cos^2(\pi t) + \sin^2(\pi t) = 1$$ for every $$t \in [0, 1]$$, so $$L_3(\gamma_{\text{arc}}(t)) \equiv \mathbf{0}$$! Thus $$S_0$$ is **path-connected** even though it is not convex!

### Explanation: From Connectedness Axioms to Model Merging in Billion-Parameter AI

1. **See sublevel sets $$S_c$$ as topological spaces evolving with $$c$$:** just as $$H_0$$ persistence tracks data clusters merging as radius $$\varepsilon$$ grows, loss-landscape topology tracks isolated minima merging into a single connected valley as the loss ceiling $$c$$ rises.
2. **Distinguish path-connectedness from convexity (linear mode connectivity):** in high-dimensional neural networks, symmetry (such as permuting hidden neurons) creates vast curved zero-loss valleys like Landscape 2—so two trained models are often connected by a curved low-loss tunnel even when naive weight averaging fails.
3. **Align symmetries to unlock linear mode connectivity:** once you permute neurons of $$w_1$$ to match the functional alignment of $$w_0$$ (Tran et al., 2026), the two points move onto the *same* local basin where the straight segment $$(1-t)w_0 + tw_1$$ stays low-loss—turning topology into practical LLM model merging!
4. **Rely on compactness for stable topological summaries:** when turning persistence barcodes into vectors for downstream models, compactness prevents infinitely many unmanageable bars from destroying Lipschitz stability.

**Quick check.** In Landscape 2 ($$L_3(w_1, w_2, w_3) = (w_1^2 + w_2^2 - 1)^2 + w_3^2$$), what is the topological shape of the zero-loss set $$S_0$$? It is the unit circle $$S^1$$ sitting in the plane $$w_3 = 0$$—both **compact** (closed and bounded) and **path-connected**, yet **not convex**!

---

## 📐 Four concrete advances

### 1. Persistent $H_0$ as a theory of components

Bot–McInnes–Aerts (2025) and the 2025–2026 ToMATo line (see Lecture 01.90) turn connected components into **multiscale objects**. Formally, if
$$
X_{\varepsilon}=\bigsqcup_{\alpha} C_{\alpha}(\varepsilon)
$$
is the path-component partition of the $\varepsilon$-complex, then a death in the $H_0$ barcode is the moment two $C_{\alpha}$ merge. This is not a new Munkres theorem — it is connectedness, filtered.

- Daniël Bot, Leland McInnes, Jan Aerts, *Persistent Multiscale Density-based Clustering*, arXiv:2512.16558 (2025).

### 2. Mode connectivity: path-connectedness of loss landscapes

A network with weights $w\in\mathbb{R}^N$ and loss $L$ has sublevel sets
$$
S_c=\{w:L(w)\le c\}.
$$
**Mode connectivity** asks whether $S_c$ is path-connected for large enough $c$. Work in 2025–2026 pushes this past classical classifiers: Yao, Zhang, and Tian (2026) find mode paths in generative and contrastive models; Cheng and Amiri (2026) read machine unlearning through the same path-connectedness lens.

- Chengzheyi Yao, Yongzhao Zhang, Yongding Tian, *Mode Connectivity Beyond Classifiers: Evidence from Generative and Contrastive Models*, arXiv:2608.30366 (2026).
- Jiali Cheng, Hadi Amiri, *Understanding Machine Unlearning Through the Lens of Mode Connectivity*, arXiv:2607.23970 (2026).

### 3. Linear mode connectivity at scale

“Linear” mode connectivity means the segment $(1-t)w_0+tw_1$ stays inside $S_c$. That is path-connectedness with a very poor path — hence a stronger property. Li and Shen (2026) take it to billion-parameter transformers; Tran et al. (2026) analyse functional equivalence of attention as a reason modes connect.

$$
\gamma(t)=(1-t)w_0+tw_1,\qquad t\in[0,1],\qquad L(\gamma(t))\le c.
$$

- Tianyi Li, Zhiqiang Shen, *Scaling Linear Mode Connectivity and Merging to Billion Parameter Pretrained Transformers*, arXiv:2606.23607 (2026).
- Viet-Hoang Tran et al., *Functional Equivalence in Attention: A Comprehensive Study with Applications to Linear Mode Connectivity*, arXiv:2606.17830 (2026).

### 4. Compactness as cover control in TDA

Classical persistence stability says the map from a compact metric space to diagram space is bottleneck-Lipschitz. Vectorization papers from 2023–2024 (Loiseaux et al.; Bravetti–Mijangos–Padilla) extend the point: to feed barcodes into a network one needs a Lipschitz embedding — that is, one must not break the “finite-like” character of compact sets.

- David Loiseaux, Luis Scoccola, Mathieu Carrière, Magnus Bakke Botnan, *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Alessandro Bravetti, Martín Mijangos, Pablo Padilla, *New divergence measures between persistence diagrams and stability of vectorizations*, arXiv:2410.03910 (2024).

---

## 🧠 Papers and references

- Munkres, *Topology*, Ch. 3.
- Morris, *Topology without Tears*, Ch. 12–13.
- The arXiv items above.

## 🔗 Applications

When two checkpoints of a large language model can be joined by a low-loss segment, practitioners *merge* weights instead of ensembling. That is path-connectedness in production.

## Video tham khảo

- **xem trước** [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, English. Persistent H_0 as a theory of the connected components of a sample.
- [[NeurIPS 2018] Loss Surfaces, Mode Connectivity, and Fast Ensembling of DNNs](https://www.youtube.com/watch?v=UwKdNzb_Q6U) — Timur Garipov, English. Mode connectivity: path-connectedness of a loss landscape between minima, the second item here.

## 🧩 Exercises

1. Sketch $S_c$ for $L(x,y)=(x^2-1)^2+y^2$. For which $c$ is $S_c$ connected?
2. Distinguish connected from path-connected with a sampled topologist’s sine curve.
3. Why is a barcode with infinitely many long bars not “compact” in the Heine–Borel sense?
