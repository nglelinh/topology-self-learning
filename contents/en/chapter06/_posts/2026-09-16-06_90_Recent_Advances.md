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

Think of a deep neural network as a sculptor working on tangled clay: the input dataset may consist of two intertwined rings or scattered islands that no straight hyperplane could ever separate, yet layer by layer the network folds, stretches, and collapses space until the two classes sit neatly on opposite sides of a flat wall. At the exact same time, inside the network's *own* weight space, symmetries create multiple distinct weight vectors that compute the exact same function—just like sheets of a covering space sitting above a single base point! Both phenomena live squarely inside Chapter 06: **homotopy**, **$$\pi_0$$ and $$\pi_1$$**, and **covering spaces**.

**Optional notes.** Homotopy, $\pi_1$, and covering spaces stay as in Chapter 06. We change only the space: $X$ is now a loss landscape, an activation set, or data flowing through a layer. The theory track is in Vietnamese; this English page holds recent-advance notes only.

---

## Key ideas: Homotopy, Covering Spaces, and Deep Neural Networks

Three core ideas from algebraic topology's Chapter 06 explain surprising empirical discoveries in 2022–2026 deep learning:

1. **Homotopy & Path-Components ($$\pi_0$$ vs. $$\pi_1$$):** Two maps are *homotopic* if one continuously deforms into the other. In parameter space, checking whether two trained checkpoints $$w_0, w_1$$ lie in the same low-loss basin is a **$$\pi_0(S_c)$$** question (how many path-components does $$S_c = \{w : L(w) \le c\}$$ have?), while checking whether two low-loss paths enclose an obstacle is a **$$\pi_1(S_c)$$** question!
2. **Covering Spaces & Weight-Space Symmetries:** Just as the covering map $$p: \mathbb{R} \to S^1$$ wraps infinitely many points $$t + 2\pi k$$ onto one point of the circle, permuting the $$m$$ hidden neurons of a layer gives $$m!$$ distinct weight vectors that map to the **exact same neural function**—creating a multi-sheeted covering structure over function space!
3. **Layer-Wise Homotopy Simplification:** Every ReLU layer $$f_\ell(x) = \mathrm{ReLU}(W_\ell x + b_\ell)$$ is a continuous, non-injective folding map. Because it is not a homeomorphism, it can *kill* topological complexity—collapsing disconnected components and loops of a class until the final layer sees contractible, linearly separable blobs.

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

### Worked Example (Step by Step): Permutation Covering Sheets and a ReLU Layer Untangling Disconnected Data

Verify both sides of neural network topology—in **weight space** and in **data space**—on two tiny formulas:

**Part A — A 2-sheeted permutation symmetry in weight space.** Consider a 2-neuron network:

$$
f_w(x) = a_1\,\mathrm{ReLU}(b_1 x) + a_2\,\mathrm{ReLU}(b_2 x), \qquad w = (a_1, b_1, a_2, b_2).
$$

Take the weight vector $$w = (1, 1,\ -2, -1)$$ and swap the two neurons to get $$w' = (-2, -1,\ 1, 1)$$. For *every* input $$x \in \mathbb{R}$$, $$f_{w}(x) = f_{w'}(x)$$ identically! Yet their linear midpoint is:

$$
\bar{w} = \frac{1}{2}(w + w') = (-0.5,\ 0,\ -0.5,\ 0) \implies f_{\bar{w}}(x) \equiv \mathbf{0} \text{ (completely broken!)}.
$$

That is the exact geometry behind **Git Re-Basin** and linear mode connectivity: $$w$$ and $$w'$$ sit on two different sheets of a permutation covering over the *same* optimal function, so naive averaging lands off the sheet—until you permute $$w'$$ back onto $$w$$'s sheet!

**Part B — One ReLU layer collapsing $$\beta_0 = 2$$ into $$\beta_0 = 1$$ in data space.** Suppose Class `+1` on $$\mathbb{R}$$ is disconnected: $$X_+ = [-3, -1] \cup [1, 3]$$ ($$\beta_0 = 2$$), trapping Class `-1` in the middle $$X_- = (-1, 1)$$. No homeomorphism of $$\mathbb{R}$$ can ever separate $$X_+$$ from $$X_-$$ with a single threshold! Now apply a 2-neuron ReLU layer $$\phi(x) = \mathrm{ReLU}(x) + \mathrm{ReLU}(-x) = \vert x\vert$$:
- $$\phi([-3, -1]) = [1, 3]$$ and $$\phi([1, 3]) = [1, 3]$$ → the two disconnected pieces fold right on top of each other into **1 connected interval** $$[1, 3]$$ ($$\beta_0$$ drops from 2 to **1**!).
- Meanwhile $$\phi(X_-) = [0, 1)$$, so a single linear cut at $$y = 1$$ now separates the classes with 100% accuracy!

### Explanation: How Layers Simplify Data Topology While Symmetries Multiply Minima

1. **Why invertible layers alone are not enough:** a homeomorphism preserves $$\beta_0$$ and $$\beta_1$$, so an invertible map can never untangle two linked rings or merge two separated islands of the same class; ReLU's *non-invertible* folding is what drops Betti numbers!
2. **Read mode connectivity as $$\pi_0(S_c)$$:** asking whether two checkpoints can be connected by a low-loss curve is asking whether they represent the same element in $$\pi_0(\{w : L(w) \le c\})$$.
3. **Explain naive merging failure via covering sheets:** as Part A proved, two weight vectors implementing the *exact same function* can have a terrible midpoint if they sit on different permutation sheets—aligning the sheets restores linear mode connectivity.
4. **Watch the frontier move from $$\pi_0$$ to $$\pi_1$$ and induced maps $$(f_\ell)_*$$:** measuring how each layer kills loops (the kernel of $$(f_\ell)_*: \pi_1(X_{\ell-1}) \to \pi_1(X_\ell)$$) is turning algebraic topology into a diagnostic stethoscope for deep architectures.

**Quick check.** In Part A, if a hidden layer has $$m = 5$$ distinct neurons instead of 2, how many permutation-equivalent weight vectors cover the exact same function? Exactly $$5! = \mathbf{120}$$ distinct sheets!

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

## Video tham khảo

- **xem trước** [[NeurIPS 2018] Loss Surfaces, Mode Connectivity, and Fast Ensembling of DNNs](https://www.youtube.com/watch?v=UwKdNzb_Q6U) — Timur Garipov, English. Paths in a loss landscape joining modes, the homotopy picture of this note.
- [Introduction to Topological Deep Learning](https://www.youtube.com/watch?v=N67GABKImZA) — Mathilde Papillon, English. Networks as spaces you can deform, the frame of topological deep learning.

## 🧩 Exercises

1. For $L(x)=(x^2-1)^2$, compute $\pi_0(S_c)$ as a function of $c$.
2. Why is linear mode connectivity stronger than ordinary path-connectedness?
3. Sketch a 2-sheeted cover of $S^1$ and say one sentence about “two minimizers covering one minimizer on the quotient”.
