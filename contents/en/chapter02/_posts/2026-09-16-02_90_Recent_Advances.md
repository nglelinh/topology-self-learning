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

**Optional notes.** Connectedness, path-connectedness, and compactness stay as in Chapter 02. We only follow them into data and into neural parameter space.

The theory track is in Vietnamese. This English page holds recent-advance notes only.

---

## 📖 Overview

The two “most important” point-set properties — **cannot be split** and **every open cover has a finite subcover** — are the language of two modern questions: (1) how many pieces does the data have? (2) can a family of models walk from one minimum to another without climbing a loss wall?

![Mug and torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)
*Path-connectedness in shape space: a continuous path of homeomorphisms. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif)*

---

## 🎯 Intuition

A connected space cannot be written $X=U\cup V$ with $U,V$ open, nonempty, and disjoint. In clustering that is the definition of “one cluster” at a fixed scale. $H_0$ persistence refines it: two points lie in the same component at radius $\varepsilon$ when a chain of intermediate points has steps of length $\le\varepsilon$. Compactness appears when we ask whether barcodes are stable: the space of persistence diagrams (bottleneck metric) is complete, and finite diagrams behave in a Heine–Borel “finite-like” way.

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

## 🧩 Exercises

1. Sketch $S_c$ for $L(x,y)=(x^2-1)^2+y^2$. For which $c$ is $S_c$ connected?
2. Distinguish connected from path-connected with a sampled topologist’s sine curve.
3. Why is a barcode with infinitely many long bars not “compact” in the Heine–Borel sense?
