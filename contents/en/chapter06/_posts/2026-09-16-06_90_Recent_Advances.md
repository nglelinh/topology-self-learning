---
layout: post
title: "Lecture 06.90: Recent Advances (2022–2026) — Homotopy of Neural Networks and Mode Connectivity"
lang: en
lang-ref: lecture-06-90
chapter: 6
lecture: 90
order: 90
lesson_type: optional
categories: [chapter06]
tags: [optional, recent-advances, homotopy, mode-connectivity, neural-networks]
description: "Optional notes: π₁ and homotopy meet neural-network topology and mode connectivity. Not a theory translation."
---

**Optional notes.** Homotopy, $\pi_1$, and covering spaces stay as in Chapter 06. We only change the space: $X$ is now a loss landscape, an activation set, or the data after a layer.

The theory track is in Vietnamese. This English page holds recent-advance notes only.

---

## 📖 Overview

A homotopy is a continuous deformation of maps. In deep learning two weights $w_0,w_1$ lie in the “same mode” when a path $\gamma$ keeps $L(\gamma(t))$ under a barrier — a path-homotopy in a sublevel set. The Ballester–Casacuberta–Escalera survey (2023) and 2025–2026 mode-connectivity papers turn Chapter 06 into a reading tool for empirical work.

![Neural network](https://upload.wikimedia.org/wikipedia/commons/4/46/Colored_neural_network.svg)
*A feedforward net is a composite map $f:X\to Y$ — an object of homotopy. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Colored_neural_network.svg)*

![Covering of the circle](https://upload.wikimedia.org/wikipedia/commons/5/54/Covering_map.png)
*The covering $\mathbb{R}\to S^1$: many preimages, one loop. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Covering_map.png)*

---

## 🎯 Intuition

$\pi_1(S^1)=\mathbb{Z}$ counts windings. Naitzat, Zhitnikov, and Lim (2020) — still heavily cited after 2022 — showed that a deep net *simplifies the topology of data*: Betti numbers of layer-wise sets drop, as if each layer were a homotopy toward a contractible space. Mode connectivity is the dual question: is *parameter* space contractible on low sublevel sets?

---

## 📐 Four concrete advances

### 1. TDA for neural-network analysis (survey)

Ballester, Casacuberta, and Escalera (2023/24) collect uses of $\pi_1$, Mapper, and persistent homology on (i) data, (ii) activations, and (iii) weight space. This is the Chapter 06 → ML map.

- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *Topological Data Analysis for Neural Network Analysis: A Comprehensive Survey*, arXiv:2312.05840 (2023).
- Gregory Naitzat, Andrey Zhitnikov, Lek-Heng Lim, *Topology of deep neural networks*, *JMLR* (2020), arXiv:2004.06093 — still shaping 2022–2026 papers.

### 2. Mode connectivity beyond classifiers

Yao, Zhang, and Tian (2026) find mode-connectivity evidence in generative and contrastive models — homotopy in $S_c=\{L\le c\}$ is no longer a softmax story. Cheng–Amiri (2026) use the same path language for unlearning: does deleting a datum cut the path between two minimizers?

- Chengzheyi Yao, Yongzhao Zhang, Yongding Tian, *Mode Connectivity Beyond Classifiers*, arXiv:2608.30366 (2026).
- Jiali Cheng, Hadi Amiri, *Understanding Machine Unlearning Through the Lens of Mode Connectivity*, arXiv:2607.23970 (2026).

### 3. Linear mode connectivity and model merging

If the segment between two minimizers lies in $S_c$, the network admits a *linear* homotopy. Li–Shen (2026) take this to billion-parameter transformers; Tran et al. (2025–26) analyse MoE and attention. Formally this is a $\pi_0(S_c)$ question: how many path-components does the sublevel set have?

$$
[\gamma]\in\pi_0\bigl(\{w:L(w)\le c\}\bigr).
$$
(The path-components; $\pi_1(S_c)$ is still almost unmeasured at scale.)

- Tianyi Li, Zhiqiang Shen, *Scaling Linear Mode Connectivity and Merging to Billion Parameter Pretrained Transformers*, arXiv:2606.23607 (2026).
- Viet-Hoang Tran, Van Hoan Trinh, Khanh Vinh Bui, Tan M. Nguyen, *On Linear Mode Connectivity of Mixture-of-Experts Architectures*, arXiv:2509.11348 (2025).

### 4. Homotopy as a layer-wise invariant of data

Su et al. (2025) stress TDA *beyond* persistent homology: homotopy and cell complexes become features. In Chapter 06 language each layer $f_\ell$ induces $(f_\ell)_*$ on $\pi_1$ — and people have begun to measure that kernel/cokernel on real data.

- Zhe Su et al., *Topological Data Analysis and Topological Deep Learning Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

---

## 🧠 Papers and references

- Hatcher, *Algebraic Topology*, Ch. 1.
- Munkres, *Topology*, Ch. 9, 13.
- The arXiv items above.

## 🔗 Applications

Model soups / weight averaging work only when the segment between checkpoints is a low-loss homotopy. Chapter 06 supplies the name.

## 🧩 Exercises

1. For $L(x)=(x^2-1)^2$, compute $\pi_0(S_c)$ as a function of $c$.
2. Why is linear mode connectivity stronger than ordinary path-connectedness?
3. Sketch a 2-sheeted cover of $S^1$ and say one sentence about “two minimizers covering one minimizer on the quotient”.
